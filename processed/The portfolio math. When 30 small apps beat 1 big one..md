---
title: "The portfolio math. When 30 small apps beat 1 big one."
source: "https://dev.to/thegdsks/the-portfolio-math-when-30-small-apps-beat-1-big-one-41ai"
author:
  - "[[GDS K S]]"
published: 2026-05-18
created: 2026-05-19
description: "The portfolio math. When 30 small apps beat 1 big one.   For a decade the indie hacker... Tagged with webdev, indiehackers, startup, productivity."
tags:
  - "clippings"
---
For a decade the indie hacker playbook stayed the same. Pick one product. Find a niche. Focus. Iterate. Sell. That advice fit 2014 perfectly. It started quietly going wrong in 2022, and by 2026 it is the wrong default for most solo operators, including a meaningful chunk of the ones the courses are still selling it to.

Eight solo founders crossed twenty thousand dollars a month in revenue between November 2025 and April 2026. The shape of how they got there is not the shape the courses describe. The shape is a portfolio. One person, many products, lots of small bets, no precious single hill to die on.

This article is the economic case for the portfolio shape, the math that determines whether it fits your situation, the kill rule that makes it work, and a working calculator you can paste into a spreadsheet this afternoon. By the end you will know whether you should be running one product or seven, and you will know exactly what number to track to decide if a given product belongs in the portfolio.

## TL;DR

| The choice | When it wins |
| --- | --- |
| Single product, all-in | High build cost, defensible moat, large addressable market, slow feedback cycles |
| Portfolio of 5 to 10 | Medium build cost, fragmented attention, fast feedback cycles, you have any distribution |
| Portfolio of 20-plus | Very low build cost, niche-of-niches, owned channel, willing to kill aggressively |

The math behind that table is below.

## 1\. The case for the portfolio in three numbers

The portfolio shape is not a fashion. It is a response to three measurable changes since 2014.

```
Number 1: build cost per product, in hours
  2014:  ~400 hours for a working SaaS with payments
  2020:  ~120 hours, same scope
  2026:   ~25 hours, same scope, including auth, payments, and a usable UI

Number 2: cost per useful signal, in product-attempts
  2014:  one attempt, run for 6 to 12 months, then maybe one more
  2026:  ten to thirty attempts, each run for 30 to 90 days

Number 3: average successful attempt rate, indie SaaS
  Published founder reports cluster around 1 in 8 to 1 in 15
  Conservative call: 1 in 10
```

Combine those three. In 2014 you got one shot per year. In 2026 you can take twenty shots per year. If one in ten shots becomes a paying product, the single-shot strategy gets you to a paying product roughly every decade. The twenty-shot strategy gets you to two paying products per year, on average.

This is the entire economic argument for the portfolio. It is not that portfolios are inherently better. It is that the cost of an attempt fell by an order of magnitude, and the strategy that matches the new cost is to take more attempts.

## 2\. The actual revenue distribution inside a portfolio

The first thing to understand is that a portfolio does not produce uniform revenue. It produces a long tail.

Max, one of the eight founders from the writeup, makes $22K MRR across thirty apps. Average revenue per app: $733. That number is misleading. The real distribution probably looks like this:

```
App rank | Estimated share of MRR | Estimated MRR
─────────┼───────────────────────┼──────────────
App 1    |  35 to 50%            |  $7,700 to $11,000
App 2    |  15 to 20%            |  $3,300 to $4,400
App 3    |  10 to 15%            |  $2,200 to $3,300
App 4-6  |  5 to 8% each         |  $1,100 to $1,760 each
App 7-15 |  1 to 3% each         |  $220 to $660 each
App 16+  |  near zero            |  rounding error
```

The distribution above is a power law, which is the same shape every portfolio of consumer or SMB SaaS products converges to. Pieter Levels has been transparent about this for years across his 12-plus product portfolio. A handful of products carry the revenue. The rest exist to feed the funnel and explore new niches.

If you find this depressing, the portfolio shape is not for you. The right reading is liberating: you do not need every product to win. You need to ship enough that one or two find the power law top.

## 3\. The kill rule is the load-bearing piece

The thing that separates a working portfolio from a graveyard of half-finished SaaS projects is the kill rule. Without it the portfolio becomes a tax. Each product needs maintenance. Each product accumulates support tickets, dependency upgrades, expired domains, broken Stripe webhooks. A portfolio of unkilled losers will eat all your time.

The kill rule has three components.

```
Component 1: time horizon
  Pick a number, write it down, do not negotiate with yourself later.
  Reasonable defaults: 30 days for SaaS, 60 days for content products,
                       90 days for marketplaces.

Component 2: signal threshold
  Define the minimum signal that justifies keeping the product alive.
  Reasonable defaults: 3 paying customers, OR $50 MRR,
                       OR 100 active users with stickiness over 20%

Component 3: kill action
  Define exactly what "kill" means before you have to do it.
  Standard practice: archive the repo, sunset the domain,
                     refund any remaining subscribers, write the postmortem.
```

A working kill rule reads like a contract: "If this product has fewer than 3 paying customers 30 days after launch, I archive the repo, redirect the domain to my portfolio page, and write a one-page postmortem before starting the next product."

The contract part matters. You will not want to kill the product. You will have spent 25 hours on it. You will have a tiny number of free users who like it. You will tell yourself that with one more feature it will take off. The kill rule is the version of you that wrote the contract overruling the version of you that is sentimental about the work.

The portfolio founders who succeed are not the ones with the best products. They are the ones with the strictest kill rules.

## 4\. A working calculator

You can decide whether the portfolio shape fits your situation with this calculator. Paste it into a spreadsheet, fill in the inputs, read the recommendation.

```
INPUTS

  H = hours to ship a working version (including auth, payments, UI)
  S = your success rate per attempt (default 0.10 if unknown)
  D = distribution multiplier (1.0 if launching cold, 3.0 if you have any
      owned channel, 8.0 if you have a list of 5K-plus engaged followers)
  W = available hours per week
  K = your sentimental kill tax (in extra hours per failed product)

CALCULATIONS

  Attempts per year possible:
    A = (W * 50) / (H + K)

  Expected successful products per year:
    P = A * S * D

  Cost per successful product:
    C = (H + K) / (S * D)

DECISION RULES

  If P < 1, you cannot run a portfolio. Pick a single product.
  If 1 <= P < 3, run a small portfolio of 5 products. Be strict.
  If P >= 3, run an aggressive portfolio. Kill faster.
```

Example for a founder with 20 hours a week, 25-hour builds, no distribution, no kill tax:

```
A = (20 * 50) / (25 + 0) = 40 attempts per year possible
P = 40 * 0.10 * 1.0 = 4 expected successes per year
C = 25 / (0.10 * 1.0) = 250 hours per successful product
```

That founder should run an aggressive portfolio. Same founder, same hours, but with a 10K-follower X account that they have nurtured for two years:

```
A = (20 * 50) / 25 = 40 attempts per year
P = 40 * 0.10 * 8.0 = 32 expected successes per year (clip to feasibility)
```

The math goes silly fast when distribution is the multiplier, because distribution is the multiplier. The cap is realistically how many products one person can actually maintain at once, not how many will succeed.

## 5\. When the single product still wins

The portfolio shape is not universal. Three cases where focusing on a single product is the right call, regardless of the math above:

```
Case 1: high build cost, defensible moat
  If your product needs 600 hours of engineering before the first
  customer can even use it, the attempt cost is too high to run
  a portfolio. Examples: developer infrastructure, a database, a
  language runtime, deep ML, hardware. Pick one. Commit.

Case 2: large total addressable market, slow feedback cycle
  If the buyer has a 6-month evaluation cycle (enterprise SaaS,
  regulated industries, government), the portfolio cannot give you
  enough signal per year. Pick one. Run a long sales cycle.

Case 3: brand-building motion
  If your goal is to become the founder of the thing (the next
  Stripe, the next Linear, the next Figma), the portfolio shape
  fights you. Investors, press, and senior hires want one story.
  Pick one. Tell the story.
```

If you are in any of these three cases, run the single product strategy and ignore the portfolio noise. If you are not, the math says you are leaving signal on the table by limiting yourself to one product.

## 6\. The operating cadence that actually works

Founders who run successful portfolios converge on a similar weekly cadence:

```
Mondays:  triage the portfolio. Which products had movement? Which need
          a support reply? What is the metric I am tracking per product
          this week?

Tuesdays-Thursdays: build. Either ship a new product, ship a meaningful
          improvement to a top-3 revenue product, or kill a failing
          product per the contract.

Fridays:  distribution. Post about whatever shipped this week. Engage
          in the channel you own. Reply to comments. No new code.

Saturdays: rest.

Sundays:  one hour of metrics review. Update the portfolio dashboard.
          Decide what next week's primary focus is.
```

The discipline is in the constraint. You do not work on a product unless it appears in Monday's triage. You do not start a new product mid-week. You do not skip Friday distribution because you are "behind on shipping." The cadence is the moat.

## 7\. The honest take

The portfolio shape is not a moral upgrade over the single product shape. It is a different shape of bet, with its own losing scenarios. The biggest one is brand. A founder with thirty products will never become the founder of one thing. The LinkedIn headline reads "Maker of stuff." The Twitter bio reads as a list. The portfolio founder will not become the next Stripe.

That tradeoff suits a goal of freedom and revenue. The tradeoff fails a goal of building a category-defining company. Pick the goal honestly. The portfolio gets you out of the day job. The single product, if it works, gets you to the IPO.

The current decade rewards the portfolio shape more than the previous one did, because the cost of an attempt fell by an order of magnitude. The strategy that matches the new cost is to take more attempts. The kill rule turns those attempts into a long-term system instead of a graveyard.

Run the calculator. Be honest about your distribution. Pick your shape. Set the kill rule. Then start.

Question for the comments: how many products do you currently maintain, and what is your actual kill rule (not the one you wish you had)?

---

**GDS K S** · [thegdsks.com](https://thegdsks.com/) · follow on X [@thegdsks](https://x.com/thegdsks)

*The cheapest year of your life is the one where you killed three bad ideas instead of one good one.*

DEV Community

[![Google AI Education track image](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fu09y9fffqrb2one15j3g.png)](https://dev.to/deved/build-apps-with-google-ai-studio?bb=238784)

## Work through these 3 parts to earn the exclusive Google AI Studio Builder badge!

This track will guide you through Google AI Studio's new "Build apps with Gemini" feature, where you can turn a simple text prompt into a fully functional, deployed web application in minutes.