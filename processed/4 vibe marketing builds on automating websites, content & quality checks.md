---
title: "4 vibe marketing builds on automating websites, content & quality checks"
source: "https://thevibemarketer.beehiiv.com/p/4-vibe-marketing-builds-on-automating-websites-content-quality-checks"
author:
  - "[[The Vibe Marketer]]"
published: 2026-07-30
created: 2026-07-31
description: "Human for direction + judgment & AI for execution."
tags:
  - "clippings"
---
## Human for direction + judgment & AI for execution.

Hey Vibe Marketer,

**“AI is not replacing you.”**

In fact, it's about to do the opposite: it's going to remind you what your actual job was supposed to be all along.

==**Before**====: human → ideate → execute → quality check → ship==  
==**Now**====: human decides → AI does the work → human approves.==

Traditionally, a person sat inside the work: writing the code, designing the asset, checking every listing manually, running the audit themselves.

In this week's **[vibe marketing builds](https://www.thevibemarketer.com/?utm_source=thevibemarketer.beehiiv.com&utm_medium=referral&utm_campaign=4-vibe-marketing-builds-on-automating-websites-content-quality-checks)**, that middle step is gone.  
  
Fully delegated. The human shows up before the work starts, to decide what should happen, or after it finishes, to decide if it's actually good. Never in between.

### 4 builders. 4 different products. Same exact pattern.

**James Pinder** doesn't scout listings, write SEO code, or draft the newsletter. Agents execute all of it. His one job: look at what came out and click "approve."

**Sourabh Band** writes the content briefs, the voice doc, the project spec, before Claude Code touches anything. Once that spec exists, he doesn't build the site. He set the direction once, then stepped back.

**Tony Morinello** doesn't personally re-audit his code. He reads the executive summary and the milestone plan, and decides what to fix next. He's judging the output, not doing the auditing.

**Spencer Stewart** takes it the furthest. No prompt, no dashboard, just an @ mention. The agent decides what to generate. He's barely even upstream anymore.

Let's dive right in.

## Build #1 - The local directory that runs itself

==*(by James Pinder)*==

Running a local directory usually means one person doing everything by hand: scrolling Instagram for events, manually entering listings, guessing when hours changed, writing code for every SEO update. James built a swarm of specialized agents to do it instead.

| **Step** | **Input** | **Output** | **Outcome** |
| --- | --- | --- | --- |
| Scout new listings | Instagram and web search across Bucks, Montgomery, and Chester counties | Structured drafts of new restaurants, shops, and events (via Suburb Scout) | New listings surfaced without manual scrolling |
| Manage events | Daily checks on existing event listings | Flags for cancellations, date changes, and stale listings (via Happenings Herald) | Listings stay current without manual checking |
| Find SEO opportunities | Google Search Console and site data | Ranking recommendations, approved by James, then coded and opened as a GitHub PR (via BurbSEO and WebBurb) | SEO updates shipped without James writing code |
| Handle sponsors and coordinate | Airtable data, incoming leads | Triaged leads, featured listing/sponsorship handling, monthly sponsor reports (via BrokerBurb); system-wide coordination and routing (via Burbs Maestro) | Sponsor pipeline and system coordination run without manual routing |
| Assemble the newsletter | All compiled data | A finished weekly newsletter, designed and assembled (via Burbsworth Goodletter) | Newsletter produced without manual formatting |

James's role in all of it: "James acts as the editor and final approver." The agents never publish content, merge code, or sell recommendations without his approval, they just get the recommendation in front of him.

**Checkout the site here:** [**https://goodburbs.com**](https://goodburbs.com/?utm_source=thevibemarketer.beehiiv.com&utm_medium=referral&utm_campaign=4-vibe-marketing-builds-on-automating-websites-content-quality-checks)

## Build #2 - Ship faster with the right AI workflow

==*(by Sourabh Band)*==

Rebuilding a company website usually means three separate hires and three separate timelines: content, design, and development. Sourabh ran all three through Claude Code against a project spec he wrote himself.

| **Step** | **Input** | **Output** | **Outcome** |
| --- | --- | --- | --- |
| Plan the content | Keyword research, content briefs | Full site structure: homepage, about, blog, contact, enquiry page, an 11-park destinations hub, a 3-package safaris hub | Every page targets real search terms instead of guesses |
| Lock the voice | A voice and positioning doc written first | A consistent tone across every page | Tone doesn't drift page to page |
| Design the site | Client's existing brand guidelines and logo assets, started in Figma | A design rebuilt in code instead of a page builder | Matches the client's brand instead of a generic template look |
| Build the site | Figma files, project spec, run through Claude Code | A static Next.js site on Cloudflare Pages, no database or plugin bloat | Fast-loading site, replacing the old WordPress build |
| Capture leads | Enquiry form, WhatsApp click tracking | Submissions emailed to the client and logged to a Google Sheet; WhatsApp vs. contact-form click data | Client can check leads without logging into WordPress |

Sourabh's actual pitch: "content, design, and development used to be three separate hires and three separate timelines. One person with the right AI workflow can do all three and ship faster than a traditional agency setup."

**Site:** **[jungleejourneys.com](https://jungleejourneys.com/?utm_source=thevibemarketer.beehiiv.com&utm_medium=referral&utm_campaign=4-vibe-marketing-builds-on-automating-websites-content-quality-checks)**

==*(by Tony Morinello)*==

Most AI code audit prompts grade on vibes: ask an LLM how good your codebase is, it eyeballs a few files, and it lands on a B. Every time. No matter how much you fix, the grade barely moves. Tony rebuilt the audit prompt to fix that ceiling.

| **Step** | **Input** | **Output** | **Outcome** |
| --- | --- | --- | --- |
| Measure before judging | Linters, security scanners, dependency vulnerability checks, dead code detection, duplication checks, test coverage tools | Real, tool-generated data as ground truth | The model triages real data instead of guessing from a few files |
| Grade on a fixed rubric | Nine weighted areas (security, testing depth, architecture, code quality, correctness, performance, dependencies, dev experience, documentation), each scored 0-4 | A weighted GPA mapped to a letter grade | The grade becomes a formula, not an opinion |
| Track findings over time | Prior run's scorecard and findings ledger | Findings marked closed, never deleted | Re-runs credit work already done instead of resetting to B |
| Sweep without a cap | Full codebase scan, repeated until two full passes turn up nothing new, plus a "skeptic" pass to disprove findings | A complete findings backlog with no top-15 limit | Smaller issues that separate a B from an A don't get skipped |
| Turn findings into a plan | The full backlog | A milestone-ordered remediation plan and executive summary | Tony knows the single highest-leverage thing to do next |

Every run produces `scorecard.md`, `backlog.jsonl`, `closed.md`, a `census` folder of raw tool outputs, a remediation plan, and an executive summary. Run it inside a tool that can execute commands, like Claude Code or Cursor, so it can run the real scanners instead of just reading files.

**Grab Tony's version here:** **[https://github.com/MorinelloA/audit-improvement-prompt](https://github.com/MorinelloA/audit-improvement-prompt?utm_source=thevibemarketer.beehiiv.com&utm_medium=referral&utm_campaign=4-vibe-marketing-builds-on-automating-websites-content-quality-checks)**

==*(by Spencer Stewart)*==

Marketing teams already work in Slack. Spencer's question: why send them somewhere else to get assets made? Brand Pulse answers by generating images directly inside the thread.

| **Step** | **Input** | **Output** | **Outcome** |
| --- | --- | --- | --- |
| Trigger the agent | @ mention with a brand URL and/or social media link | The agent researches the brand from the site and socials | No prompt input, no dashboard needed |
| Decide what to make | Brand research | The agent decides what types of images would actually fit | No manual creative direction required |
| Generate the images | Bloom (image generation), inside one Runtype canvas | Marketing images | Assets produced in about 30 seconds |
| Deliver the output | Generated images | Images posted back into the Slack thread | Team gets assets without leaving Slack |

**Built with:** **[https://www.trybloom.ai/](https://www.trybloom.ai/?utm_source=thevibemarketer.beehiiv.com&utm_medium=referral&utm_campaign=4-vibe-marketing-builds-on-automating-websites-content-quality-checks)** **and** **[https://www.runtype.com/](https://www.runtype.com/?utm_source=thevibemarketer.beehiiv.com&utm_medium=referral&utm_campaign=4-vibe-marketing-builds-on-automating-websites-content-quality-checks)**

## Wrapping Up

Four builders, four different products, same question answered the same way: where does your judgment actually need to be?

Not in the middle. Pick your edge, spec it or approve it, and let the system run.

The work still gets done. It's just not you doing it anymore. That's the whole shift.

—

## Miscellaneous vibes

4\. you don't need many tools to **[turn hermes agent into a smart marketing research assistant](https://www.linkedin.com/posts/iamavibemarketer_smart-marketing-assistant-ugcPost-7488208273435918336-_0ZY/?utm_source=share&utm_medium=member_desktop&rcm=ACoAAGdTJrIBiEPt975SkkYdTCZa9VT80DcyEsw)** …

## Let’s vibe

Crazy time to be building with AI.  
  
==Wanna know if your business is showing up on ChatGPT?== ==**[Run your audit.](https://boringmarketing.com/audit?utm_source=thevibemarketer.beehiiv.com&utm_medium=referral&utm_campaign=4-vibe-marketing-builds-on-automating-websites-content-quality-checks)**==  
Wanna scale marketing and outperform your competitors? **[Upgrade your AI.](https://www.thevibemarketer.com/skills?utm_source=thevibemarketer.beehiiv.com&utm_medium=referral&utm_campaign=4-vibe-marketing-builds-on-automating-websites-content-quality-checks)**  
Wanna learn from marketers actually shipping with AI? **[Upgrade yourself.](https://www.skool.com/the-vibe-marketers?utm_source=thevibemarketer.beehiiv.com&utm_medium=referral&utm_campaign=4-vibe-marketing-builds-on-automating-websites-content-quality-checks)**  
Wanna unlock both at once? **[Get the bundle.](https://www.thevibemarketer.com/bundle?utm_source=thevibemarketer.beehiiv.com&utm_medium=referral&utm_campaign=4-vibe-marketing-builds-on-automating-websites-content-quality-checks)**  
  
Got feedback or a question? Just hit reply. I read every message.

Know someone who’d love this newsletter? Share it with a friend who is figuring AI out too.

**The Vibe Marketer**

### How'd you like this letter?

Was this a vibe?

[Login](https://thevibemarketer.beehiiv.com/login) or [Subscribe](https://thevibemarketer.beehiiv.com/subscribe) to participate in polls.