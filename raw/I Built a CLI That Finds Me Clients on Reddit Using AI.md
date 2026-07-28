---
title: "I Built a CLI That Finds Me Clients on Reddit Using AI"
source: "https://dev.to/hidekiryu/i-built-a-cli-that-finds-me-clients-on-reddit-using-ai-55dc"
author:
  - "[[hideki]]"
published: 2026-07-23
created: 2026-07-25
description: "tl;dr — I got tired of manually scrolling Reddit for people asking \"who can build me a landing page?\"... Tagged with ai, cli, rust, sideprojects."
tags:
  - "clippings"
---
**tl;dr** — I got tired of manually scrolling Reddit for people asking "who can build me a landing page?" so I built a Rust CLI that scans subreddits, uses AI to score buying intent, and hands me a ranked list of leads. Open source, runs locally, works with Ollama or any cloud AI provider.

---

## The Problem

I'm a freelancer. Half my clients come from Reddit — someone posts in r/SaaS or r/startups asking for help, and I reply. Simple.

Except it's not simple. The workflow looks like this:

1. Open Reddit
2. Scroll through 6 subreddits
3. Read every post
4. Ignore 95% of them
5. Maybe find 1-2 posts where someone is actually looking to hire
6. By the time you find them, 3 other freelancers already replied

It's a full-time job just to find leads. And the signal-to-noise ratio is terrible — most posts are people venting, sharing links, or asking questions they don't need help with.

I wanted a tool that does the scrolling for me and only shows me posts where someone is ready to spend money.

## What Cypher Does

Cypher is a terminal tool that:

- Scans subreddits you're watching
- Filters posts by keyword match first (cheap, fast)
- Sends matching posts to AI for signal extraction (intent, budget, urgency)
- Scores each lead 0-100
- Shows you a ranked table in the terminal

You tell it what you do in one sentence. It suggests subreddits to watch and keywords to filter by. Then you just run `cypher scan` when you're ready to find leads.

## The Stack

**Language:** Rust — because I wanted it fast and I wanted a single binary I could `cargo install` and forget about.

**Reddit data:** [Sylvia API](https://sylvia-api.com/) — a Reddit data proxy that handles rate limits, parsing, and anti-bot measures. I didn't want to build a scraper. I just wanted an API key and clean JSON. Sylvia does that.

**AI layer:** Hybrid — local Ollama for speed, cloud fallback (OpenAI, Groq, Gemini, OpenRouter) for when the local model isn't confident enough. You set a `cloud_threshold` score and anything above it gets re-analyzed by a stronger model.

**Database:** SQLite — stores leads locally at `~/.local/share/cypher/leads.db`. No cloud, no accounts, no tracking.

## How It Works Under the Hood

### 1\. Profile Setup

You run `cypher init` and describe what you do:

```
I build landing pages for SaaS startups
```

Cypher takes that sentence, sends it to your configured AI provider, and gets back:

- A list of subreddits where your clients hang out
- Keywords to filter posts by

For "landing pages for SaaS startups," it might suggest:

- r/SaaS, r/startups, r/webdev, r/Entrepreneur, r/smallbusiness
- Keywords: "landing page," "need a website," "looking for designer," "conversion"

### 2\. Scan Pipeline

```
cypher scan
```

This is the core loop:

```
Fetch recent posts from watched subreddits (Sylvia API)
    ↓
Keyword filter (cheap, fast — throws out 80% of posts)
    ↓
AI analysis on remaining posts
    ↓
Extract signals: intent, budget, urgency, service needed
    ↓
Score 0-100 based on signal strength
    ↓
Store in local SQLite
    ↓
Display ranked table
```

The keyword filter is important — it saves API calls and AI tokens. If a post doesn't contain any of your keywords, it never touches the AI layer.

### 3\. Lead Scoring

Each lead gets a score based on:

| Signal | Weight | What it measures |
| --- | --- | --- |
| Intent | 30% | How clearly they're looking to hire (vs. just asking a question) |
| Budget | 25% | Whether they mention money, or it's implied |
| Urgency | 25% | Time pressure ("need this done by Friday" vs. "someday") |
| Fit | 20% | How well the post matches your profile description |

A post like "Need a landing page done, budget $3k, launching next week" scores high. "Anyone know a good landing page builder?" scores low — they're probably looking for a tool, not a person.

### 4\. The AI Layer

This is where it gets interesting. Cypher supports two modes:

**Local (Ollama):** Runs `qwen3:4b` locally. Fast, free, private. Good enough for most lead scoring.

**Cloud fallback:** When the local model's confidence is below `cloud_threshold`, Cypher sends the post to your first configured cloud provider (OpenAI, Groq, Gemini, or OpenRouter). If that fails, it tries the next one.

The config looks like this:

```
[ai]
local_model = "qwen3:4b"
ollama_url = "http://127.0.0.1:11434"
cloud_threshold = 70
openai_api_key = "sk-..."
openai_model = "gpt-4o-mini"
groq_api_key = "gsk_..."
groq_model = "llama-3.3-70b-versatile"
```

You don't need all of them. Just one cloud provider works. Ollama is optional — if you don't have it, everything goes through cloud.

### 5\. Daemon Mode

If you want continuous monitoring:

```
cypher daemon --interval 60
```

Scans every 60 seconds. Good for leaving running while you work — new leads pop up in your terminal as they appear.

## The Commands

```
cypher init          # Setup profile, API keys, subreddits
cypher scan          # One-shot scan
cypher leads         # List all leads
cypher leads --min-score 80 --status new
cypher lead <id>     # Detailed view of one lead
cypher watch r/SaaS  # Add subreddit to watchlist
cypher unwatch r/SaaS
cypher watchlist     # List all watched subreddits
cypher daemon        # Background scan loop
cypher export csv    # Export to CSV
cypher export json   # Export to JSON
cypher status        # Config and status check
```

## Try It

```
# Install
cargo install --path .

# Setup
cypher init

# First scan
cypher scan
```

You'll need:

- Rust 1.70+
- A [Sylvia API](https://sylvia-api.com/) key (free tier works)
- At least one AI provider (Ollama local, or any cloud key)

## What I'd Do Differently

A few things I'd change if I rebuilt this:

1. **Webhook alerts** — instead of just terminal output, send high-score leads to Slack or Telegram. I'm building this next.
2. **Reply templates** — store pre-written responses per subreddit. When you find a lead, one key to copy a tailored reply.
3. **Historical scoring** — track how your lead quality changes over time. Are you getting better at finding clients, or just finding more noise?
4. **Multi-profile** — right now it's one profile per config. If you offer multiple services, you need separate configs.

## Why Open Source

I built this because I needed it. I'm not trying to turn it into a SaaS — it runs locally, on my machine, with my API keys. If you find it useful, use it. If you want to add features, open a PR.

GitHub: [hidekiryuuga/cypher](https://github.com/hidekiryuuga/cypher)

---

*Cypher is built with [Sylvia API](https://sylvia-api.com/) — a Reddit data proxy that handles rate limits, parsing, and anti-bot measures. If you're building anything that needs Reddit data, check it out.*

DEV Community

[![Google AI Education track image](https://media2.dev.to/dynamic/image/width=775%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fu09y9fffqrb2one15j3g.png)](https://dev.to/deved/build-apps-with-google-ai-studio?bb=238781)

## Build Apps with Google AI Studio 🧱

This track will guide you through Google AI Studio's new "Build apps with Gemini" feature, where you can turn a simple text prompt into a fully functional, deployed web application in minutes.