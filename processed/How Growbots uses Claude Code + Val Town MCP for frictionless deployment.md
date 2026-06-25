---
title: "How Growbots uses Claude Code + Val Town MCP for frictionless deployment"
source: "https://blog.val.town/growbots"
author:
  - "[[Pete Millspaugh]]"
published: 2026-05-27:00:00.000Z
created: 2026-06-10
description: "If Claude Code is Amazon, Val Town is same-day shipping"
tags:
  - "clippings"
---
If Claude Code is Amazon, Val Town is same-day shipping. [Growbots](https://www.growbots.com/), a lead generation agency for SMBs, creates tools and apps with Claude Code and instantly deploys to Val Town using the [Val Town MCP server](https://docs.val.town/guides/prompting/mcp/).

## Who/what: Growbots helps SMBs with outbound sales

[Growbots](https://www.growbots.com/) is a lead generation agency for small- and medium-sized businesses. They’ve served over 3,000 customers since their founding just over a decade ago, helping customers generate over $500 million in total revenue. They save businesses time on customer prospecting and outreach, and Val Town saves *them* time building and deploying tools to run their business.

We talked to Greg Pietruszynski, Growbots’ co-founder and CRO, and Jakub Kalbarczyk, GTM Engineer, about how they’re using Val Town with Claude Code.

## Problem: codegen is frictionless, deployment is not

There’s a lot of talk lately about how code is cheap, but working software isn’t. Part of that is the bridge between codegen and deployment. Greg put it eloquently:

> 99% of non-technical users have no f\*\*\*ing idea how to deploy apps, and it’s even f\*\*\*ing hard to register on GitHub now because you need to do this captcha verification spending 10 minutes listening to strange animal noises.

## Solution: deploy Claude’s code with Val Town’s MCP

Val Town solved that deployment gotcha for Greg, who doesn’t write code and isn’t used to dealing with engineering infrastructure.

> As I started digging more into Claude Code, I obviously ran into deployment issues. Instead of fighting with GitHub, I now have a simple solution: I just talk to Val Town using MCP. That’s the most reliable part of my process.

### Sales vals

For example, Greg compressed his sales knowledge and experience into a val that ingests meeting transcripts, updates their HubSpot CRM, and crafts a suggested follow-up for his sales team.

> I built a sales coach into it that suggests a follow-up. We could even send those follow-ups directly from Slack with our Slackbot val. We’re minimizing all of that manual CRM work.

![growbots-slackbot.png](https://imagedelivery.net/iHX6Ovru0O7AjmyT5yZRoA/a98ee152-b0b2-4ce7-1083-24e00f99ff00/public)

The Growbots val sending action items after a sales meeting

In their Slack workspace, the Growbots team is joined by bots hosted on Val Town. The sales team can type `/proposal exampleclient.com` to run a val that generates a first draft of the outbound playbook for a sales pipeline, for example.

### Scraper vals

Jakub on the GTM engineering team talked about using Val Town with [Clay](https://www.clay.com/) (see also: [how we built an API for Clay](https://blog.val.town/clay)). Jakub told us about switching to Val Town from another vendor to host their Cloudflare crawler, saving an order of magnitude in cost.

> We use our Cloudflare scraper val for everything. It’s an easily accessible endpoint that runs Cloudflare crawlers on Val Town, and it’s something like 20x cheaper than our previous vendor. We import that val into other vals, or use it with tools like Clay. Actually, Val Town was the first tool recommended to me by Claude when I was looking for how to host “Claygent” workflows.

## Takeaway: Val Town lets you forget about deployment

There’s that old business advice to spend time on your core competency and outsource the rest. For Greg, that means letting Claude combobulate some code and deploying right to Val Town.

> My goal is to test to what extent I can automate the whole company with Val Town so that I can focus on building. As a CRO, the biggest advantage of Val Town for me is that I’ve never even seen it. I do everything in Claude Code, and then it just runs on Val Town.

For Jakub, he also likes the instant deployment from Claude Code, but also having the full flexibility of code.

> We dropped every single no-code automation builder we were using before. I just try to do everything with Val Town and Claude Code now. Those workflow tools are more complicated than Val Town—you have to fight with the platform, not the code itself. And it’s cheaper with Val Town.

So again, if Claude Code is Amazon, then GitHub + deploying somewhere with a build step would be like USPS. Sometimes it’s good to go with USPS—the Val Town application itself is deployed to Render—but often you want the convenience of same-day shipping (in our case, 100ms deployment).

Metaphors aside, it’s quite productive to have an immediate feedback loop where the code you or Claude write is instantly live at a URL, or in Slack, or wherever. [Sign up](https://www.val.town/auth/signup) for Val Town, or [book a demo](https://calendar.app.google/uXdbgkdtz9SLzR25A) with our founder Steve to learn how your team can enjoy frictionless deployment.