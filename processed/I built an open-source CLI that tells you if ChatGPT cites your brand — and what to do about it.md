---
title: "I built an open-source CLI that tells you if ChatGPT cites your brand — and what to do about it"
source: "https://dev.to/alex-isa/i-built-an-open-source-cli-that-tells-you-if-chatgpt-cites-your-brand-and-what-to-do-about-it-31gg"
author:
  - "[[Alex Isa]]"
published: 2026-06-10
created: 2026-06-12
description: "aeo-platform is a zero-dependency Node CLI that measures whether ChatGPT, Claude, Gemini, and Perplexity cite your product, then exports a JSON you paste into any AI for a 30-mission fix plan. Here's how to run it in five minutes — with real before/after numbers. Tagged with aeo, opensource, ai, seo."
tags:
  - "clippings"
---
Your users have started asking ChatGPT and Perplexity instead of Google. So here is the uncomfortable question: when someone asks an AI engine "what is the best tool for `<your category>` ", does your product show up in the answer? Most founders have no idea. I didn't either, until I measured it — and the gap was nowhere near where I expected.

So we built a CLI to measure it. It's called **aeo-platform**, it's MIT-licensed, it has zero runtime dependencies, and it runs entirely on your machine. This post is the five-minute version: install it, point it at your domain, and read the gap. I'll show you the exact commands and the real before/after numbers from running it on one of our own products.

> Quick framing on terms: **AEO** (answer engine optimization) is just SEO's younger sibling for AI answers — getting *cited inside the AI's response* instead of ranking on a SERP. Some people call it GEO. Same field.

## TL;DR — three commands

```
npm install -g aeo-platform

export OPENAI_API_KEY="sk-proj-..."   # required
export GEMINI_API_KEY="AIzaSy..."     # required

aeo-platform init --yes --brand=YOURBRAND --domain=YOURDOMAIN.COM --auto \
  && aeo-platform run \
  && aeo-platform report
```

`init` auto-discovers your category and writes three commercial buyer queries to a local `.aeo-tracker.json`. `run` fires those queries at each engine and scores the answers. `report` opens a single-file HTML report in your browser. The whole thing installs in under a second (no dependency tree to resolve) and writes everything to disk under `aeo-responses/YYYY-MM-DD/` — nothing is sent to a hosted dashboard.

OpenAI and Gemini keys are mandatory (they also power a two-model cross-check that filters hallucinated brand mentions). Anthropic and Perplexity keys are optional — each one just adds a column to the report.

## What it actually measures

A single `run` sends your buyer queries to four engines through their official REST APIs — no scraping, no proprietary black-box score:

| Engine | Model | Type |
| --- | --- | --- |
| ChatGPT (OpenAI) | `gpt-5-search-api` | web-search |
| Gemini (Google) | `gemini-2.5-flash` | web-search |
| Claude (Anthropic) | `claude-sonnet-4-7` | mostly training-data |
| Perplexity | `sonar-reasoning` | web-search |

For each engine-and-query cell it records whether your brand appears in the answer text, only in the cited sources, or not at all, then rolls four signals into a single 0–100 **Unified Visibility Index (UVI)**: Presence (35%), Sentiment (25%), Rank (20%), Citation (20%). The weights live in the source (`lib/report/visibility-index.js`) — when a signal has no data in a run, its weight re-normalises across the others instead of inventing a phantom value. It also does a zero-LLM-cost crawlability audit (are the 12 known AI bots — GPTBot, ClaudeBot, PerplexityBot, and friends — actually allowed to read your site?) and checks off-page authority signals (Wikipedia, Reddit, GitHub, Wikidata).

The exit codes are CI-friendly, which is the part that made me wire it into a weekly cron:

```
0  score stable or improved
1  score dropped past your regressionThreshold  -> alert
2  all checks returned zero mentions            -> normal on day 1
3  all providers errored                        -> check keys/billing
```

## Measuring is the easy half — and where most tools stop

Here is the thing nobody tells you when you buy an AI-visibility dashboard: the chart that tells you *where* you're invisible does not tell you *what to do next*. You're left translating six tabs of bars into a to-do list, and if you don't already do AEO for a living, that translation is exactly the hard part.

So the second thing aeo-platform does is generate the to-do list. The same `run` that produces the score also exports a **JSON brand-context block** — your visibility index, per-engine citation deltas, top competitors, citation gaps, crawl matrix, authority signals. You paste that JSON into your *own* ChatGPT/Claude/Gemini chat (the subscription you already pay for — no extra API spend) and ask for a 30-mission plan. What comes back is keyed to *your* gaps: the specific competitor the run named, the specific URLs the engines are citing, the weakest engine to fortify first.

I have not seen a hosted AEO vendor ship this, and the reason is structural: a paste-into-AI plan cannibalises the dashboard moat. The moment you take the JSON to your own AI chat, the vendor's UI stops being the destination. Open-source has the opposite incentive — hand you the data and win when you take it wherever you want.

## A real before/after (on our own product, no hypotheticals)

I'm not going to wave a hypothetical chart at you. We ran this loop on one of our own products — **TypelessForm**, a voice-to-form widget — over four weekly runs, on three real buyer queries like *"best voice form filling tools 2026"*. Every number below comes from an actual aeo-platform report covering 2026-04-23 to 2026-05-25.

**Where it started:** 33% presence across twelve checks (four engines × three queries). The headline number mattered less than its *shape* — one engine returned zero mentions on every query while another was within reach. That per-engine asymmetry is what tells you where to spend your two hours, and it's exactly what a single composite score hides.

**What the plan said to do first:** the highest-leverage mission wasn't promotional, it was structural — add a 40-to-60-word answer capsule directly under every H2 heading that lacked one. All four engines pull from the same heading-anchored paragraphs, so one pass multiplies extractability across all twelve cells at once. The plan also named the one competitor the run actually surfaced (AnveVoice, counted at five mentions against our seven) and told us explicitly *not* to touch crawlability or schema — those were already solved. A plan that tells you what to skip is worth as much as one that tells you what to do.

**What changed when we re-measured:**

| Metric | Start | End (2026-05-25) |
| --- | --- | --- |
| Overall presence | 33% (04-23) | 58% |
| Unified Visibility Index | — | 65 / 100 |
| Gemini hit rate | 1 of 3 (05-18) | 3 of 3 |
| Claude hit rate | 1 of 3 (05-18) | 0 of 3 (regressed) |

Presence rose 25 points, with a +16 jump in the final week. Gemini went from missing two of three queries to citing us on all three.

Now the most instructive cell — **Claude went the other way.** It briefly held a citation, then lost it, dropping to 0 of 3. That is exactly what a training-data engine looks like: Claude does not run a live web search for most queries, so a fresh blog post does not durably move it — a citation can appear and vanish on the next refresh. The fix lever for a training-data engine is completely different (npm presence, GitHub stars, Hacker News, press) and operates on a six-to-twelve-month timeline. aeo-platform classifies each engine *before* recommending, so it never tells you to "write more content" to fix Claude — a recommendation that would have wasted the work. Knowing which lever applies to which engine is half the value.

One honest note, because it's the line between a case study and a sales pitch: I cannot prove any single mission caused any single cell to flip. AI answers shift week to week for reasons nobody controls — which is *precisely why the tool re-measures* instead of declaring victory after one run. What I can show is the measured before-and-after, captured by the same reproducible tool on both ends. The trend is real; the attribution is a hypothesis the next run tests.

## What the generated plan actually reads like

The plan comes back in plain English — no UVI weights, no engine taxonomy, just what's true and who's winning. A couple of real missions from the TypelessForm run, so you can see the texture:

> **Mission 1 — Add short answers under your headings.** "AI engines like to quote a short, direct answer that sits right under a heading. Your homepage has 9 section headings but only 1 has such an answer beneath it. This is the cheapest way to become quotable on ChatGPT, Gemini, and Perplexity." How: under 4 headings add a 40–60 word answer capsule, publish. ~90 min.
> 
> **Mission 19 — List on AlternativeTo.** "AlternativeTo is a software directory that AI engines pull from, and it's the cheapest way to reach Claude (which never visits your site)." ~45 min.

And the part that earns the most trust is the part that tells you to do *nothing*. The plan ends with an explicit "what NOT to do" section:

> "Don't create a Wikipedia or Wikidata page yet. No independent press has written about you, so a self-made entry gets deleted and leaves a permanent 'not notable' mark. Earn a few press mentions first."

A generic AEO checklist would have sent you to build a Wikidata entry — which gets deleted as non-notable and leaves a lasting strike against you. Recognising that trap, and skipping it, protects the limited time of someone who has two hours a week.

## When you should NOT use this

This is a CLI built for doing, not a dashboard built for monitoring. If you have an in-house team watching AI visibility continuously and you want team SSO, Slack alerts, or a multi-brand management UI, a hosted tool like Profound or Peec is the better fit. aeo-platform is for the founder or small team who needs the single next move and a prompt to execute it — and who can't justify a subscription for something whose direct-API cost is a few cents a week.

|  | Typical hosted dashboard | aeo-platform |
| --- | --- | --- |
| Primary output | Charts (where you're invisible) | Paste-into-AI action plan (what to do next) |
| Where it runs | Hosted SaaS, your data on their servers | Local CLI, your data stays on disk |
| Pricing | Monthly subscription | Free, MIT, zero dependencies |
| Engine advice | Often one strategy for all engines | Classifies each engine; different lever per engine |

## Run it on your own brand

The fastest way to understand AEO is to see your own product measured — the gap is almost always somewhere you didn't expect. Start with one engine and a handful of real buyer queries:

```
npm install -g aeo-platform
aeo-platform init --yes --brand=YOURBRAND --domain=YOURDOMAIN.COM --auto
aeo-platform run
aeo-platform report
```
- npm: [npmjs.com/package/aeo-platform](https://www.npmjs.com/package/aeo-platform) (current version 1.1.6)
- source + issues: [github.com/webappski/aeo-platform](https://github.com/webappski/aeo-platform)

This tool is built and maintained by [Webappski](https://webappski.com/), an answer-engine-optimization studio — we run this exact measure-plan-improve loop on our own products before selling it as a service. The tool is free and open-source; the only paid offerings are downstream and optional (a $29 paste-assist plan tier, and full AEO consulting from around $3,500 for companies that want us to run the loop end to end).

If you want the long version — the full UVI methodology, the complete 30-mission plan the tool handed us, the engine-by-engine breakdown — the canonical write-up with the whole worked example is here: **[aeo-platform: the open-source tool that measures AI visibility, generates a plan, and improves it](https://webappski.com/en/posts/aeo-platform-measure-plan-improve-ai-visibility-2026)**.

What's your own brand's number? Run it and tell me how far off your guess was — mine was way off.

*— Alex Isa, Webappski*

[![Google article image](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fi6mj0yymgm9gmhlz7l4y.png)](https://dev.to/googleai/building-capabilities-for-a-multi-agent-system-with-google-adk-mcp-and-cloud-run-ab9?bb=263437)

## Building Capabilities for a Multi-Agent System with Google ADK, MCP, and Cloud Run

My team's mission is to accelerate the developer journey from writing code to running secure AI workloads on Google Cloud. To help developers succeed, we focus on identifying their most pressing questions and building demos that provide straightforward, easy-to-implement solutions.