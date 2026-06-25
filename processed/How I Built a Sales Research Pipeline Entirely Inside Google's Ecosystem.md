---
title: "How I Built a Sales Research Pipeline Entirely Inside Google's Ecosystem"
source: "https://cashandcache.substack.com/p/i-used-gemini-to-find-sales-leads"
author:
  - "[[Raghav Mehra]]"
published: 2026-05-21
created: 2026-05-26
description: "A step-by-step build using Gemini Deep Research, NotebookLM, and Google Sheets — with the scoring framework, the prompts, and every client outreach strategy along the way."
tags:
  - "clippings"
---
> ***TLDR🧠: I built a sales research pipeline using Gemini Deep Research, NotebookLM, and Google Sheets — entirely inside Google's ecosystem. Two commands in a custom Gem produce a scored lead profile with outreach draft in under 20 minutes. Tested on three companies. Includes the full 0-16 scoring framework, every prompt, and the custom Gem instructions to copy.***

Last Tuesday, I needed to evaluate two companies as potential clients for AI implementation consulting. One was a global fintech. The other was a private healthcare IT firm.

The old way: twelve browser tabs. LinkedIn for decision-makers. Crunchbase for funding. The company blog for product announcements. Job postings for tech stack signals. Google News for recent press. Forty-five minutes per company, minimum. By the end, my notes are scattered across three apps and a sticky note, and I still don’t know if either company is worth a cold outreach.

So I tested something different. I built a research pipeline using Gemini Deep Research, NotebookLM, and Google Sheets — all Google, one ecosystem, no code — to go from a company name to a scored, qualified lead with a personalised outreach draft.

This is that build. The full prompt framework, the scoring system, the failures, and the fixes.

*👋 Hi, **I’m Raghav***

In Cash & Cache, along with Ashwin, I publish weekly on AI implementation & strategy, and every workflow we cover ships with a downloadable asset in the Library.

*Browse the Library **→** **[Cash & Cache Library](https://cashandcachewebsite.vercel.app/library)***

*Not sure where to start? **[Take the quiz](https://cashandcachewebsite.vercel.app/start)***

*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
**The gap between "I should research that company" and actually having a qualified lead with an outreach angle is 45 minutes of tab-switching nobody talks about.***

---

### In this post, we will cover:

- [Before You Touch Gemini: The Homework That Actually Matters](https://cashandcache.substack.com/i/198871081/before-you-touch-gemini-the-homework-that-actually-matters)
- [What the Research Pipeline Actually Produces](https://cashandcache.substack.com/i/198871081/what-the-pipeline-actually-produces)
- [The Pipeline: How It Works, including the full setup](https://cashandcache.substack.com/i/198871081/the-pipeline-how-it-workshttps://cashandcache.substack.com/i/198871081/the-pipeline-how-it-works)
- [The Research Prompt: What Each Section Does](https://cashandcache.substack.com/i/198871081/the-research-prompt-what-each-section-does)
- [Finding the Right Person — And Why LinkedIn Is Non-Negotiable](https://cashandcache.substack.com/i/198871081/finding-the-right-person-and-why-linkedin-is-non-negotiable)
- [The Scoring Framework: Turning Research Into a Decision](https://cashandcache.substack.com/i/198871081/the-scoring-framework)
- [NotebookLM: Where It Challenged My Scores](https://cashandcache.substack.com/i/198871081/notebooklm-where-it-challenged-my-scores)
- [The Compounding Layer: Gemini in Sheets + Gmail](https://cashandcache.substack.com/i/198871081/the-compounding-layer)
- [Repeatable Systems Pack: Gem Instructions + All Prompts](https://cashandcache.substack.com/i/198871081/repeatable-systems-pack)

![](https://substackcdn.com/image/fetch/$s_!4COG!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff4187967-0e8b-4bb1-8d72-91136efc82d5_1408x43.png)

## Before You Touch Gemini: The Homework That Actually Matters

Often AI prospecting tutorials skip this. They hand you a prompt, tell you to type a company name, and act like the hard part is getting AI to produce a report. It isn’t. The hard part is knowing what to ask for.

I spent more time preparing for this pipeline than running it.

1. **You need to understand your own offering with uncomfortable specificity.** Not “I do AI consulting.” What kind of AI work? For what kind of company? Solving what kind of problem? I help mid-market companies move from “we should use AI” to “we’ve actually built something that works” — through workflow automation, internal tool development, and AI integration into existing products. That specificity shaped every prompt. The research prompt prioritises “AI & Technology Posture” as the heaviest section because that’s where my sales signals live. A cybersecurity consultant would weight “compliance gaps.” A CFO advisory firm would weight “financial infrastructure maturity.” Your service defines your research lens.
2. **You need companies already in mind.** This pipeline is not for open-field discovery. It won’t tell you *which* companies to target. It tells you everything about companies you’ve already identified as worth investigating. Where do those targets come from? Industry news. Conference attendee lists. LinkedIn connections posting about challenges you solve. Competitor client lists. I chose my test companies because I’d already noticed signals — engineering blog posts about building internal AI agents in one case, a new Chief Transformation Officer appointment in the other. The pipeline amplifies your existing awareness. It doesn’t replace it.
3. **You need a qualification framework before you open any tool.** I defined four scoring dimensions: Budget Capacity, Need Intensity, Timing, and Accessibility. Each scored 0-4, anchored to observable evidence. “They raised a round with AI in the press release” is a 4 on Budget. “They seem well-funded” is not a score. This framework existed on paper before I opened Gemini.

> The biggest caveat in the entire article: **AI research tools are force multipliers for prepared people.** If you don’t know your value proposition and don’t have a qualification framework, Gemini will produce a beautiful, thorough, completely useless report.

![](https://substackcdn.com/image/fetch/$s_!4COG!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff4187967-0e8b-4bb1-8d72-91136efc82d5_1408x43.png)

## What the Pipeline Actually Produces

Before the build, here’s what came out the other end. For each company, four outputs.

1. **A structured intelligence brief.** Not a Wikipedia summary — a document weighted toward technology posture and AI maturity. The pipeline surfaced things like: specific internal AI tools a company had built, job postings revealing engineering bottlenecks, competitor moves creating pressure, and leadership changes signalling strategy shifts. Deep Research cited 50-100+ sources per company.
2. **A decision-maker profile.** A specific person with a verifiable name, their recent public activity (conference talks, published articles, LinkedIn posts), and a connection angle for outreach.
3. **A qualification score.** A 0-16 rating with cited evidence. One company scored 14/16 — clear fit, reach out now. Another scored 13/16 with a Need score of 1/4, revealing they were already so advanced that standard consulting wasn’t relevant. A third — Airbnb, added later to test at scale — scored 9/16: “keep on radar.” Three different scores, three different strategies. That’s the framework working.
4. **An outreach draft.** A personalised LinkedIn message under 80 words referencing something the contact actually said or published.

![](https://substackcdn.com/image/fetch/$s_!fabt!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F27bdf012-f2a7-4687-8a6a-dc7d5145f6a0_1024x541.png)

---

## The Pipeline: How It Works

Here’s the architecture. Each tool does one job, and they connect without manual data transfer.

**Gemini Deep Research** is the researcher — 50-100+ live web sources per query, synthesised into a structured report with citations. Each company took 7-10 minutes. **Gemini Chat** is the analyst — faster and more controllable for scoring, decision-maker identification, and outreach drafting. **NotebookLM** is the comparator — source-grounded, so every comparison traces back to the actual research. **Google Sheets** is the pipeline tracker, with Gemini in the sidebar making it queryable. **Gmail** feeds internal knowledge back into the research.

![](https://substackcdn.com/image/fetch/$s_!-Xoq!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ffa0d415d-0d4f-4f0f-8d83-6e144fb46e69_1024x541.png)

The export chain: Deep Research → Google Docs → NotebookLM → Data Table → Google Sheets, with Gmail feeding additional context back in. One ecosystem, one login.

I built a custom Gem so I don’t re-type the framework every time. I called it the “Sales Lead Researcher” and gave some custom instructions that form the bedrock of very research query I put.

Following this, use two commands for each company to extract research details, score them across KPIs that measure goodness-of-fit to your companies and an outreach draft message to the most relevant personnel in the prospective client (also found through this research).

```markup
Research [Company Name]
```

This triggers Deep Research with the full structured framework — company fundamentals, AI posture (priority section), business momentum (last 12 months only), and pain signals.

```markup
Score [Company Name]
```

This triggers decision-maker identification, 0-16 qualification scoring, and outreach drafting — all in one sequence.

The Deep Research output plan generates real-time for you to oversee how Gemini researches on the information.

![](https://substackcdn.com/image/fetch/$s_!1LS1!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fa14572c4-ec58-4da6-b834-81bc8d274288_1808x849.png)

And the kind of output the scoring produces — a complete company fundamental breakdown with cited evidence for every dimension— is very useful. You can even create a web prototype for C-suite presentation to give your research an interactive dashboard with Gemini’s newest updates.

![](https://substackcdn.com/image/fetch/$s_!jTRG!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F69b7c2b6-4401-4a68-ac2c-9162aff74eb4_1082x822.png)

Since we are working with Google Workspace, I can easily click on “Share and Export” option to generate a Google Doc version of the output.

![](https://substackcdn.com/image/fetch/$s_!0VvS!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fed1175d4-0d34-4d0b-8e87-9810e5c42134_1451x752.png)

Trade-offs, named: Deep Research is slow (7-10 minutes per company) with daily usage limits on Pro. NotebookLM is overkill for one company. Gmail search only works if you have relevant emails. This runs on Gemini Pro ($20/month).

---

*The free content for this piece ends here!*

#### 🔒 What’s behind the paywall:

*Paid subscribers get the full build — the custom Gem instructions (copy-paste ready), the 0-16 scoring rubric with criteria for every level, the exact NotebookLM comparison and verification prompts, the Gmail triage prompt, the Gemini-in-Sheets queries, and the complete Repeatable Systems Pack with every prompt and the Google Sheet schema. Everything you need to set this pipeline up in one sitting.*