---
title: "How to Grow a Solopreneur Business from $0 to $30K (4 Hours a Week)"
source: "https://finntropy.substack.com/p/how-to-grow-a-solopreneur-business"
author:
  - "[[Finn Tropy]]"
published: 2026-05-25
created: 2026-05-28
description: "The three-step loop I ran on Saturdays and Sundays while everyone else said “post daily.”"
tags:
  - "clippings"
---
![](https://substackcdn.com/image/fetch/$s_!r-3Q!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F29c6399a-b69a-43fa-b8c1-3fbf79986ab0_1011x463.png)

When I stopped optimizing for likes and started running the weekend loop, revenue and subscribers finally moved on different schedules—and both went up.

I used to think the problem was time. You hear it everywhere: quit your job, post daily, grind until something breaks your way.

I had a 9–5 job and a family, which meant about **four hours on weekends** — not “when I find time,” but literally Saturday and Sunday blocks before someone needed something from me. I wanted a small side business anyway, something real rather than a fantasy exit, so I wrote. Medium first, then Substack.

What I didn’t have was an audience, an offer, or any clue what people wanted to read. I published across **197 different topics**, whatever caught my interest that week, which is a polite way of saying I was guessing in public.

Most posts got zero likes and zero reads. A few got a handful. The ones that actually moved — reads, comments, DMs — shared a pattern I only noticed in hindsight: I wasn’t writing prettier prose. I was sharing **[growth insights backed by analysis](https://medium.com/the-springboard/how-to-earn-more-from-your-writing-1b3f54c57999)**, numbers I’d pulled myself from Medium and Substack backends because the dashboards wouldn’t give them to me cleanly.

Here’s the part that still surprises me when I say it out loud: **the posts that failed were creative; the posts that worked were infrastructure disguised as content.**

Gumroad revenue went from **$529 in 2024** to **$21,146 in 2025** and **$9,832 through late May 2026** — **$31,507** total on Gumroad, past the **$30K** line I’d had in my head — while I kept writing on weekends.

I didn’t become a full-time creator. I stopped trusting platform dashboards and started building systems.

## Four hours, no audience, 197 guesses

If you’ve ever posted into silence, you know the feeling isn’t just disappointment. It’s a slow leak on motivation, because without feedback, you can’t tell whether the idea was wrong, the headline was wrong, or you simply haven’t found the hundred people who care yet. I was in that hole for a long stretch — 197 topics, no Ideal Customer Profile, no product, just weekly output and hope.

The scatter plot of my early writing career would look embarrassing if I charted it honestly: a long flat tail of zeros, and a small cluster of spikes wherever I did the uncomfortable work — opened the network tab, exported something ugly into CSV, built a spreadsheet, and wrote about [what the numbers actually said instead of what I wished they’d say.](https://medium.com/the-springboard/the-real-reason-why-your-stories-collect-dust-e99aedaf25a2)

![](https://substackcdn.com/image/fetch/$s_!DBFL!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc26e0879-bda9-4bb7-afa1-207ced1bd3cf_1100x538.png)

Engagement and responses to my 197 random post topics over time

If you’re staring at a blank analytics page, wondering why you’re still showing up, I don’t think you’re broken.

**Your tools are** — or more precisely, the metrics you’re being asked to optimize for were never designed to answer *“what should I build next?”*

## Two problems worth solving

After enough weekends, I stopped telling myself the problem was *“I need better content.”* Creators around me were quitting for the same underlying reason: no readers, no actionable feedback, no loop they could run again next week.

Two gaps kept showing up, and they were specific enough that I could actually build toward them.

- **Analytics that serve the platform, not you.** Medium, Substack, and the rest surface likes, shares, follower counts, subscriber totals — metrics that drive ***their*** business and your anxiety, but rarely tell you which post pulled a new subscriber, which Note converted, or which topic correlates with revenue. I wanted decisions, not trophies. Platforms don’t ship that cleanly. By design.
- **Scheduling for Substack Notes.** Everyone wanted it. Substack didn’t ship it for a long time. That sounds like a small complaint until you’ve written a good Note at 11 pm and watched it disappear under Monday morning noise because you had no way to queue it.

I didn’t pick one skill and hope. I stacked **writing, analytics, and software** on purpose — not tips, but to build infrastructure.

![](https://substackcdn.com/image/fetch/$s_!TlFL!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fbf31f33e-5ac1-45a0-ba89-cbc7014deddb_1122x1402.png)

What Substack shows you (likes, followers, vanity totals) vs what you need to decide (subscriber source, note-to-sub conversion, cohort behavior);

You’re not overwhelmed because you’re lazy. You’re ***trying to run a business on a dashboard built for someone else’s KPIs***.

## Build infrastructure, sell the extract

Here’s what those four weekend hours turned into, in rough order — not a master plan at the start, more like one obvious next step after the last one hurt enough.

I figured out API calls to pull raw data from the Medium and Substack backends, then wrote Python scripts to dump everything into CSV files. Ugly, reliable, under my control — no waiting for a platform to provide an export button.

I analyzed in Google Sheets first because spreadsheets are honest: you see the #REF! cells and the outliers and the rows you wish weren’t there. Then I wrote [posts about what I found](https://medium.com/the-springboard/how-to-learn-who-your-audience-is-on-medium-4083ffe9e2b1), which is when content stopped being the product for me. **Content became marketing for the system I was building.**

The first thing anyone paid for on Gumroad was embarrassingly simple: [a Google Sheets extract of the top 20 Medium writers](https://medium.com/the-springboard/how-to-create-a-digital-product-in-2-days-b90a2f2a6369) posts plus publicly available metrics. Not a course, not a community, just a **simple** **dataset** that saved someone else a weekend of web scraping.

DMs taught me the next lesson fast: most people don’t run Python from a terminal. I’d built for myself. So I taught myself Chrome extensions — something I’d never done — [shared v1 in a post](https://finntropy.substack.com/p/how-to-grab-your-medium-earnings), later sold an improved version on Gumroad, then built Substack Notes scheduling with Chrome alarms because the feature gap was costing me (and everyone else) published work.

Support messages became the roadmap. Some users couldn’t get the extension working; some needed new workflows I’d never imagined.

Most weekends after that looked the same: fix what broke, ship a version bump, post a How-To so the next person wouldn’t have to email me for the same answer. Tedious? Sometimes. But it was a **loop** — *write, measure, build, sell, support, repeat* — instead of another random topic in the 197 pile.

![](https://substackcdn.com/image/fetch/$s_!5-qB!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F528bbb89-64cd-46dd-82eb-388375ec1296_1024x1536.png)

Everyone said post daily. I blocked Sat–Sun (~4 hrs) and ran this loop instead: write → find the gap → build the tool → read the data → next post or product. The red X is intentional.

## The numbers that matter (not likes)

Audience growth and revenue didn’t move on the same schedule. The list compounded; the money inflected later, when the infrastructure shipped and people could buy the shortcut instead of reading about how I built it.

### Medium

![](https://substackcdn.com/image/fetch/$s_!gIx5!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe323f289-92d7-4241-8f98-84b68fd7f2cc_353x236.png)

Followers climbed; Medium subs stayed tiny.  
That was fine — Medium was an experimental lab, not the business.

### Substack

![](https://substackcdn.com/image/fetch/$s_!1fwV!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F00f3d10b-5cbd-435a-ab67-42c4ecef01c9_361x135.png)

Real audience, compounding list — and in 2025, especially, a lot of Notes experiments behind the subscriber line. Still not the whole story.

### Gumroad

![](https://substackcdn.com/image/fetch/$s_!8U93!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3183c742-e8a8-4115-8d7e-3b2a46debad4_1400x276.png)

**$529 in 2024** — 87 sales at ~$6 average, four products (3 of them were free) — was an experiment, not a business.  
**$21,146 in 2025** — 1,285 sales, eleven products, ~$16 average — is when it became one. The cliff between 2024 and 2025 wasn’t *“I posted more”*; look at the Substack numbers above, posting volume alone doesn’t explain it.

It was the first free data extract, then free + paid Chrome extensions, then support-driven iterations (534 more sales already in 2026, average sales ~$18), all hung on the same data loop I’d been writing about in public.

I’m still weekend-bound. No hustle porn, not burning midnight oil — just a few hours on a system I actually use.

If you want the messier sequel — revenue that’s real, a platform shipping your product category natively, the week I almost killed the flagship — that’s [22 Months. $26,752 Revenue. 721 Customers. The Tool I Almost Killed Twice](https://finntropy.substack.com/p/22-months-26752-721-customers-the).

This post is how the first ~$31K on Gumroad showed up.

## What to do if you’re stuck at $0

I wouldn’t write 197 random posts hoping one lands.

I’d run one loop: pull data the platform won’t hand you cleanly, publish **one** insight post that proves you understand the number (not that you’re clever), then ***ship the smallest tool or dataset that saves the next creator a weekend or few hours of work***.

That’s how four hours compound past $30K on Gumroad — not by becoming a full-time writer, but by selling the infrastructure you already needed for yourself.

Treat every post as marketing for a system. Treat every support email as a feature spec. ***This is boring advice until you’ve watched it work***.

## If you want the infrastructure without building it from scratch

I built [StackContacts](https://finntropy.gumroad.com/l/stackcontacts) because I was tired of flying blind on my own publication — subscriber events, Notes metrics, Gumroad correlation, and the decisions platforms smooth over.

I built [Substack Pro Studio](https://finntropy.gumroad.com/l/substack_pro_studio) because scheduling and workflow gaps were costing me Notes I would’ve published if the tool had existed.

You can build your own loop from CSVs and extensions; I did, and I still think that’s the right first move if you have the patience. Or you can install mine and spend your four hours on the next experiment instead of the next scrape.

**Honest question:** What’s the ***one metric your platform shows you that you wish you could ignore?*** Reply and tell me — I read them.

— Finn