---
title: "Public prediction pages are the SEO moat I wish I'd built sooner"
source: "https://www.indiehackers.com/post/public-prediction-pages-are-the-seo-moat-i-wish-id-built-sooner-0f8c7cbd41"
author:
  - "[[Jakub]]"
published: 2026-06-24
created: 2026-06-27
description: "We spent six months writing blog posts for our products at Inithouse. Keyword research, outlines, editing, publishing. The math was simple: one post equ..."
tags:
  - "clippings"
---
[2](https://www.indiehackers.com/sign-up)

[

Likes

](https://www.indiehackers.com/sign-up)

We spent six months writing blog posts for our products at [Inithouse](https://inithouse.com/). Keyword research, outlines, editing, publishing. The math was simple: one post equals one indexable page. To get 100 pages in Google, write 100 posts.

Then we built [Watching Agents](https://watchingagents.com/) and discovered a pattern that made content marketing feel like digging a hole with a spoon.

## The blog math doesn't work for small teams

Here's the problem with "content as growth" when you're a small team running multiple products. Every blog post costs time. Research, writing, optimization, internal linking. A good post takes 3-4 hours. At that rate, getting to 500 indexable pages takes about 250 working days of pure writing.

We don't have 250 days. We have 14 products competing for attention and a team of three.

The question became: what if the product itself generated the pages?

## How user content becomes an SEO asset

Watching Agents lets people create public predictions: "Will OpenAI release GPT-5 before September 2026?" or "Will Bitcoin hit $150K by end of year?" Each prediction gets its own URL, its own FAQ schema, its own internal links to related questions.

The key insight: every public prediction is a page that Google can index. And unlike blog posts, these pages scale with the userbase, not with our writing capacity.

In the first 30 days after launching public predictions, we went from about 40 indexed pages to over 200. Not because we wrote 160 blog posts. Because users created questions that real people search for.

The growth curve looks different from content marketing. Blog growth is linear: you write, you publish, the page exists. User content growth is compounding: each user creates pages, those pages attract search visitors, some visitors create their own predictions, those become new pages.

## When this pattern works (and when it doesn't)

Not every user-generated content is an SEO asset. The framework we use:

**Index it** when the content answers a question a stranger would search for. "Will quantum computing break RSA encryption by 2030?" is a real search query. Someone landing on that page gets value: aggregated predictions, source links, tracking data. They don't need to know who created the prediction.

**Don't index it** when the content is only meaningful to the creator. A photo of someone's lunch, a private journal entry, a todo list. No search intent, no value for a stranger.

The test: would a search visitor who has never heard of your product find this page useful? If yes, index it and optimize it. If no, keep it private or noindex.

## Cross-portfolio proof: the same pattern elsewhere

We noticed this pattern works across multiple products:

[Pet Imagination](https://petimagination.com/) generates unique pet portrait galleries. Each gallery page has the pet's name, breed, art style: a long-tail combination that's indexable and useful for "AI pet portrait \[breed\] \[style\]" searches.

[Tarotas](https://tarotas.com/) creates reading pages across multiple languages and spreads. Each combination (Celtic Cross reading in Spanish, Three Card reading in Czech) is a unique page with real content. The locale multiplier alone creates hundreds of indexable variations.

The shared principle: let the product's core action generate the SEO surface area. Don't bolt SEO on as a marketing layer. Build it into the product architecture.

## The numbers after 90 days

Here's where we are with Watching Agents after three months of public predictions:

Pages indexed went from 40 to 350+. We wrote zero blog posts in that period. Every new page came from user activity.

Organic impressions grew from roughly 200/day to 1,200/day. The growth isn't uniform: prediction pages around trending topics (AI regulation, crypto milestones, election outcomes) spike when the topic is hot, then settle into steady long-tail traffic.

The conversion path: search visitor lands on a prediction page, sees the question and aggregated data, creates their own prediction (free), which generates another indexable page. The flywheel.

## What we'd do differently

Three things we got wrong:

**We launched with all predictions private.** The "public by default" toggle should have been there from day one. We lost two months of potential page generation because users had to opt into visibility.

**We didn't add FAQ schema immediately.** Adding structured data to prediction pages increased rich snippet appearances significantly. Should have been in the first deploy, not a follow-up ticket.

**We treated prediction titles as free text too long.** Unstructured titles like "what about AI?" don't match search queries. Adding suggested question formats ("Will \[X\] happen by \[date\]?") improved the SEO value of user-created pages because the titles matched how people actually search.

## The framework

If you're building a product and struggling with distribution, ask yourself:

1. Does my product's core action create content?
2. Is that content useful to someone who isn't my user?
3. Can I give each piece of content a unique URL?

If all three are yes, you might be sitting on an SEO moat. Not the kind you build by hiring writers. The kind that builds itself every time someone uses your product.

We're still early with this at Inithouse. But after watching the indexed page count climb while we focused on product work instead of blog calendars, the thesis feels solid: the best SEO strategy for an indie product isn't content marketing. It's building a product where usage equals distribution.

---

*Jakub, builder @ [Inithouse](https://inithouse.com/)*