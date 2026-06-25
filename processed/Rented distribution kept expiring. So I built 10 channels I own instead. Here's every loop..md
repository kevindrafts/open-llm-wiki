---
title: "Rented distribution kept expiring. So I built 10 channels I own instead. Here's every loop."
source: "https://www.indiehackers.com/post/rented-distribution-kept-expiring-so-i-built-10-channels-i-own-instead-heres-every-loop-HZMgyAVyVJ4GONyqTMUQ"
author:
  - "[[Max]]"
published: 2026-05-13
created: 2026-05-15
description: "Most distribution advice for solo founders is about channels: which one to pick, how to work it, how to scale it. After six weeks of trying the channels..."
tags:
  - "clippings"
---
Most distribution advice for solo founders is about channels: which one to pick, how to work it, how to scale it. After six weeks of trying the channels that fit my budget and personality, I realized the channel was not the problem.

**Every channel I tried was rented.**

Cold DMs were rented attention. The hour I spent writing them was the deposit. The moment I stopped, the attention stopped. Tweets rented reach until the algorithm shifted, which it always does. Quora answers rented inbound until the question slipped off page one. A halfway-decent Product Hunt launch rented a day of traffic that flattened by the next week. I was paying with effort instead of dollars, but the contract was the same: stop paying, traffic stops.

The IH community has been calling email lists "owned" channels for years. I had nodded at that framing without applying it at the feature level. Once I did, the question changed. Instead of "what channel should I work this week," it became "what feature can I build into the product that pays me back in six months without my hand on it?"

I rebuilt the growth side of Flowly ([flowly.run](http://flowly.run/), a task manager with timers and analytics for freelancers) around that question. In four days I shipped 10 features. None of them is revolutionary. Every one of them is mine to keep.

## The test

Here is the test I run before I build any growth feature now:

> **"Will this still produce in 30 days if I stop touching it?"**

If yes, it is a loop. You own it. If no, it is a campaign. You are renting.

This test is unforgiving. Most things people call "distribution work" fail it. Cold outbound fails. Twitter posts fail. Even a beautifully run Product Hunt launch fails by week four. Almost nothing that costs you a calendar hour today is still producing value 30 days later.

The 10 features below pass it.

## TL;DR

The 10 loops, ordered by the customer story below. The order I would build them in if starting over is in parentheses.

1. The goodbye that knows your name (build order: #2)
2. The email that meets you where you actually are (build order: #4)
3. The email I almost did not send (build order: #6)
4. The survey that does its own segmentation (build order: #3)
5. The referral I almost cut for being too early (build order: #7)
6. The roadmap that is actually free product research (build order: #8)
7. The 15 templates that pay rent at 3am (build order: #5)
8. The free tools that ask for nothing (build order: #9)
9. The card that does the bragging for you (build order: #10)
10. The boring email worth more than the clever ones (build order: **#1, by a wide margin**)

Total cost: roughly 60 hours across four days. The reason it took four days and not four months: I had no meetings.

> **If you only ship one of these this week, ship #10.** It is the most boring item on this list and the closest thing to free money in this entire post.

---

### 1\. The goodbye that knows your name

When a trial ends, most apps show the same goodbye message to everyone. *"You are about to lose analytics, calendar sync, and unlimited history."* Generic. Forgettable.

I changed it. Now the trial-end modal shows the user their actual numbers from the trial: *"You created 47 tasks. Tracked 23.5 hours across 4 projects. Hit a 9-day streak. That data goes read-only at midnight."*

Same trial. Same product. Same price. Only the goodbye is different.

**Why it works:** loss aversion is documented at roughly 2:1 over gain framing (Kahneman, Tversky). Personalization research puts the CTR lift at 25 to 50% when you replace generic copy with the user's own data. The mechanic is older than software: a person fights harder to keep something they already built than to acquire something new of equal value.

**Who it is actually for:** the freelance designer who signed up two weeks ago, quietly built habits, and forgot how much she had already invested by the time the trial-end modal showed up. The modal reminds her.

**What it taught me:** I shipped the first version without a fallback. A user with very low trial activity saw *"You created 0 tasks. Tracked 0 hours."* I had built loss aversion that worked perfectly against me. The screen told her the trial was a waste. The fix is one line of code; the lesson is bigger: loss aversion needs something to lose. If your version of this feature can hit zero, build the fallback first.

---

### 2\. The email that meets you where you actually are

The trial drip used to send the same Day 3 email to everyone. Same Day 7. Same Day 10. I rewrote it to branch on what the user actually did inside the product.

- Created zero tasks in the first 48 hours? *"Start with one quick task. Takes 30 seconds."*
- Created tasks but never started a timer? *"One click to know where your hours actually go."*
- Timers running but no calendar connected? *"Add 15 minutes. Link Calendar. See your full day."*
- Calendar already connected? An entirely different Day 7. There is no point re-pitching a feature she already uses.

**Why it works (the data):** triggered emails outperform batch sends by roughly 70.5% on open rate and 152% on click-through (MarketingProfs). Braze reports about 5x revenue per email for behavioral versus broadcast. Automated emails are about 2% of email volume and drive about 37% of email sales.

**Why it actually works (the customer part):** the user is told, in plain language, "I see what you did and did not do this week. Here is the next 30-second action specifically for that." Most onboarding emails address a user the company imagines. This one addresses the user who exists.

**What it taught me:** I wildly underestimated how much harder it is to write four good versions of a Day 3 email than to write one polished version. The code change was a switch statement. The copy is the actual work. I am already rewriting two of the four.

---

### 3\. The email I almost did not send

When a paid subscriber cancels, three emails fire over the following weeks.

- **Day 7:** *"We miss you. Here is what shipped since you left."*
- **Day 21:** *"Try Pro free for 30 days, no card."*
- **Day 45:** *"What would have kept you?"*

**Why it works (the data):** Klaviyo data has win-back open rates around 29% on average. Multi-email sequences reactivate around 10% of recipients; optimized sequences hit 14 to 18%. The median ROI on optimized win-back is documented at about 380%, compared to 150 to 200% for paid acquisition. One in ten cancellations coming back is meaningful at every scale.

**What it taught me:** I held this feature off for weeks. Writing the Day 21 email felt presumptuous, as if I was bothering someone who had already left and made it clear. I drafted it three times. I deleted it twice.

Then I read the open-rate benchmarks and realized the embarrassment was mine, not the customer's. Your churned users opted in to hearing from you once when they signed up. One polite *"we miss you"* email is not a violation; it is a courtesy. The customer who left because she switched jobs and stopped freelancing is not insulted by your email. She just deletes it. The customer who left because of a real reason (price, a missing feature, a workflow change) might come back. Either way, you find out.

I almost cost myself a 10% reactivation rate on every future cancellation because I was projecting embarrassment onto people I had never met. Do not do that.

---

### 4\. The survey that does its own segmentation

At Day 30 of paid, every customer gets a one-question email: *"0 to 10, how likely are you to recommend Flowly?"* The email body is 11 score buttons. Each click goes to a different page depending on the score.

- **9 to 10** lands on a pre-filled G2 review page
- **7 to 8** lands on *"What would make it a 10?"*
- **0 to 6** lands on a direct message to me

The clever part is not the email. The clever part is that **the user does the segmentation for me**. I do not have to look at a score in a database and decide what to do; the user has already self-routed by the time the page loads.

**Why it works:** G2 reviews compound forever and cost nothing to acquire from a customer who was already going to give you a 9 anyway. Productivity SaaS with NPS above 40 correlates with strong word-of-mouth. Below zero means you have a churn timer running and do not know it.

**Who it is actually for:** the customer who has been paying for four months, is genuinely happy, and would never sit down at her laptop on a Saturday to write a public review on her own. The email gives her a 30-second path with one click of friction. She would not have done it otherwise. Now she does.

---

### 5\. The referral I almost cut for being too early

Every user gets a unique referral link. When their referee signs up and pays for the first time, the referrer gets +30 days of Pro added to their plan. The referee gets +14 days on top of the standard 14-day trial.

The detail that mattered: the reward fires on the referee's **first paid charge**, not on signup. Without that single condition, every trial signup via a referral link would reward the referrer regardless of whether the referee ever pays. That is the difference between a working incentive and a leaking one.

**Why it works (the data):** referred customers have 16 to 25% higher LTV, churn 20% less, and convert at 3 to 5x the rate of paid leads (GrowSurf 2026 benchmarks). Adding referral as a channel drops blended CAC by 25 to 35%.

**Why it actually works (the human part):** referrals are not really about the reward. The reward is permission. When a freelancer tells another freelancer about a tool, the reward says *"the company endorses this conversation and made it easy for you to do it."* Most people just want to be helpful and slightly compensated. The reward is the *slightly.*

**What it taught me:** I almost cut this feature for being premature. The math says it does very little this month. The counter-argument I talked myself into is that the cost of installing the loop now is the same as installing it at 10x the user base, and the only loop you cannot measure is the one you did not build. The mechanic stays whether or not it produces this quarter. Future-me thanks present-me.

---

### 6\. The roadmap that is actually free product research

I shipped a public roadmap page with three columns: Planned, In Progress, Shipped. Logged-in users can upvote. I seeded it with 8 honest items spanning all three columns, including items that are months out.

**Why it works as a distribution loop:** the page is indexable. Every item title is a small SEO bet on a phrase a specific user is searching for ("Slack integration," "iOS app," "weekly invoice export"). The page itself is also a trust signal: companies that publish what they are building are perceived as more accountable and more permanent.

**Why it actually works (the human part):** people who upvote feel ownership. Ownership correlates with lower churn. They are invested in the version of the product that exists in six months, not just the one they bought today.

**What surprised me:** the upvotes are the most valuable product research I have ever paid nothing for. The feature I expected to win did not. The one that did is going to the top of my queue. I had not appreciated, before shipping this, that a public roadmap is a product-discovery channel disguised as a marketing surface.

**What I am watching:** noise from competitors voting strategically and from loud free users who never upgrade. I am planning to weight votes by account age and plan tier if it gets noisy. Worth thinking about before you ship.

---

### 7\. The 15 templates that pay rent at 3am

I shipped 15 real templates as public, indexable pages at [flowly.run/templates](http://flowly.run/templates). Freelance time tracker. Weekly client review. Onboarding flow. Each is a real workflow, not "Hello world" filler. Each detail page is SEO-targeted with structured data so Google can render it as a rich snippet. A logged-out visitor who clicks "Use this template" gets signed up and the template applied to their workspace in one motion.

**Why it works (the data):** Notion's template gallery ranks for over 60,000 organic keywords in the US and pulls roughly 287,000 monthly organic visitors. #notiontemplate has over 180M views on TikTok. The mechanic does not require Notion's scale to start; it requires presence so that compound interest has a surface to land on.

**The mechanic in one sentence:** each template page is a small SEO bet that sits in a search result at 3am, when I am asleep, and signs up a small percentage of clickers.

**Who it is for:** the freelance designer who Googles *"weekly client review template"* on Sunday night because she has a meeting Monday and does not want to start from scratch. She does not know me. She does not need to. The template solves her actual problem in 30 seconds, and the signup happens as a side effect of solving it.

**What it taught me:** I assumed the bottleneck would be the code. It was not. The bottleneck was sitting down to write 15 templates that are actually useful, not garbage to fill a directory. I ended up using Flowly to draft them, which is either a tight feedback loop or selection bias. I am still figuring out which.

---

### 8\. The free tools that ask for nothing

I shipped three standalone tool pages at [flowly.run](http://flowly.run/), each one fully functional without an account.

- /pomodoro-timer
- /freelance-rate-calculator
- /time-tracker

Each has a soft signup CTA at the bottom. None of them is gated.

**Why it works:** "pomodoro timer" alone is 100,000+ monthly searches. CAC is zero. Tool-to-signup conversion lands in the 3 to 8% range when the tool is genuinely useful and the CTA is not aggressive. Bannerbear, Tally, and many others built their early traffic on free tool pages like these.

**The mechanic in one sentence:** people who type *"pomodoro timer"* into Google are not in the market for a productivity SaaS today; they are in the market for a 25-minute timer. I give them the timer. A small percentage of them think, while the timer is running, *"I should be tracking this more seriously,"* and the CTA catches them at that exact moment.

**What it taught me, in advance:** SEO takes 6 to 12 months. I have not ranked yet. I am building tools my future self will thank me for, not tools that move this month's number. That is an honest tension you need to make peace with before you ship work that will not pay off for a year.

---

### 9\. The card that does the bragging for you

At the end of each week, every user can click "Share this week" and get an image: hours worked, project count, longest streak, *Powered by* [*flowly.run*](http://flowly.run/)*.* The weekly digest email automatically appends the share link, so users who never visit the analytics page see the loop anyway.

**Why it works:** Spotify Wrapped mechanic. The content celebrates the user's accomplishment; my brand is the attribution. Every shared card is a free acquisition impression delivered by my most invested user. Granola's growth coverage attributes a meaningful share of their early lift to this exact pattern.

**Why it actually works (the human part):** people share evidence of discipline. A freelancer who logged 38 hours of focus time this week and is quietly proud will share that image to the LinkedIn audience of other freelancers and small founders who care about discipline. She is not advertising me. She is advertising herself. I am the credit line at the bottom.

**What I have not solved:** social media crawlers do not run client-side JS, so the personalized image preview falls back to a generic one in Twitter and LinkedIn thumbnails. The personalized card only shows when a human clicks through to the share page itself. Worth knowing before you ship.

---

### 10\. The boring email worth more than the clever ones

Every monthly subscriber who hits day 30 of paid gets a one-time email: *"Switch to annual and save $48."* Daily cron. Dedicated upgrade page that pre-fills the plan switch.

**Why it works (the data):** Baremetrics measures monthly plan retention at about 68% and annual plan retention at about 92%. Annual subscribers churn roughly 3 to 5x less than monthly. Involuntary churn (failed payments) drops by up to 95% because the card runs once a year instead of twelve times. OpenView and ProfitWell document meaningful month-2-to-4 conversion from monthly to annual when prompted at the right moment.

**Why it actually works (the human part):** a monthly subscriber at month two is invested. She has felt the product work for eight weeks. She has absorbed it into her week. The annual plan is not *"spend more money."* It is *"lock in the price you are already paying and stop thinking about it."* Most people, given the chance to stop thinking about a recurring decision, will take it.

**What it taught me:** I had been quietly losing this revenue for weeks before I shipped the email. The boring email turned out to be worth more than any of the clever ones above. **If you only ship one feature from this list, ship this one.** It is the highest leverage email you are not sending today, and it is the closest thing to free money in this entire post.

---

## What I considered and did not ship

For balance, four features I considered through the same 30-day test and rejected.

- **AppSumo lifetime deal.** Failed the test on a different axis: the audience is price-sensitive in a way that anchors the perception of the regular tier downward. The 70% revenue share also hits worse at low margin. Revisit at year two.
- **Aggressive trial extension on email verification.** Tested the manipulative-versus-helpful line and it felt manipulative. *"Verify your email and get +3 days"* reads as a bribe, not an extension. Cut.
- **Heavy LinkedIn personal posting.** Wrong audience for a $12 a month freelancer product. LinkedIn CPL math does not work at this price point even with organic. Defer until I have business-cohort data.
- **Removing the free tier.** Reverse trial only works if there is a free tier on the other side to land on. Removing it would kill the activation mechanic that is doing all the work today. Sometimes the right answer is to not change anything.

---

## Yes, I know

A few things I expect in the comments. Saving the round trip.

**"A referral program is pointless this early."** Fair on the absolute numbers this month. But the cost of installing the loop now is the same as installing it at 10x the user base, and the only loop I cannot measure is the one I did not build. I would rather have an unfired referral mechanic in month two than rebuild it from scratch in month twelve.

**"You shipped 10 features in 4 days; quality has to be bad."** Reasonable concern. None of these touches the core product. They are bolt-ons: emails, modals, public pages, a handful of scheduled jobs. Every one has tests. Every one is feature-flagged so I can flip it off if conversion drops 10% for three consecutive days without redeploying. The honest tradeoff I made to ship this fast: I have data on almost none of them yet. I will know in 30 days.

**"This is just the OpenView playbook with extra steps."** Yes. The playbook is public for a reason. Most founders read it and do not ship it. I shipped it.

**"None of this matters if your product is not good."** Agreed. Product comes first. Flowly has paying customers and healthy visit-to-signup conversion. The product holds. Distribution was the bottleneck; the 10 loops above are the fix. If your situation is the inverse (great distribution, leaky product), this list is not for you and I wish I had your problem.

---

## What is next

The metric I care about is trial-to-paid conversion 30 days from now. The whole thesis is that compound returns on 10 loops beat one viral spike nobody can reproduce on purpose.

I will come back in 30 days with which of the 10 actually moved a metric, which were a waste, and which one I would have built differently. If that interests you, follow this account. Part 2 will have the data.

You can look at the actual implementations live:

- Public roadmap: [flowly.run/roadmap](http://flowly.run/roadmap)
- Templates gallery: [flowly.run/templates](http://flowly.run/templates)
- Free pomodoro tool: [flowly.run/pomodoro-timer](http://flowly.run/pomodoro-timer)

The product itself: [flowly.run](http://flowly.run/). Free tier, 14-day reverse Pro trial, no card.