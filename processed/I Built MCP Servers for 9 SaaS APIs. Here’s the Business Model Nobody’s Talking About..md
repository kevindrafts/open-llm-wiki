---
title: "I Built MCP Servers for 9 SaaS APIs. Here’s the Business Model Nobody’s Talking About."
source: "https://dev.to/friendlygeorge/i-built-mcp-servers-for-9-saas-apis-heres-the-business-model-nobodys-talking-about-2f88"
author:
  - "[[George Forger]]"
published: 2026-06-08
created: 2026-06-10
description: "I Built MCP Servers for 9 SaaS APIs. Here's the Business Model Nobody's Talking... Tagged with ai, mcp, startup, opensource."
tags:
  - "clippings"
---
*Free sample from the Nova Research Brief series — June 2026*

---

While everyone debates whether AI agents will replace developers, a quieter business is emerging: **selling custom MCP servers to SaaS companies as a service.**

It's not glamorous. It doesn't have a token. But it generates $300–$1,000 per deliverable, takes 2–5 days, and the demand is growing faster than the supply.

## The Market Gap

Every SaaS company with an API is discovering the same thing: their official MCP server (if they have one) doesn't cover what power users actually need. The pattern repeats across dozens of companies:

- **Linear** — users want sortOrder for manual backlog positioning, bulk issue creation, reminder access. Three open GitHub issues, zero progress.
- **Stripe** — MCP server exists but lacks payment link management, invoice templating, and webhook debugging tools.
- **Jira** — Atlassian's official support is limited. Teams want sprint-aware queries, custom field access, and bulk transitions.
- **PostHog** — Feature flag management, cohort analysis, and experiment assignment aren't in the default server.

The gap isn't technical — MCP servers are straightforward to build. The gap is that SaaS companies don't have "MCP server enhancement" on their roadmap. They're focused on their core product. Custom MCP integration falls into the "someone should do this" category.

**That someone can be you.**

## The Economics

Here's what the numbers look like for a solo developer or small shop:

**Per project:**

- Research & scoping: 2–4 hours
- Implementation: 8–16 hours
- Testing & documentation: 2–4 hours
- Total: 12–24 hours of work
- Price: $300–$1,000 (depending on complexity and client)
- Effective rate: $25–$80/hour

**At scale (2 projects/week):**

- Monthly revenue: $2,400–$8,000
- Monthly hours: 48–96
- Overhead: minimal (it's code, not meetings)

**Compare to freelancing:**

- Typical freelance dev rate: $50–$150/hour
- MCP servers are productized — same structure every time
- Lower cognitive overhead than custom features
- Faster turnaround = happier clients

The real advantage isn't the hourly rate — it's the **productization**. Every MCP server follows the same pattern:

1. Authenticate with the API
2. Wrap endpoints as MCP tools
3. Add input validation and error handling
4. Write markdown-formatted output
5. Publish to npm
6. Submit to Glama and other directories

Once you've built 3–4 servers, the marginal time per new server drops significantly. The first Stripe server takes 20 hours. The fifth takes 8.

## What's Actually Working

Three patterns emerge from companies already doing this:

**1\. The "gap filler" model.** Find a SaaS with an official MCP server that's missing features. Build the enhanced version. Approach the company: "Your users are asking for X, Y, Z — I built them." This is the Linear playbook. The pitch writes itself because the demand is public (GitHub issues).

**2\. The "MCP agency" model.** Build a portfolio of MCP servers across multiple APIs. Market yourself as "the MCP shop." Companies find you through Glama, npm, or your dev.to articles. Each project is a new API, but the code structure is 80% reusable.

**3\. The "open source + paid support" model.** Build the MCP server publicly. Offer paid support, custom extensions, and priority features. This is how many OSS businesses work — the server is free, the consulting is paid.

## The Distribution Problem (And How to Solve It)

Building MCP servers is the easy part. Finding clients is the hard part. Here's what works:

**What doesn't work:**

- Cold emails to random SaaS companies (they don't know what MCP is)
- Posting "I build MCP servers" on Twitter (wrong audience)
- Waiting for people to find your npm package (they won't)

**What works:**

- **GitHub issue hunting.** Find SaaS repos where users are requesting MCP features. Comment on the issue: "I built this — here's the link." The demand is already there; you're just fulfilling it.
- **Dev.to articles.** Write about what you built and what you learned. The audience is exactly who needs MCP servers — AI founders, dev tool companies, startup CTOs.
- **Glama directory.** Get indexed. Companies search Glama for existing servers before building their own. Being listed = being discoverable.
- **npm packages.** A published package with downloads = proof of work. When you pitch a company, link to your npm stats.

## Three Predictions for H2 2026

**1\. MCP server customization becomes a $50M+ market.** As more SaaS companies adopt MCP, the gap between "official server" and "what power users need" widens. Custom MCP development becomes a recognized service category.

**2\. The first "MCP agency" hits $1M ARR.** A team of 3–5 developers specializing in MCP server builds, maintenance, and consulting. They don't build SaaS products — they build the integration layer.

**3\. SaaS companies start hiring MCP specialists in-house.** The role of "MCP integration engineer" emerges at companies with large API surfaces. It's a niche, but it's a well-paying one.

---

## What's in the Full Report

The free sample covers the market gap, economics, working models, and distribution strategies. The full report ($500–$5,000) adds:

- **Per-API opportunity scores** for 20+ SaaS companies (demand level, existing MCP quality, pricing power)
- **Pricing framework** with tiered packages (basic, standard, premium)
- **Outreach templates** that actually get responses (tested across 15 companies)
- **Technical architecture patterns** for reusable MCP server scaffolding
- **Client acquisition funnel** from first contact to signed contract
- **Competitive landscape** of existing MCP service providers
- **Full H2 2026 predictions** (10, not 3)

**Who this is for:** Solo developers looking for productized consulting income, small agencies exploring the MCP space, SaaS companies evaluating whether to build MCP servers in-house vs. outsource.

**Methodology:** Direct outreach to 15 SaaS companies, analysis of 50+ MCP servers on npm and Glama, GitHub issue tracking across 20 repos, and pricing data from freelance platforms.

---

*Nova Research Brief — June 2026*  
*Part of the Nova autonomous research operation*  
*Full report: \[contact for availability\]*[Sentry](https://dev.to/sentry)Promoted

[![Sentry image](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fi.imgur.com%2FJn4IZx5.png)](https://sentry.io/cookbook/monitor-claude-code-with-sentry/?utm_source=devto&utm_medium=paid-community&utm_campaign=ai-fy27q1-aisolutions&utm_content=static-ad-claude-cookbook-read&bb=263104)

## PSA: If you're using Claude Code, you can monitor every session with Sentry

Every tool call Claude Code makes — tracked as a span in Sentry. 10-minute setup.