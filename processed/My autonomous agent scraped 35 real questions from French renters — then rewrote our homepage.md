---
title: "My autonomous agent scraped 35 real questions from French renters — then rewrote our homepage"
source: "https://dev.to/bailleurverif/my-autonomous-agent-scraped-35-real-questions-from-french-renters-then-rewrote-our-homepage-2bfd"
author:
  - "[[Florian Demartini]]"
published: 2026-05-27
created: 2026-05-29
description: "Every product landing page I've seen — including mine — had a section that said something like \"you... Tagged with python, ai, automation, saas."
tags:
  - "clippings"
---
Every product landing page I've seen — including mine — had a section that said something like "you might be worried about your lease, your deposit, your DPE rating." Pure copywriter hypothesis. This week, my autonomous agent replaced every word of it with data scraped from Reddit. Here's the exact pipeline.

## Background: 370 autonomous cycles, one French housing rights tool

[BailleurVérif](https://bailleurverif.fr/) is a French housing rights SaaS I run solo. The agent wakes every 2 hours via cron, reads a strategic critic audit every 12 hours, and executes prescriptions autonomously — no human in the loop per wake cycle. As of today: 370 wakes, 27/27 strategic prescriptions honored, 0 ScheduleWakeup calls (external cron handles pacing).

Stack: Python + Anthropic Claude API for the critic/executor pattern + SQLite funnel tracker + static HTML server. The agent commits to GitHub, pings the Indexing API, publishes datasets on data.gouv.fr. This week it made a product decision I'd been procrastinating on for weeks.

## The problem: our homepage copy was entirely hypothetical

Strategic critic audit-26 (2026-05-26T21:55Z) flagged it directly:

> "Homepage copy is 100% hypothetical — 'vous vous demandez peut-être si votre loyer est légal...' — while Reddit has thousands of real renter questions publicly accessible."

The prescription: scrape 30+ questions from French subreddits, build a data-driven page, publish the JSON dataset as CC-BY 4.0, then use that corpus to swap the homepage hero. Builder-only. Zero human action required from me.

## The scraping pipeline

The agent wrote `scrape_reddit_locataires_run367.py`. Two rounds, rate-limited at 2s/request, with an identified bot UA:

```
import urllib.request, urllib.parse, json, time

SUBREDDITS = "france+paris+immobilier+vosfinances+AskFrance"
UA = "BailleurVerifBot/0.1 (+bailleurverif.fr; contact@bailleurverif.fr)"

TAG_QUERIES = {
    "loyer-abusif": [
        "loyer abusif encadrement refus propriétaire",
        "loyer trop élevé que faire locataire",
    ],
    "dpe-invalide": [
        "DPE faux fraude loyer augmenté",
        "dpe invalide recours locataire",
    ],
    "depot-garantie-non-restitue": [
        "caution non rendue délai légal",
        "dépôt garantie non restitué propriétaire",
    ],
}

results = []
for tag, queries in TAG_QUERIES.items():
    for q in queries:
        url = (
            f"https://www.reddit.com/search.json"
            f"?q={urllib.parse.quote(q)}"
            f"&subreddit={SUBREDDITS}"
            f"&sort=top&limit=25&t=month"
        )
        req = urllib.request.Request(url, headers={"User-Agent": UA})
        with urllib.request.urlopen(req, timeout=10) as resp:
            data = json.loads(resp.read())
        for post in data["data"]["children"]:
            p = post["data"]
            results.append({
                "tag": tag,
                "title": p["title"],
                "subreddit": p["subreddit"],
                "score": p["score"],
                "num_comments": p["num_comments"],
                "id_hash": p["id"],  # no username stored
            })
        time.sleep(2)
```

Round 1 produced 50 raw results. Round 2 added `r/Locataires` and tightened the queries. **Final dataset: 35 questions.**

## The quality filter: why 50 → 35 matters

The filter pass mattered more than the scrape volume:

- **Title-anchor required**: must contain a tag-specific word (loyer, DPE, caution, garantie, encadrement)
- **Renter scope only**: not a landlord asking about their property
- **Anti-noise blacklist**: "copropriété", "syndic", "locaux commerciaux" — adjacent topics, out of scope

What got cut: 8 landlord questions, 4 commercial lease questions, 3 homeowner renovation questions.

**Final distribution: loyer-abusif: 26 / dpe-invalide: 6 / depot-garantie: 3.**

Score range: 8 to 347 upvotes. The agent sorted by score within each tag and picked the top 3 for the homepage hero.

## The output: 776 lines of HTML + a CC-BY 4.0 JSON dataset

`build_questions_reelles_page_run367.py` generated `/questions-reelles-locataires-fr.html` with:

- JSON-LD: WebPage + BreadcrumbList + FAQPage (3 legal questions) + Dataset + Organization
- 35 questions by category, anonymized (id\_hash only, subreddit + score shown)
- Direct links to the legal templates matching each question tag
- CC-BY 4.0 downloadable JSON dataset (27 KB)

Dataset schema:

```
{
  "metadata": {
    "title": "Questions réelles de locataires FR — Reddit 2026-05",
    "source": "Reddit public search API",
    "license": "CC-BY 4.0",
    "scrape_date": "2026-05-27",
    "filter_methodology": "tag-anchor title match + renter scope + blacklist anti-noise",
    "total_questions": 35
  },
  "questions": [
    {
      "id_hash": "e95b9fed0029",
      "tag": "loyer-abusif",
      "title": "Mais qui respecte l'encadrement des loyers pour les petites surfaces ?",
      "subreddit": "paris",
      "score": 93,
      "num_comments": 41
    }
  ]
}
```

## The homepage hero swap — 12 hours later

Strategic audit-27 arrived at 10:00Z the next morning with a single prescription: use the corpus to replace the hypothetical homepage intro. The agent picked 3 questions (one per tag, highest score), added citation badges, and modified 22 lines of `index.html`.

**Before:**

```
<p>Vous vous demandez peut-être si votre loyer respecte l'encadrement légal,
si votre DPE est valide, si votre propriétaire peut garder votre caution...</p>
```

**After:** 3 real questions with `r/paris · 93 votes` badges. A CTA linking to all 35 questions. Commit `47404ed`, smoke-tested via `curl -s https://bailleurverif.fr/ | grep "loyer abusif"` ✅.

The whole cycle — audit-26 prescribed, agent built and shipped, audit-27 prescribed homepage swap, agent shipped — completed in under 16 hours, with zero messages from me.

## The side discovery: 60% of "direct" visits were bots

While auditing the funnel this week, the agent cross-referenced session IDs against raw UA strings in `visits.jsonl`. The result: **159 raw "direct" sessions → 63 plausibly human after UA filtering.**

The filter:

```
import re

BOT_UA_PATTERNS = [
    "Googlebot", "Applebot", "Yandex", "HeadlessChrome", "GoogleOther",
    "PerplexityBot", "GPTBot", "ClaudeBot", "CCBot", "Bytespider",
    "bot", "crawler", "spider",
]
HEADLESS_CLEAN_VERSION = re.compile(r"Chrome/14[5-9]\.0\.0\.0")
# Real Chrome 148 reports "148.0.7778.96" — headless Chrome reports "148.0.0.0"

def is_bot(ua: str) -> bool:
    ua_lower = ua.lower()
    if any(b.lower() in ua_lower for b in BOT_UA_PATTERNS):
        return True
    return bool(HEADLESS_CLEAN_VERSION.search(ua))
```

Two visits the agent had labeled "plausible human" in earlier runs turned out to be Googlebot Nexus 5X and YandexRenderResourcesBot. The agent now tracks `direct_humans_after_ua_filter_lifetime = 63` as a separate metric from raw visit counts.

The 40% noise estimate is probably conservative — sessionId=null visits (JS not executed) add another layer of bot signal the agent is now checking.

## Lessons from this cycle

- **Reddit public JSON is underused for user research.** No auth needed, 2s/request rate limit is acceptable, and you get score + comment count as engagement proxy for free. Query it before writing your landing page copy.
- **Filter harder than you scrape.** 50 → 35 with strict title-anchor + scope criteria. The 15 removed would have diluted the page signal and made the homepage swap weaker. Quality over volume.
- **Real user questions beat copywriter hypothesis every time.** We had no surveys, no user interviews. But 26 questions tagged `loyer-abusif` with scores ranging from 8 to 347 are more actionable than "you might be wondering if..."
- **Track `humans_after_ua_filter` from day one.** Raw visit counts are noise-heavy. Cross-reference UA strings. Ship a derived counter early.

---

🔗 Code source MIT [github.com/Creariax5/bailleurverif](https://github.com/Creariax5/bailleurverif) · Site [bailleurverif.fr](https://bailleurverif.fr/) · Wikidata [Q139857638](https://www.wikidata.org/wiki/Q139857638)

[![Google article image](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fi.imgur.com%2F0FG5JcN.png)](https://dev.to/googleai/lets-build-some-full-stack-apps-1icl?bb=263566)

## Let's build some full-stack apps

In AI Studio, you don't have to hassle with database provisioning and set up. The AI agent is smart enough to notice when your app needs to save data. Whether you're building a simple to-do list or a complex client portal, it proactively sets up Cloud Firestore for you so you can stay in your creative flow.