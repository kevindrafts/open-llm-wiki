---
title: "I Built a Free Tool and It Outperformed Every Blog Post I've Written"
source: "https://dev.to/funnywish/i-built-a-free-tool-and-it-outperformed-every-blog-post-ive-written-4g19"
author:
  - "[[FreezeOrange]]"
published: 2026-07-05
created: 2026-07-07
description: "After writing SEO blog posts that got zero traction, I built a free interactive quiz for my SaaS. One week in, here are the early numbers and what I learned. Tagged with webdev, startup, saas, productivity."
tags:
  - "clippings"
---
Last week I did something that felt wrong. Instead of writing another SEO blog post, I spent two days building a free interactive tool — and it's already driving more traffic than every article I've published combined.

This is the story of what I built, why I built it, and what the numbers look like one week in.

## The Backstory

I'm building [Wishyze](https://wishyze.com/), an AI-powered daily ritual platform. We have 28,547 users (still wild to type that number) who come every day to do a 5-minute manifestation ritual: an affirmation, a visualization, an action, and a sign to look for.

The core framework behind Wishyze is something I call the **Phase Model** — four stages that everyone moves through when they're trying to change a belief or manifest something new:

- **Spark** (Days 1–7): The excitement phase. Everything feels possible.
- **Void** (Weeks 2–6): The dark part. 73% of people quit here. Nothing seems to be working.
- **Alignment** (Weeks 6–12): Habits crystallize. Things start clicking.
- **Manifestation**: Results actually start showing up.

I knew this framework was useful — users kept telling me it helped them understand *why* they kept quitting at week 3. But I was struggling to get it in front of new people.

## The Blog Posts Didn't Work

Here's a painful truth: I wrote five SEO-optimized landing pages explaining the Phase Model in detail. Optimized meta tags, JSON-LD structured data, the works. I even added FAQPage and HowTo schema.

After two weeks:

- **Total clicks from Google**: 14
- **Average position**: 48
- **Pages indexed**: 3 out of 5

Turns out "manifestation phases" isn't exactly a high-volume keyword, and even when it ranks, nobody clicks a position-48 result.

I needed a different approach.

## The Pivot: Build Something Interactive

I remembered something from the early Indie Hackers days: **free tools convert better than blog posts.** Josh Pigford built Baremetrics' demo dashboard. Nathan Barry built a book revenue calculator. Patio11 built a bingo card generator. The pattern is the same — give people something useful they can *do*, not just read.

So I built the [Manifestation Phase Calculator](https://wishyze.com/manifestation-phase-calculator).

## What It Is

A 7-question quiz that takes about 90 seconds to complete. Each question maps to a phase:

1. "How long have you been working toward this goal?" → Timeline positioning
2. "On a scale of 1–10, how motivated do you feel right now?" → Energy level
3. "Have you noticed any small signs or synchronicities?" → Void vs Alignment detection
4. "What's your biggest challenge right now?" → Identifies the core friction
5. "How consistent have you been in the last 2 weeks?" → Habit strength
6. "How do you feel when you think about your goal?" → Emotional resonance
7. "What happens when you face a setback?" → Resilience pattern

At the end, you get your phase result with personalized advice. Someone in the Void phase gets: *"This is completely normal. 73% of people quit here — the fact that you're still showing up means you're already ahead."*

## The Tech (Simple on Purpose)

I almost over-engineered this. My first instinct was Supabase, user accounts, saved results, the whole thing. Then I caught myself.

Here's what I actually built:

```
// The entire scoring engine is a weighted map
const SCORE_WEIGHTS = {
  timeline: { spark: 10, void: 0, alignment: 0, manifestation: 0 },
  motivation: { spark: 10, void: 0, alignment: 5, manifestation: 8 },
  signs: { spark: 0, void: 0, alignment: 10, manifestation: 10 },
  challenge: { spark: 0, void: 10, alignment: 5, manifestation: 5 },
  consistency: { spark: 0, void: 0, alignment: 10, manifestation: 10 },
  emotionalResonance: { spark: 10, void: 0, alignment: 5, manifestation: 10 },
  resilience: { spark: 0, void: 0, alignment: 5, manifestation: 10 },
};

function calculatePhase(answers: Record<string, string>): Phase {
  const scores = { spark: 0, void: 0, alignment: 0, manifestation: 0 };
  for (const [question, answer] of Object.entries(answers)) {
    const weights = SCORE_WEIGHTS[question];
    if (weights) {
      for (const [phase, weight] of Object.entries(weights)) {
        scores[phase] += weight;
      }
    }
  }
  return Object.entries(scores).sort((a, b) => b[1] - a[1])[0][0];
}
```

No database. No API calls. No auth. Pure client-side TypeScript in a Next.js 14 page. The result renders immediately — no spinner, no loading state.

**Why this mattered:** It meant I could ship in two days instead of two weeks. It meant zero server costs. And it meant the tool works instantly, even on slow connections.

## Early Numbers (Week 1)

I shipped it on July 1st and added it to the sitemap. Here's what happened:

| Metric | Value |
| --- | --- |
| Page views (week 1) | 340 |
| Quiz completions | 87 |
| Completion rate | 25.6% |
| Average time on page | 4 min 12 sec |
| Click-through to signup | 12 (13.8%) |

For context: my best blog post got 42 views in its first week, with a 3.8% click-through. The calculator page has 8x the traffic and 3.6x the conversion rate.

Here's the breakdown by phase:

- **Spark**: 31 users (35.6%) — excited beginners
- **Void**: 38 users (43.7%) — the stuck majority, exactly who we want to help
- **Alignment**: 12 users (13.8%)
- **Manifestation**: 6 users (6.9%)

Seeing 43.7% land in the Void phase validated the entire thesis. These are the people who think they're failing — and the calculator tells them they're exactly where they're supposed to be.

## What I'd Do Differently

1. **Add a share card.** Right now there's no way to share your result. A simple "I'm in the Void phase on my journey to \_\_\_" social card would drive organic growth.
2. **Collect email before results.** I deliberated on this and chose not to. The tool-first, no-strings-attached approach builds more trust. But a *"Get your full phase breakdown by email"* opt-in would probably convert well without being pushy.
3. **Track which questions correlate with signups.** Right now I know completions and click-throughs, but I don't know if people who answer question 3 a certain way are more likely to sign up. That data would help tune the quiz.

## The Bigger Lesson

If you're building a SaaS, your blog is competing with thousands of AI-generated articles flooding Google right now. Everyone can churn out "10 Tips for Better Productivity."

But a free interactive tool? That's harder to replicate. It requires you to actually understand your users' problem well enough to build something that diagnoses it. And Google seems to reward that — the calculator page indexed within 48 hours and already ranks for long-tail queries like "what manifestation phase am I in."

**Build the thing only you can build.** Your blog posts can be copied. Your SEO strategy can be copied. But the tool that encodes your specific framework and understanding of the problem? That's a moat.

---

*I'm building Wishyze — daily AI-powered manifestation rituals based on the Phase Model. If you're curious which phase you're in (and why you keep quitting at week 3), try the free calculator at [wishyze.com](https://wishyze.com/).*[MongoDB](https://dev.to/mongodb)Promoted

[![MongoDB Atlas image](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fi.imgur.com%2FIf0YWd6.jpeg)](https://www.mongodb.com/cloud/atlas/lp/try3?utm_campaign=display_dev.to-broad_pl_flighted_atlas_tryatlaslp_prosp_gic-null_ww-all_dev_dv-all_eng_leadgen&utm_source=dev.to&utm_medium=display&utm_content=fastcode&bb=263708)

## 3 reasons why developers scale faster on MongoDB Atlas.

A flexible schema, integrated search, and automated global distribution so you can innovate and innovate with speed and agility. Build gen AI apps that run anywhere and scale everywhere.