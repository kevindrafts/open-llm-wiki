---
title: "I Built an AI System to Run My Content Operation. Here's the Whole Thing."
source: "https://www.thedaringcreatives.com/the-ai-system-behind-this-site/"
author:
  - "[[The Man in Yellow Sunglasses]]"
published: 2026-06-08
created: 2026-06-10
description: "A one-person setup — orchestrator, pitch generator, optimizer, scheduler — that pitches ideas, researches with Gemini, drafts with Claude, and ships across the site, newsletter, and four social accounts. Built on my own dime to learn AI by making something."
tags:
  - "clippings"
---
// SYSTEM: DIGEST // LIVE

AI WORKFLOW

OPINION

TUTORIALS

Most of what goes out under The Daring Creatives — the articles, the newsletter, the posts across Threads and LinkedIn and Instagram — runs through a system I built. A loose collection of scripts, APIs, and a few stubborn rules, wired together so one person can operate something that normally takes a small team.

The honest backstory first: nobody paid me to build this. No client, no budget — my own time and my own money. I built it to learn AI the way that actually sticks for me, which is by making something real with it instead of reading about it. And since I was footing the bill anyway, I figured it should be something I'd genuinely want to read and tinker with — fun enough to keep diving into, and good enough to put in front of someone as proof of how far I've come.

I wrote [a first version of this overview](https://www.thedaringcreatives.com/how-we-built-our-ai-content-pipeline-and-whats-actually-running-it/) back in April, when the whole thing was mostly Obsidian and a couple of Claude prompts. It's grown a lot since — most of what's below didn't exist then. So treat this as the current map. Most of it is built from tools you already have access to, and once you see the shape of it, you'll probably spot a piece you could build for yourself this weekend.

Let me start with what I was actually trying to do.

## The goal

I'm one person, and I wanted to run a real content operation anyway — a site that publishes a few times a week, a weekly newsletter, four social accounts, and a serialized fiction world running underneath all of it.

The catch was time. The repetitive shit — researching a topic, formatting a draft, resizing images, scheduling posts, remembering what I already published — that's the work I'd happily hand off. What I wanted to keep was the deciding: what to make, what's good enough to ship, what actually sounds like me.

So the whole system is built around one split. The AI does the labor. I make the calls. Everything else is plumbing in service of that line — and building that plumbing, piece by piece, is how I actually learned this stuff.

## The core loop

Underneath all the parts, there's one loop the whole thing runs on:

Ideas → I approve → research and draft → I review → publish and promote → measure → learn.

Each step is a specific program doing a specific job. Here's who does what — or click through it yourself:

THE DARING CREATIVES · CONTENT PIPELINE ◉ HEALTHY · 3/DAY · NEXT 1:00 PM PT

PitchApproveResearchDraftReviewPublishPromoteMeasure

sherman@orchestrator:~$propose-topics --morning --mix 50/50

Sherman pitches the ideas

Every morning a script reads the news feed, Search Console (via Sebastian) and our own build log, then asks Claude for a shortlist — each with a reason. About half come from our own work. Nothing is written yet. **Pick one to pursue:**

SHERMAN · orchestrator · propose-topics.js, 06:35 daily

## The systems that do the work

I gave the moving parts names, because "the script" stops being useful once there are a dozen of them. These are the main ones.

**The orchestrator** is the heartbeat. It's a script that wakes up on a schedule, looks at what shipped this week versus what I planned, and decides what the system should work on next. It used to just draft whatever it thought was missing — which is how I once opened the folder to seventeen articles I never asked for. Now it defers to the pitch queue instead, which is the single best change I've made.

**The pitch generator** is what fills that queue. Once a day it reads my AI news feed, my Google Search Console data, and — the part I like most — my own build log, then asks Claude to propose a short list of things worth writing about. About half the pitches now come from the work itself: a bug I fixed, a decision I made, a system I shipped. I approve the ones I want; nothing gets researched or drafted until I do.

**Research and drafting** is a two-model handoff. When I approve a pitch, Gemini does the deep research — it's good at pulling current, wide context. Then Claude (Sonnet) writes the first draft, working against [a file of my voice patterns](https://www.thedaringcreatives.com/teach-ai-brand-voice/) the system has learned from my past edits, so the draft starts closer to how I actually talk. It's a starting point. I rewrite it.

**The optimizer** is the pass that runs after a draft exists. It adds internal links — but only to pages that genuinely exist on the site, checked against an index of real URLs, because nothing tanks trust like a link to a page that isn't there. It also handles SEO housekeeping: titles, meta descriptions, tags.

**The scheduler** takes an approved piece, pushes it to Ghost (the CMS this site runs on) through Ghost's Admin API, and books it into an open slot on the calendar. No copy-paste, no browser tabs.

**The distributor** fans each published piece out to social. It reshapes the article into posts sized and voiced for each platform — Threads sounds nothing like LinkedIn, which sounds nothing like Instagram — and queues them through Buffer. One article becomes a week of distribution without me babysitting it.

## The crew

Here's the part people find strange, and it's my favorite. The dashboard isn't a wall of charts. It's three characters who report in.

Sherman is the creative director — he runs what I call Central Dispatch and files a short status every morning (written by Claude Sonnet against the day's real data): what shipped, what's in the queue, what we should do next. Wilson is the engineer; he scans the pipeline for things that broke and quietly fixes what he can. Sebastian watches the audience and search data and flags pieces worth promoting.

They're not magic — under the hood they're prompts with access to the same logs and data the rest of the system writes. But giving it a few distinct voices turned a boring dashboard into something I actually want to open, which, when it's your own money and your own free time, matters more than it sounds.

## The rest of it

**Images** come from Gemini — it generates them, including [a consistent cast](https://www.thedaringcreatives.com/ai-image-consistency/) for the fiction side. I browse and assign those by hand; I didn't want the machine choosing the pictures.

**The watchers** are small jobs that keep the thing honest — checking that posts go out on cadence, that the data feeding decisions is fresh, that nothing's silently stuck. When something breaks, I'd rather hear it from my own system than from a reader.

## What it's actually built on

None of this is exotic. The CMS is Ghost. Social posting runs through Buffer. The research and images run on Gemini; the writing — drafts, social copy, the morning dispatch — runs on Claude, mostly Sonnet. The glue is a pile of Node scripts run by cron, the same scheduler that's been sitting on every Mac and Linux machine for decades. The dashboard is a small local web app. That's the whole stack.

I point that out because "AI content system" sounds like something you need a company and a budget to build. It isn't. It's a few APIs, a scheduler, and the patience to wire up one piece at a time.

## If you want to build your own

Start with one link, not the whole loop.

Pick the part of your own work that's the most repetitive and the least creative, and automate just that. Maybe it's reshaping a finished post into your social drafts. Maybe it's a morning script that gathers everything you need to read before you start. Get one piece working, live with it a week, then add the next. That's genuinely how this got built — it didn't arrive as a system, it accreted one annoyance at a time, and each piece taught me what I needed to build the next.

The most important rule is a human one: the approve step. The orchestrator can pitch, the optimizer can polish, the scheduler can publish, the crew can report — but nothing goes out under my name until I've read it and said yes. Everything that ships is something I chose. The machine handles the work, not the judgment.

This is the first piece in a series I'm going to keep writing as I build — I'll pull apart each subsystem in its own post, including the stuff that breaks along the way. If there's a part you want me to open up first, tell me.

Most of what goes out under The Daring Creatives — the articles, the newsletter, the posts across Threads and LinkedIn and Instagram — runs through a system I built. A loose collection of scripts, APIs, and a few stubborn rules, wired together so one person can operate something that normally takes a small team.

The honest backstory first: nobody paid me to build this. No client, no budget — my own time and my own money. I built it to learn AI the way that actually sticks for me, which is by making something real with it instead of reading about it. And since I was footing the bill anyway, I figured it should be something I'd genuinely want to read and tinker with — fun enough to keep diving into, and good enough to put in front of someone as proof of how far I've come.

I wrote [a first version of this overview](https://www.thedaringcreatives.com/how-we-built-our-ai-content-pipeline-and-whats-actually-running-it/) back in April, when the whole thing was mostly Obsidian and a couple of Claude prompts. It's grown a lot since — most of what's below didn't exist then. So treat this as the current map. Most of it is built from tools you already have access to, and once you see the shape of it, you'll probably spot a piece you could build for yourself this weekend.

Let me start with what I was actually trying to do.

## The goal

I'm one person, and I wanted to run a real content operation anyway — a site that publishes a few times a week, a weekly newsletter, four social accounts, and a serialized fiction world running underneath all of it.

The catch was time. The repetitive shit — researching a topic, formatting a draft, resizing images, scheduling posts, remembering what I already published — that's the work I'd happily hand off. What I wanted to keep was the deciding: what to make, what's good enough to ship, what actually sounds like me.

So the whole system is built around one split. The AI does the labor. I make the calls. Everything else is plumbing in service of that line — and building that plumbing, piece by piece, is how I actually learned this stuff.

## The core loop

Underneath all the parts, there's one loop the whole thing runs on:

Ideas → I approve → research and draft → I review → publish and promote → measure → learn.

Each step is a specific program doing a specific job. Here's who does what — or click through it yourself:

THE DARING CREATIVES · CONTENT PIPELINE ◉ HEALTHY · 3/DAY · NEXT 1:00 PM PT

PitchApproveResearchDraftReviewPublishPromoteMeasure

sherman@orchestrator:~$propose-topics --morning --mix 50/50

Sherman pitches the ideas

Every morning a script reads the news feed, Search Console (via Sebastian) and our own build log, then asks Claude for a shortlist — each with a reason. About half come from our own work. Nothing is written yet. **Pick one to pursue:**

SHERMAN · orchestrator · propose-topics.js, 06:35 daily

## The systems that do the work

I gave the moving parts names, because "the script" stops being useful once there are a dozen of them. These are the main ones.

**The orchestrator** is the heartbeat. It's a script that wakes up on a schedule, looks at what shipped this week versus what I planned, and decides what the system should work on next. It used to just draft whatever it thought was missing — which is how I once opened the folder to seventeen articles I never asked for. Now it defers to the pitch queue instead, which is the single best change I've made.

**The pitch generator** is what fills that queue. Once a day it reads my AI news feed, my Google Search Console data, and — the part I like most — my own build log, then asks Claude to propose a short list of things worth writing about. About half the pitches now come from the work itself: a bug I fixed, a decision I made, a system I shipped. I approve the ones I want; nothing gets researched or drafted until I do.

**Research and drafting** is a two-model handoff. When I approve a pitch, Gemini does the deep research — it's good at pulling current, wide context. Then Claude (Sonnet) writes the first draft, working against [a file of my voice patterns](https://www.thedaringcreatives.com/teach-ai-brand-voice/) the system has learned from my past edits, so the draft starts closer to how I actually talk. It's a starting point. I rewrite it.

**The optimizer** is the pass that runs after a draft exists. It adds internal links — but only to pages that genuinely exist on the site, checked against an index of real URLs, because nothing tanks trust like a link to a page that isn't there. It also handles SEO housekeeping: titles, meta descriptions, tags.

**The scheduler** takes an approved piece, pushes it to Ghost (the CMS this site runs on) through Ghost's Admin API, and books it into an open slot on the calendar. No copy-paste, no browser tabs.

**The distributor** fans each published piece out to social. It reshapes the article into posts sized and voiced for each platform — Threads sounds nothing like LinkedIn, which sounds nothing like Instagram — and queues them through Buffer. One article becomes a week of distribution without me babysitting it.

## The crew

Here's the part people find strange, and it's my favorite. The dashboard isn't a wall of charts. It's three characters who report in.

Sherman is the creative director — he runs what I call Central Dispatch and files a short status every morning (written by Claude Sonnet against the day's real data): what shipped, what's in the queue, what we should do next. Wilson is the engineer; he scans the pipeline for things that broke and quietly fixes what he can. Sebastian watches the audience and search data and flags pieces worth promoting.

They're not magic — under the hood they're prompts with access to the same logs and data the rest of the system writes. But giving it a few distinct voices turned a boring dashboard into something I actually want to open, which, when it's your own money and your own free time, matters more than it sounds.

## The rest of it

**Images** come from Gemini — it generates them, including [a consistent cast](https://www.thedaringcreatives.com/ai-image-consistency/) for the fiction side. I browse and assign those by hand; I didn't want the machine choosing the pictures.

**The watchers** are small jobs that keep the thing honest — checking that posts go out on cadence, that the data feeding decisions is fresh, that nothing's silently stuck. When something breaks, I'd rather hear it from my own system than from a reader.

## What it's actually built on

None of this is exotic. The CMS is Ghost. Social posting runs through Buffer. The research and images run on Gemini; the writing — drafts, social copy, the morning dispatch — runs on Claude, mostly Sonnet. The glue is a pile of Node scripts run by cron, the same scheduler that's been sitting on every Mac and Linux machine for decades. The dashboard is a small local web app. That's the whole stack.

I point that out because "AI content system" sounds like something you need a company and a budget to build. It isn't. It's a few APIs, a scheduler, and the patience to wire up one piece at a time.

## If you want to build your own

Start with one link, not the whole loop.

Pick the part of your own work that's the most repetitive and the least creative, and automate just that. Maybe it's reshaping a finished post into your social drafts. Maybe it's a morning script that gathers everything you need to read before you start. Get one piece working, live with it a week, then add the next. That's genuinely how this got built — it didn't arrive as a system, it accreted one annoyance at a time, and each piece taught me what I needed to build the next.

The most important rule is a human one: the approve step. The orchestrator can pitch, the optimizer can polish, the scheduler can publish, the crew can report — but nothing goes out under my name until I've read it and said yes. Everything that ships is something I chose. The machine handles the work, not the judgment.

This is the first piece in a series I'm going to keep writing as I build — I'll pull apart each subsystem in its own post, including the stuff that breaks along the way. If there's a part you want me to open up first, tell me.