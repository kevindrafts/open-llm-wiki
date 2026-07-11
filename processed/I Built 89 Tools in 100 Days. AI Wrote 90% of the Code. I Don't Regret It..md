---
title: "I Built 89 Tools in 100 Days. AI Wrote 90% of the Code. I Don't Regret It."
source: "https://dev.to/dngzihng114379/i-built-89-tools-in-100-days-ai-wrote-90-of-the-code-i-dont-regret-it-563j"
author:
  - "[[Zihang Dong 董子航]]"
published: 2026-07-05
created: 2026-07-07
description: "The 'hand-written code backlash' misses the point. Here's what actually happens when one developer... Tagged with ai, webdev, productivity, startup."
tags:
  - "clippings"
---
The 'hand-written code backlash' misses the point. Here's what actually happens when one developer ships a full SaaS with AI — and what the critics get wrong.

The current dev.to narrative is clear: AI coding is creating a generation of "prompt engineers" who can't debug their own code. The hand-written code backlash is real — a recent HN post arguing for ditching AI coding assistants hit 737 points. "Vibe coding" is a punchline. Senior engineers are writing manifestos about comprehension gaps and skill atrophy.

I want to offer a counterpoint — not from theory, but from production.

On March 18, 2026, I launched [ToolKnit.com](https://toolknit.com/) — a privacy-first online toolbox. 109 days later, the site has **89 browser-based tools**, **87 blog posts**, a **DR 41 domain rating**, and thousands of monthly visitors from Google and Bing. Every tool runs 100% client-side. No backend. No database. No signup.

AI wrote roughly 90% of the code.

Here's the part the critics don't tell you: **it worked**. And I think the backlash, while understandable, is fighting the wrong battle.

## What "90% AI-Generated" Actually Means

Let me be precise, because the numbers matter.

ToolKnit has 89 tools. Each tool has:

- An HTML page (~350-600 lines of semantic markup)
- A JavaScript engine (~200-800 lines of logic)
- i18n translations in English and Chinese
- SEO metadata, JSON-LD structured data, Open Graph tags
- A service worker entry
- A sitemap entry

That's roughly **55,000 lines of code** across the project.

I hand-wrote exactly **zero** of those lines from scratch. Every file started with an AI prompt. Some took 3 iterations. Some took 15. But the initial scaffolding, the repetitive patterns (tool cards, footer components, meta tags), the JavaScript logic — AI generated all of it.

But here's the catch: **I read and understood every line.**

## The Workflow That Makes AI Actually Work

The anti-AI crowd describes a world where developers paste AI output into production without reading it. I don't know anyone who actually works that way. Here's my real workflow:

### Phase 1: Architecture (Human)

AI cannot design a system. It can't decide that 89 tools should share a common `bilingual.js` engine rather than each implementing their own language toggle. It can't plan a service worker caching strategy or decide which CDN to use.

I made all architectural decisions. I designed the component patterns, the file structure, the CSS custom property system, the build pipeline. This is the work that determines whether a project survives six months or collapses under its own weight.

### Phase 2: Scaffolding (AI)

Once the patterns were established, AI became a multiplier. "Create a new tool page following this template, with these features, using this CSS framework." 90 seconds later, I had a complete HTML file with working JavaScript.

The AI understood the patterns because I'd already established them. It knew the bilingual setup because [bilingual.js](https://toolknit.com/assets/js/bilingual.js) was part of the project context. It knew the footer pattern, the tool card pattern, the SEO pattern.

### Phase 3: Review & Fix (Human)

This is where the 70% rejection rate from the studies comes in. AI gets things wrong. It hallucinates API names. It generates CSS that looks right but breaks at certain viewports. It writes JavaScript that handles the happy path but ignores edge cases.

But here's the thing: **reviewing AI-generated code is faster than writing it from scratch.** The cognitive load of "is this correct?" is lower than "what should I write and is it correct?".

For ToolKnit, the review phase typically took 5-10 minutes per file. I'd scan for:

- Logical errors (timer countdowns that don't handle pause correctly)
- Edge cases (what happens when localStorage is full?)
- Security issues (never trust user input, even in client-side tools)
- i18n completeness (did the Chinese translations actually get generated?)

### Phase 4: Iterate (Human + AI)

The back-and-forth is where the real work happens. "The progress ring doesn't update when switching tabs." "The mobile layout breaks at 320px." "The Chinese translation for 'health recovery timeline' is awkward."

Each fix is another AI prompt. Each prompt takes 30 seconds. Each fix takes 2 minutes to verify.

## What the Critics Get Right

I want to be fair to the backlash. They're not entirely wrong.

**AI code converges on the median.** If you let AI design your architecture, you'll get a generic React app with useState and useEffect everywhere. It won't be wrong, but it won't be good. The median is fine for CRUD. It's death for anything novel.

**The comprehension gap is real.** When I wrote code by hand ten years ago, I built a mental model of every subsystem. With AI, I have to *actively* build that model by reading the generated output. It's a different kind of understanding — more like code review than authorship — but understanding still happens if you're disciplined about it.

**Debugging AI-generated code is harder.** When you wrote it yourself, you know where the bodies are buried. When AI wrote it, you have to discover them. This is the single biggest productivity drag in my workflow. I've spent 45 minutes debugging a 200-line JavaScript file that AI wrote in 90 seconds. That ratio is real and it's painful.

## What the Critics Get Wrong

**They assume AI replaces thinking.** It doesn't. It replaces typing. The thinking — architecture, design decisions, user experience, SEO strategy — all of that still comes from a human. AI is a force multiplier for execution, not a substitute for judgment.

**They compare AI output to ideal human output.** The fair comparison is AI output vs. what one developer can actually ship in a given timeframe. I could have built ToolKnit without AI. It would have taken 500 days instead of 100. And in those 400 extra days, I probably would have made just as many mistakes — just slower.

**They ignore the solo developer economics.** I'm one person. I don't have a team. I don't have a QA department. AI is my rubber duck, my code reviewer, my junior developer, and my documentation writer. For a solo founder, the alternative to "AI with careful review" isn't "pristine hand-written code." It's "shipping 15 tools instead of 89."

## The Tools That Prove the Point

Some examples from ToolKnit where AI genuinely accelerated shipping:

**[Quit Smoking Tracker](https://toolknit.com/tools/quit-smoking-tracker.html)** — A behavioral reinforcement tool with localStorage persistence, a 10-stage health recovery timeline (based on CDC/WHO research), achievement badges, and bilingual support. The core logic — calculating cigarettes avoided, money saved, life minutes regained — took about 4 prompts to implement. The health timeline component took another 3. Total dev time: ~2 hours.

**[Pomodoro Timer](https://toolknit.com/tools/pomodoro-timer.html)** — Circular progress ring with SVG animation, three work/break modes, configurable durations, audio alerts, and tab title countdown. The SVG arc animation logic alone would have taken me an hour to write from scratch. AI generated it in one prompt. I spent 15 minutes fixing edge cases (what happens when the user switches tabs?).

**[PDF to Image](https://toolknit.com/tools/pdf-to-image.html)** — Converts PDF pages to PNG/JPG/WebP using pdf.js and canvas. This would have been a multi-day deep dive into the pdf.js API. AI knew the API surface area, generated the rendering pipeline, and handled the format conversion options. I verified correctness and fixed browser-specific rendering bugs.

The pattern repeats across all 89 tools. AI handles the API integration, the boilerplate, the repetitive patterns. I handle the architecture, the UX decisions, the edge cases, and the quality gate.

## So Should You Use AI to Write Code?

In 2026, asking "should I use AI to code?" is like asking "should I use a framework?" in 2016. The answer depends on what you're building and who you are.

**Use AI aggressively if:**

- You're a solo developer shipping a product
- Your project has clear, repeatable patterns
- You understand the code well enough to review it
- Speed-to-market matters more than architectural elegance

**Be skeptical of AI if:**

- You're building novel, performance-critical systems
- You're a junior developer who can't evaluate AI output yet
- Your project has complex state management or race conditions
- You're working on security-sensitive infrastructure

The critical variable isn't the tool. It's **whether you're capable of reviewing what the tool produces.** If you can spot the bugs, AI is a multiplier. If you can't, AI is a liability.

This is why the most dangerous advice in tech right now is "just use AI, you don't need to learn to code." You absolutely need to learn to code. You just might not need to type as much.

## The Bottom Line

109 days. 89 tools. 87 blog posts. DR 41. Real traffic from Google and Bing. All built by one person with AI assistance.

The hand-written code crowd isn't wrong about the risks. They're wrong about the conclusion. The goal shouldn't be hand-written code. The goal should be **understood code** — code where the developer, AI-assisted or not, knows what every line does and why it's there.

AI didn't build ToolKnit. I built ToolKnit. AI typed faster than I can. That's it. That's the entire magic trick.

And I don't regret a single prompt.

---

*[ToolKnit.com](https://toolknit.com/) is a free, privacy-first online toolbox with 89 browser-based utilities. No uploads, no signup, no ads. All tools run entirely in your browser.*

---

**What's your experience with AI coding?** Has it been a multiplier or a liability for your projects? I'm genuinely curious — especially if you're in the "going back to hand-written code" camp. Drop a comment.

[![Google article image](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fes646druifsk2owm2v3e.png)](https://dev.to/googleai/antigravity-managed-agents-tutorial-ship-production-ai-agents-21c0?bb=263653)

## Antigravity Managed Agents Tutorial: Ship Production AI Agents

Managed Agents represent a fundamental shift in how we build with AI. You’re no longer building the infrastructure around the AI, you’re simply giving the AI a goal and a sandbox, and letting it work. The sandbox is the abstraction. The agentic loop is the engine. And the Interactions API is your single point of contact with all of it.