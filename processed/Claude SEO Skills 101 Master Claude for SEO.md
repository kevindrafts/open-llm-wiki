---
title: "Claude SEO Skills 101: Master Claude for SEO"
source: "https://www.lawrencehitches.com/claude-skills-seo-workflows/#h-seo-skills-you-should-build"
author:
  - "[[Lawrence Hitches]]"
published: 2026-06-21
created: 2026-06-23
description: "Build Claude skills for SEO: reusable AI workflows for audits, title tags, content briefs, and meta optimisation. Step-by-step guide with real examples."
tags:
  - "clippings"
---
Claude skills are reusable AI workflows you build once and run forever. For SEO, this means you can create a skill that audits a page, another that writes content in your brand voice, another that builds internal links - then chain them together or run them on a schedule.

It's the difference between asking Claude for help once and having a permanent SEO team member who knows your site, your style, and your process.

A Claude SEO skill is a saved prompt file that tells Claude exactly how to perform a specific SEO task: content audits, [keyword research](https://www.lawrencehitches.com/keyword-research/), [internal linking](https://www.lawrencehitches.com/internal-linking-seo/), meta rewrites, and more. You build the skill once as a markdown file, save it to your Claude project, and reuse it on any URL or page. Claude skills eliminate the need to re-explain your process or preferences each session. They make Claude a permanent, consistent SEO team member rather than a one-off tool.

**Free: 29 Claude SEO Skills (open source)**

The Claude Skills the StudioHawk team runs across 500+ client SEO campaigns, open-sourced free (MIT licence) through Hawk Academy. Drop them into Claude Desktop and run agency-grade audits, content briefs, and reports.

[Get the 29 Claude SEO Skills on GitHub](https://github.com/lhitches/claude-seo-skills)

**This is the 101 guide**: the foundations and how to actually execute with them. For the full map of every Claude SEO workflow, see the [Claude SEO skills](https://www.lawrencehitches.com/claude-seo-skills/) hub, which organises everything into the three pillars of SEO: [technical](https://www.lawrencehitches.com/claude-for-technical-seo/), [content](https://www.lawrencehitches.com/claude-for-content-optimization/), and [links and digital PR](https://www.lawrencehitches.com/claude-for-link-building/).

## What Are Claude Skills?

A Claude skill is a markdown file that defines a specific behaviour. It tells Claude exactly how to approach a task - what context to use, what steps to follow, what output format to produce.

What's in this guide

Think of each skill as an SOP (Standard Operating Procedure) that Claude follows precisely, every time.

Skills live in your project directory and get loaded automatically when you run [Claude Code](https://www.lawrencehitches.com/claude-code-for-seo/). They're portable - copy them to a new project and they work immediately.

Here's what makes them powerful for SEO:

- **Consistency:** Your content refresh process runs the same way every time, not just when you remember all the steps
- **Brand voice:** Define your writing style once, and every piece of content matches it
- **Composability:** Chain skills together - audit a page, then refresh it, then add internal links, then log the test
- **Delegation:** Hand off execution to Claude while you focus on strategy

## SEO Skills You Should Build

### 1\. Content Refresh Skill

This is the highest-ROI skill you can create. It takes a URL, fetches the current content, analyses what's weak, generates an improved version, and pushes the update.

**What the skill does:**

- Fetches current content via WordPress REST API
- Checks word count, heading structure, internal links, FAQ section
- Analyses SEOtesting performance data for the URL
- Generates refreshed content in your brand voice (using a style guide context file)
- Saves a backup, pushes the new content, updates meta tags
- Logs the change for tracking

The critical detail: **your writing style guide is loaded as context**. This means Claude doesn't just rewrite content generically - it writes like you. On my site, I use an adapted Animalz editorial style: direct openers, short paragraphs, bold key terms, practitioner authority, Australian English.

### 2\. Internal Linking Skill

Internal linking is the most neglected and most impactful structural SEO task. Building a skill for it turns a multi-day project into a 15-minute job.

**What the skill does:**

- Fetches all posts and builds a topic cluster map
- Scores link opportunities using category overlap, slug matching, and title-in-content detection
- Selects contextual anchor text (not generic terms like "click here")
- Generates a dry-run plan for review
- Executes with deduplication - no duplicate anchors, no self-links, max 5 new links per post

I ran this skill across 164 posts and added **305 internal links across 73 posts** in a single session. Manually, that's easily a week of work.

### 3\. Meta Audit Skill

Ingests your SEOtesting CSV exports and identifies pages with the highest CTR opportunity - high impressions, low click-through rate, good position. Then generates improved meta titles and descriptions.

**What the skill does:**

- Parses SEOtesting pages report (CSV)
- Ranks pages by impressions × CTR gap
- Fetches current Yoast meta for each target
- Generates improved titles (max 60 chars) and descriptions (max 155 chars)
- Pushes updates via the WordPress API
- Creates SEOtesting tests to measure the impact

### 4\. Writing Style Skill (/polish)

Every piece of content should sound like it came from the same author. A writing style skill takes any draft and refines it to match your voice.

This is where the advice from marketing automation experts rings true: **"Without human strategy and authenticity, you are just automating average."** The style skill is what prevents your content from sounding like every other AI-generated article.

Define your voice characteristics explicitly:

- Opening style (direct answer vs narrative vs provocative question)
- Paragraph length (1-3 sentences max for punchy content)
- Technical depth (practitioner vs beginner)
- Formatting preferences (tables, lists, bold terms)
- Regional spelling (Australian English for AU audiences)

## Chaining Skills: The Multi-Skill Workflow

Individual skills are useful. Chaining them is transformative.

Here's a content refresh workflow that chains 4 skills:

1. **Meta Audit skill** → identifies the next page to refresh (highest ROI)
2. **Content Refresh skill** → fetches, rewrites, and pushes updated content
3. **Writing Style skill** → polishes the output to match your brand voice
4. **Internal Linking skill** → re-runs the link graph to connect the refreshed page to the rest of the site

Claude figures out the most efficient way to combine these. It runs the audit first, picks the target, generates the refresh, applies the style pass, adds links, and logs everything. You can set this to run on a schedule - Mon/Wed/Fri at 8am, one page per run.

## Sub-Agents: Parallel SEO Execution

For bigger operations, Claude Code can spawn **sub-agents** - parallel workers that each handle a piece of the task independently.

Real example from my workflow:

- **Agent 1:** Explores the codebase to understand the current [site structure](https://www.lawrencehitches.com/site-architecture/)
- **Agent 2:** Analyses SEOtesting data to identify priorities
- **Agent 3:** Researches competitor content (StudioHawk's sitemap) for gap analysis

All three run simultaneously. The main agent waits for results, then synthesises a plan. This is genuinely having three marketing assistants working in parallel.

## Context Files: The Secret to Quality Output

The difference between generic AI output and genuinely useful SEO content comes down to **context**.

Claude Code uses several context mechanisms:

- **CLAUDE.md:** Project-level instructions that load automatically. Put your site URL, CMS details, API credentials location, and key constraints here.
- **Memory files:** Persistent notes about your preferences, writing style, project status, and reference information. Claude remembers these across sessions.
- **Config files:** YAML configs for [topic clusters](https://www.lawrencehitches.com/claude-for-topical-maps/), keyword queues, and site settings. Claude reads these to understand your content strategy.
- **SEOtesting data:** CSV exports in a known directory that Claude parses for performance insights.

The more context you provide, the less you need to explain in each conversation. After a few sessions, Claude Code knows your site better than most team members would.

## Building Your First Skill

Start simple. Create a skill that does one thing well:

1. Pick your most repetitive SEO task (meta audits, content checks, link reviews)
2. Write out the steps as if explaining to a junior SEO
3. Save it as a markdown file in your project's `.claude/` directory
4. Test it on a single page
5. Refine the output until it matches what you'd produce manually
6. Then scale - run it across your entire site

The goal isn't to remove yourself from the process. It's to handle the execution so you can focus on the strategy that actually moves the needle.

## FAQ

**Can I share skills with a team?**

Yes. Skills are just markdown files in your project directory. Commit them to Git and your whole team has access. This is one of the most underrated features - you're essentially version-controlling your SOPs.

**How are skills different from ChatGPT custom instructions?**

ChatGPT custom instructions set a general behaviour. Claude skills define specific workflows with steps, context files, and output formats. Skills can also trigger other skills, access your file system, run scripts, and interact with APIs. They're executable SOPs with specific steps and output formats.

**Do I need one skill per task?**

Generally yes - small, focused skills are more reliable than one massive skill that tries to do everything. Think of them like Unix commands: each does one thing well, and you chain them together for complex workflows.

**Can skills run on a schedule without me?**

Yes. Claude Code supports scheduled tasks that fire on a cron schedule. You can set a content refresh skill to run every Monday, a monitoring skill to run daily, and a link audit to run weekly. They execute in the background and notify you when done.

## Watch: Claude across the three SEO pillars

![](https://www.youtube.com/watch?v=S18roQFhxUQ)

## Final Word

Claude skills turn one-off AI conversations into permanent SEO workflows. Build them incrementally - start with the task you do most often, automate it, then move to the next. Within a few weeks, you'll have an [AI-powered SEO](https://www.lawrencehitches.com/what-is-ai-seo/) operation that runs with minimal manual input.

The humans who win at AI-powered SEO aren't the ones using AI to generate the most content. They're the ones building the best systems.

Hawk Academy

Every skill on this page, pre-built and ready to run

All workflows are available as free Claude skills on Hawk Academy. Run them inside Claude, no setup, no API keys.

- [Technical SEO Audit](https://hawkacademy.co/claude-seo-skills/technical-seo-audit.html)
- [Competitor Gap Check](https://hawkacademy.co/claude-seo-skills/competitor-gap.html)
- [AI Visibility Check](https://hawkacademy.co/claude-seo-skills/ai-visibility.html)
- [Topical Authority Map](https://hawkacademy.co/claude-seo-skills/topical-authority-map.html)
- [Content Brief & Draft](https://hawkacademy.co/claude-seo-skills/content-brief-draft.html)
- [Ecommerce SEO Audit](https://hawkacademy.co/claude-seo-skills/ecommerce-seo-audit.html)
- [Local SEO Audit](https://hawkacademy.co/claude-seo-skills/local-seo-audit.html)
- [Information Gain Finder](https://hawkacademy.co/claude-seo-skills/information-gain.html)
- [Calculator Page Builder](https://hawkacademy.co/claude-seo-skills/calculator-page-builder.html)
- [Data PR & Outreach](https://hawkacademy.co/claude-seo-skills/data-pr-outreach.html)
[Browse All Skills on Hawk Academy](https://hawkacademy.co/claude-seo-skills)