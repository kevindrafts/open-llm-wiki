---
title: "What if every company had an internal hosting platform like Shopify’s Quick?"
source: "https://blog.val.town/shopify-quick-for-all"
author:
  - "[[Pete Millspaugh]]"
published: 2026-06-22
created: 2026-09-08
description: "Val Town is a sort of Third Space for non-prod code"
tags:
  - "clippings"
---
[*Quick*](https://shopify.engineering/quick) is Shopify’s “internal hosting platform for the AI era.” It looks both useful and fun. Reading about Quick struck a chord with us because they were [pretty much describing Val Town](https://x.com/pushmatrix/status/2064722585019969727) —but only for Shopify employees.

The tl;dr on Quick is that any Shopify employee can (vibe) code a website or tool, upload a folder of HTML and other assets, and get back a secure `something.quick.shopify.io` URL. They also have a simple API for saving data, storing files, and using LLMs and websockets. We’d like to know: what other companies have something like this, or want it?

<video src="https://pub-039d2b636d8e46199759f7a9e1e076a3.r2.dev/summer.mp4" controls=""></video>

Before continuing, I’ll use this paragraph to wonder publicly whether Val Town might have even inspired Quick. Tobi himself [has used Val Town](https://www.val.town/x/tobi/qs), which he called “a competent implementation of something I think should exist.” Hm.

## Architecture

Each app in Val Town is a folder of code (called a “val”). When you or your agent edit the code, your app deploys in 100 milliseconds to a URL like `something.val.run`.

![architecture-1.png](https://imagedelivery.net/iHX6Ovru0O7AjmyT5yZRoA/7a90f025-615d-4ebf-4292-5fd7ff74dc00/public)

As you can see in the diagram, Val Town code runs on the Deno runtime. And you also get some platform batteries: SQLite, blob storage (S3), Slack and Google connectors, and LLM APIs.

![architecture-2.png](https://imagedelivery.net/iHX6Ovru0O7AjmyT5yZRoA/837b3bf0-4626-4a71-7b5a-54a3e2a1c800/public)

And actually, apps on Val Town don’t just run on HTTP URLs like `aviato.val.run`. You can also trigger code manually, from your agent (MCP), on a cron, or via email.

Outside of those platform batteries and triggers, apps on Val Town are just standard JavaScript. Import libraries from npm and node, call APIs, return HTML, respond to webhooks. And for keeping apps private to you and your team, there’s OAuth middleware.

## Agents

Some users hand- or vibe-code within the [val.town](https://val.town/) website, and others hook into our MCP server from their agent (and never even see the Val Town frontend). So while we do have extensive [docs](https://docs.val.town/), copy-pasting `npx plugins add val-town/plugins` into your agent is often all you need to get started.

Since the advent of frontier LLMs and agents, we’ve seen both engineers with decades of experience *and* business or growth builders who’ve never touched code using Val Town.

## Adoption

I mentioned up top that Quick looks both useful and fun. Well, emergent behavior on Val Town since launching a few years ago has definitely been both serious and silly, too.

Justin Uberti, Head of Realtime at OpenAI, uses Val Town to demo new voice models, like [realtyper.val.run](https://realtyper.val.run/), [hello-realtime.val.run](https://hello-realtime.val.run/), and another val that translates international radio stations using `gpt-realtime-translate`.

<video src="https://pub-039d2b636d8e46199759f7a9e1e076a3.r2.dev/gpt-realtime.mp4" controls=""></video>

Geoffrey Litt built [Stevens, an AI butler](https://www.geoffreylitt.com/2025/04/12/how-i-made-a-useful-ai-assistant-with-one-sqlite-table-and-a-handful-of-cron-jobs) (in April of last year—imagine what Stevens could do today).

<video src="https://pub-039d2b636d8e46199759f7a9e1e076a3.r2.dev/stevens.mp4" controls=""></video>

Peter Liu made a mesmerizing [SF muni bus tracker](https://pql.val.run/pieces/allthebuses/#3).

<video src="https://pub-039d2b636d8e46199759f7a9e1e076a3.r2.dev/sfmuni.mp4" controls=""></video>

Robin Sloan used Val Town email handling to [track preorders](https://www.robinsloan.com/lab/at-home-in-high-dimensional-space/#valtown) of his book, *Moonbound*.

![robinsloan.png](https://imagedelivery.net/iHX6Ovru0O7AjmyT5yZRoA/bea70798-82e0-4a0e-591f-c6bf299eef00/public)

Paul Kinlan, Chrome DevRel Lead at Google, makes many vals using our AI agent [Townie](https://www.val.town/townie), like his email-based blog [posthero.us](https://posthero.us/).

![posthero.us.png](https://imagedelivery.net/iHX6Ovru0O7AjmyT5yZRoA/feeb3071-8506-418b-f004-4cf1056b0100/public)

And actually, Paul’s blog post^ perfectly captures what I’m writing about:

> **I love Val.town for building little experiments and getting them hosted quickly. The fact that you can instantly have a URL to run code is incredible.**

Listing off neat vals users have made starts to sound like that [scene in Elf](https://www.youtube.com/watch?v=cTvpclcBpvs) where Michael reads aloud Santa’s book: Sam Rose built his own personal ping; Guy Dupont tracks laundry machines in his NYC apartment; Dan Abramov prototypes AT Protocol types; Seep starts their Subaru programmatically.

This blog itself [is a val](https://www.val.town/x/valdottown/blog), and so was a [previous version](https://www.val.town/x/valdottown/Townie) of our resident AI agent, Townie. A couple years ago Max [rebuilt Val Town *in Val Town*](https://blog.val.town/val-town-town), and last year Steve used a Wordle-like val to [propose marriage](https://stevekrouse.com/proposal).

## Constraints

Of course, you can’t have it all.

Unlike Quick, Val Town *does* have cron jobs and custom backends but *doesn’t* have websockets. And while Quick sits securely within the walls of Shopify, Val Town apps are on the scary public internet. There is the aforementioned OAuth middleware from our standard library, and Pro and Business users can keep their code private, but Val Town is public by default. We’re also working toward SOC2, which we know is table stakes for many companies.

If any constraints are too high friction or deal breaking for you, [we’d like to hear that feedback](mailto:hello@val.town). But overall, four years in, we’re still excited about Val Town—both what our users have already made, and what we think is a product that can spread the joy of programming to millions more.

\*\*\*

*Credit and thanks to Alex Pilon for writing that great [blog post about Quick](https://shopify.engineering/quick). We liked it so much that we roughly modeled this one after it.*

[Edit on val.town](https://blog.val.town/source)

**We're hiring!**

Are you an infra engineer who cares about the joy of programming?

[View position →](https://www.val.town/careers)