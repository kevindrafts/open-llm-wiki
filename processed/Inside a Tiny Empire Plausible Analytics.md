---
title: "Inside a Tiny Empire: Plausible Analytics"
source: "https://tinyempires.substack.com/p/inside-a-tiny-empire-plausible-analytics"
author:
  - "[[Joshua Tiernan]]"
published: 2026-06-20
created: 2026-06-23
description: "How two founders turned Google’s worst product decision into a $3M ARR business"
tags:
  - "clippings"
---
![](https://substackcdn.com/image/fetch/$s_!mw5-!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc100ba6c-014e-46e2-bffd-f8bffeac2141_1536x1024.png)

Two weeks ago we looked at Exploding Topics, a business that found a gap in data timing and monetized it.

This week we’re looking at Plausible Aanaytics.

When Google made Analytics worse, two people built a business around the frustration it created.

[Plausible](https://plausible.io/) was fully bootstrapped and publicly reported revenue of $3.1M ARR by late 2024. The product is a single-page dashboard that tells you where your visitors came from, which pages they read, and which campaigns worked.

---

## The gap they found

Google Analytics was the obvious choice for anyone running a website. It was free, it was functional, and it was good enough. Then a few things happened in quick succession.

GDPR arrived in 2018 and turned cookie consent into a legal and UX headache. Google released GA4 in 2020, a near-complete rebuild that confused almost everyone who’d used the previous version. A growing number of website owners, bloggers, small SaaS founders, and agencies started realizing they were using an enterprise tool designed for large e-commerce teams when all they actually needed to know was: where did my visitors come from, and did they read what I wrote?

Uku Täht and Marko Šarić launched Plausible in 2018 around that observation: most websites don’t need Google Analytics. They need three or four answers, delivered clearly, without requiring a data analyst to interpret them.

What they were actually selling wasn’t a new capability, it was relief from an existing frustration. The emotional pitch was essentially: you’re tired of GA4 and so are we.

The wedge was the combination of simplicity, privacy, and independence from Google. Copying any one of them without the others doesn’t produce the same product, which made the positioning hard to replicate without fully committing to all three.

---

## What the product actually is

The Plausible dashboard fits on a single page: pageviews, unique visitors, bounce rate, top sources, top pages, countries, devices. Filtering was easy and it make drilling down into the key data insights 10x less confusing than Google Analytics

The product is open source under the AGPL licence, which means anyone can inspect the code, verify the privacy claims, and self-host if they want to. Most users don’t self-host. They pay for the hosted version because they want updates, uptime, and support without managing a server.

The open source version serves as proof that the paid product does what it claims, rather than competing with it.

That distinction matters more for Plausible than it would for most businesses. Their core marketing claim is that they don’t collect personal data, don’t use cookies, and don’t track visitors across sites. Any company can make that claim. Publishing the source code means anyone can verify it.

---

## The revenue model

Pricing is based on monthly pageviews rather than seats or features, with plans running from around $9/month for low-traffic sites up to several hundred for high-volume ones. The entire feature set is available on every plan.

Most SaaS products use features to justify higher tiers. Plausible prices by infrastructure cost instead. Their customer base has widely varying traffic but relatively consistent needs. A solo blogger and a small e-commerce site both need the same information. Charging them different amounts based on a capability gate would create friction and resentment. Charging based on pageviews, the actual cost of serving them, produces less churn and a cleaner relationship with the product.

The founders have been transparent that [reaching $1M ARR took until 2022](https://plausible.io/blog/open-source-saas), four years after launching. One profile noted it took 324 days to reach $400 MRR. Revenue compounded rather than spiked, and by 2024 the business was at $3.1M ARR with two founders and a small remote team, still bootstrapped. With software margins and a tiny team, most additional revenue falls heavily to the bottom line.

---

## How they grew it

The founders have stated repeatedly that they never ran paid advertising.

The channels that built the business were developer communities, SEO, and transparency.

Hacker News and GitHub were the early distribution. Uku posted Plausible to Hacker News in the early days and the developer community responded. The [GitHub repository](https://github.com/plausible/analytics) accumulated stars, which brought more developers, which brought more word of mouth in the communities where their customers spent time.

The SEO strategy targeted people actively searching for Google Analytics alternatives: privacy-friendly analytics, GDPR-compliant tracking, cookie-free analytics. Someone searching those terms has already decided to switch. They’re looking for a product to switch to. Plausible’s content met them at that point and converted well.

Harder to quantify but probably the most durable channel was transparency. The founders wrote publicly about revenue milestones, growth decisions, and the reasoning behind product choices. That openness built a community of people who rooted for the business and told others about it. In a category where trust is the primary purchase driver, an audience that believes in what you’re building is a distribution advantage you can’t buy.

---

## Why the business is structurally strong

Analytics is infrastructure. Once a business installs Plausible and starts collecting historical data, switching costs rise steadily. The longer you use it, the more disruptive it becomes to move that history to a competitor. Retention builds passively, without loyalty programmes or lock-in tactics.

The subscription-only model means no advertisers to serve, no data to sell, no investor expectations pushing toward growth at any cost. Customer interests and business interests point in the same direction, which is rarer than it sounds.

The moat people underestimate is brand and content. Plausible has spent years ranking for “Google Analytics alternative” and related searches. They own that conversation in a way that takes years to build and can’t be bought. New entrants with cleaner code or lower prices still have to earn that trust from scratch.

Part of what made this possible was timing. Plausible launched at a specific moment when GDPR had made privacy commercially valuable, ad blockers were mainstream, and trust in large tech platforms was declining. The same product in 2013 would have found almost no market.

---

## Use the same strategy to get to $3k/month

When a market leader optimizes for power users, they often abandon the majority. This is the pattern to look out for. Find where complexity has outgrown the needs of a specific customer type. Strip it back, price it clearly, publish your reasoning openly, and let the content do acquisition work by targeting people already searching for an alternative.

An accountant who builds a straightforward monthly reporting package for small businesses, without the complexity of enterprise accounting software, is applying the same logic. A consultant who offers one clear deliverable rather than a sprawling retainer is doing the same thing.

At $3k/month, that’s 30 customers at $99/month for a stripped-down version of something they currently over-pay for and under-use. The acquisition cost is low when you’re writing for people already searching for something simpler.

---

**The Playbook**

- **Problem** GA4 became too complex for most users
- **Customer** Bloggers, SaaS founders, small agencies
- **Solution** Simple, privacy-first analytics
- **Distribution** SEO and developer communities
- **Monetization** Usage-based SaaS, priced by pageviews
- **Moat** Trust, open source credibility, years of content
- **Lesson** When a market leader abandons the majority, a simpler product can win

---

**Three things to take away**

1. Open source as a trust mechanism rather than a business model. Publishing your code is a credibility claim your competitors can’t match with marketing spend.
2. Pricing by infrastructure cost rather than features reduces churn from customers who feel they’re paying for things they don’t use.
3. Plausible took four years to reach $1M ARR and never took outside money. By year six they were at $3M.

---

*Is there a business you’d like to see pulled apart in a future issue? Hit reply.*

---

*Inside a Tiny Empire profiles real small businesses to show how they actually work. If you run a business you’d be willing to have featured, or know one worth looking at, reply or comment to let us know.*

---

==If you enjoyed this newsletter, you may be interested in joining== [==No Code Founders==](https://www.nocodefounders.com/?utm_source=tinyempires&utm_medium=referral)==, our sister community of 38k+ founders and operators building businesses without code. It’s free →== [==Learn more==](https://www.nocodefounders.com/?utm_source=tinyempires&utm_medium=referral)

---

**SPONSOR THIS NEWSLETTER** [Learn more](https://www.nocodefounders.com/sponsor)

Want to get in front of 38k+ other founders and makers building business faster using no-code and AI tools.