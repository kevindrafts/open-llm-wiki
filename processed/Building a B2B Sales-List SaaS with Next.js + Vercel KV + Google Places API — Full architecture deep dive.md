---
title: "Building a B2B Sales-List SaaS with Next.js + Vercel KV + Google Places API — Full architecture deep dive"
source: "https://dev.to/j209509/building-a-b2b-sales-list-saas-with-nextjs-vercel-kv-google-places-api-full-architecture-2gha"
author:
  - "[[j209509]]"
published: 2026-05-15
created: 2026-05-19
description: "Intro   I built a B2B sales-list-generation SaaS as a solo/small-team developer and have... Tagged with nextjs, typescript, saas, webdev."
tags:
  - "clippings"
---
## Intro

I built a B2B sales-list-generation SaaS as a solo/small-team developer and have been running it in production. The product is [bacotto](https://bacotto.com/en) — type in an industry and a region, and it returns 100 enriched leads in 3 minutes (address, phone, email, Instagram handle, LINE official account, Google reviews, plus a "still operating" classification).

This post walks through the architecture from the angle of "engineering decisions a tiny team needs to make to keep the lights on cheaply." Should be useful if you're building a Maps-API + Web-scraping style SaaS, or any low-budget local B2B tool.

## Stack overview

- **Front / API**: Next.js 15 (App Router) + TypeScript
- **Deploy**: Vercel (Hobby plan)
- **Auth**: NextAuth.js v5 (Google OAuth + email/password)
- **DB / Cache**: Vercel KV (Upstash Redis under the hood)
- **Payments**: Stripe Checkout + Customer Portal
- **Error monitoring**: Sentry
- **Email**: Resend
- **Data sources**: Google Places API + a regulation-compliant HTML crawler

The thesis: lean on fully-managed services everywhere possible to keep operational cost minimal.

## Three core design decisions

### 1\. Search → Enrich two-stage pipeline

When a user submits "industry × region", the internal flow is:

```
[Google Places Text Search] → 60 candidates
   ↓ dedupe by placeId
[Website Enrich (concurrency 16)] → fetch each business's official site
   ↓ HTML parsing
[Extract] email / Instagram / LINE / "closed?" classifier
   ↓
[Output] CSV / Google Sheets
```

The trick is running stage two with **concurrency 16** via `Promise.allSettled` plus a hand-rolled `parallelMap(items, fn, concurrency)` so per-site latency variance doesn't dominate end-to-end time.

```
export async function parallelMap<T, R>(
  items: T[],
  fn: (item: T) => Promise<R>,
  concurrency: number
): Promise<R[]> {
  const results: R[] = new Array(items.length);
  let idx = 0;
  async function worker() {
    while (idx < items.length) {
      const i = idx++;
      results[i] = await fn(items[i]);
    }
  }
  await Promise.all(Array.from({ length: concurrency }, worker));
  return results;
}
```

100-row list generation that takes a human 8 hours of clicking finishes in 3 minutes in the SaaS.

### 2\. Cache layer abstracted so the codebase runs without KV

```
interface CacheStore {
  get<T>(key: string): Promise<{ value: T; storedAt: number } | null>;
  set<T>(key: string, value: T, ttlSec: number): Promise<void>;
  del(key: string): Promise<void>;
}

class MemoryCache implements CacheStore { /* per-instance Map */ }
class KVCache implements CacheStore { /* @vercel/kv backed */ }

function pickCache(): CacheStore {
  if (process.env.KV_REST_API_URL && process.env.KV_REST_API_TOKEN) {
    return new KVCache();
  }
  return new MemoryCache();
}

export const cache = pickCache();
```

Wins:

- **Local dev runs with no KV env vars set** — falls back to Memory automatically
- **Production picks up KV the moment env vars exist** — zero code changes to migrate
- **Tests inject MemoryCache directly** — no Redis mocking required

When I added KV later, the existing cache keys started persisting in Redis with literally zero code diff.

### 3\. Negative caching + per-use-case TTLs

Google Places costs roughly $0.02 per call so cache hit rate maps directly to money. There's also a long tail of "I crawled the official site but couldn't find an email" responses, which I want to negative-cache.

```
const SEARCH_TTL_SEC = 60 * 60 * 24 * 14;          // Places API results: 14d
const ENRICH_TTL_SEC = 60 * 60 * 24 * 30;          // Found-something: 30d
const ENRICH_NEGATIVE_TTL_SEC = 60 * 60 * 24 * 14; // Found-nothing: 14d

const foundAnything = !!result.email || !!result.instagram || !!result.line;
await cache.set(
  key,
  result,
  foundAnything ? ENRICH_TTL_SEC : ENRICH_NEGATIVE_TTL_SEC
);
```

Negative cache entries use **the same key and same value shape** as positive ones. The fast path is "cache hit → return immediately" with zero branching. The shorter TTL means failed lookups retry automatically 14 days later, which catches sites that have since added contact info.

This pattern alone cut my Places API spend to a quarter of the original projection.

## Programmatic SEO: 4,400 indexable pages

Local-B2B tooling has demand fragmented across prefecture × city × industry combinations. The naive cross-product is 47 prefectures × 30 industries = 1,410 base pages, but expanding to detail-level cells creates thousands of pages where "low-population area × niche industry" combinations become thin content — which Google penalizes as scaled content abuse.

So I added a **tier × popularity gate**:

```
// city.tier:        1 (low population) - 5 (major metro center)
// industry.popularity: 1 (niche) - 3 (major)
export function shouldIndexDetail(cityTier: number, industry: Industry): boolean {
  if (industry.popularity === 3) return cityTier >= 3;
  if (industry.popularity === 2) return cityTier >= 4;
  return cityTier >= 5;
}
```

This narrows indexable combinations from 7,321 → 4,364 and marks the rest noindex. `robots.ts` and `sitemap.ts` both consume this same filter, so only the strong pages get pushed to Google.

## Daily IndexNow ping cron

A new domain takes Google several weeks to fully crawl 4,400 pages. To speed it up I ping IndexNow daily with the full URL list via Vercel Cron:

```
// vercel.json
{
  "crons": [
    { "path": "/api/cron/onboarding", "schedule": "0 9 * * *" },
    { "path": "/api/cron/indexnow",   "schedule": "15 0 * * *" }
  ]
}
```

Bing / Yandex / Naver respect IndexNow with near-instant crawls. So even if Google takes its time, you have a non-Google discovery channel running.

## Stripe webhook fire-and-forget email pattern

Payment events trigger both a thank-you email to the customer and an alert email to the admin. I never want a transient email failure to make Stripe think the webhook failed (it'd retry, potentially double-credit accounts):

```
// webhooks/stripe/route.ts
void notifyAdmins(
  adminCheckoutNotification({ email, kind: "subscription", label, amountJpy })
).catch((err) => console.warn("[stripe] notif failed:", err));

void sendMail({ to: email, subject, text })
  .catch((err) => console.warn("[stripe] receipt failed:", err));

return NextResponse.json({ received: true });
```

Resend can be flaky for a minute and payment processing still completes. Failures land in Sentry for retroactive review.

There's also a deliberate "silence on renewal" choice: I never implemented `invoice.paid` handler, which means subscribers never get a monthly "we charged you again" email. The intent is to make the subscription fade into background — fewer "oh right, I should cancel that" moments. Lowered voluntary churn.

## Trade-offs

| Chose | Skipped | Why |
| --- | --- | --- |
| Vercel KV (Upstash) | PostgreSQL | Stay inside Hobby budget |
| Vercel Cron | GitHub Actions | One-file config |
| Resend | SendGrid | 3 DNS records for domain auth, clean UI |
| Sentry | Roll-my-own logging | Min observability cost |
| Stripe Customer Portal | DIY cancellation flow | Legally safer, no UI to maintain |
| Programmatic SEO | Hand-written blog | Scales orders of magnitude better with quality gates |

## Actual monthly cost

- Vercel: $0 (Hobby)
- Vercel KV: $0 (Free plan = 500K commands/mo)
- Sentry: $0 (Developer plan)
- Resend: $0 (3,000 emails/mo)
- Google Places API: usage-based (currently $10–25/mo)
- Domain: ~$1/mo (annualized)
- **Total: about $10/mo**

Comfortably supports a few hundred MAU on these settings.

## Takeaways

- **Two-stage pipeline** for parallelism wins
- **Cache abstraction** to keep dev/prod codepaths identical
- **Negative cache + per-use-case TTL** can cut API cost dramatically
- **tier × popularity gate** keeps programmatic SEO out of spam territory
- **IndexNow cron** speeds up new-domain discovery
- **Fire-and-forget** isolates external API failures from payment processing
- **Silent renewals** reduce voluntary churn

The actual product is at [bacotto.com](https://bacotto.com/en) (free tier of 20 leads/month, no card required) — though it's Japan-focused, so the UI is in Japanese. The architecture patterns above are language-agnostic.

If you're building something similar, happy to discuss specifics in the comments.[MongoDB](https://dev.to/mongodb)Promoted

[![MongoDB Atlas image](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fi.imgur.com%2FDa7EFPJ.jpeg)](https://www.mongodb.com/cloud/atlas/lp/try3?utm_campaign=display_dev.to-webdev_pl_flighted_atlas_tryatlaslp_prosp_gic-null_ww-all_dev_dv-all_eng_leadgen&utm_source=dev.to&utm_medium=display&utm_content=deployinminutes&bb=263181)

## Scale your AI apps to 125+ cloud regions.

Atlas handles the sharding, backups, and failover while you focus on shipping features. Get a flexible document model and integrated vector search on any cloud provider. Create your free cluster now.