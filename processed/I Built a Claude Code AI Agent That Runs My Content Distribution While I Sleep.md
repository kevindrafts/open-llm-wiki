---
title: "I Built a Claude Code AI Agent That Runs My Content Distribution While I Sleep"
source: "https://aiblewmymind.substack.com/p/claude-code-content-distribution-ai-agent"
author:
  - "[[Daria Cupareanu]]"
published: 2026-06-10
created: 2026-06-14
description: "An autonomous system I built in Claude Code that repurposes every new article into Reddit, LinkedIn, and more — six automations running in the cloud, four times a day, hands-off."
tags:
  - "clippings"
---
A content distribution system is the engine that takes one thing you've published and gets it onto every platform, automatically. Mine is a [Claude Code](https://aiblewmymind.substack.com/p/claude-code-workflow-beginners) AI agent that does exactly that, while I sleep.

Last week I showed you the [Cowork operating system](https://aiblewmymind.substack.com/p/claude-cowork-operating-system) I built to hold my whole working life in a set of folders [Claude](https://aiblewmymind.substack.com/p/how-to-use-claude-ai-complete-guide) reads automatically, so I [never brief it from scratch](https://aiblewmymind.substack.com/p/reuse-ai-workflows).

That’s the system for the work I want to stay deep inside: [writing](https://aiblewmymind.substack.com/p/claude-skills-ai-write-like-you) the newsletter, client projects, [Amplifiers](https://aiblewmymind.substack.com/p/ai-research-tools-claude-chatgpt). Automations run in there too, [skills](https://aiblewmymind.substack.com/p/claude-skills-ai-write-like-you), commands, whole workflows, but I’m present for every decision, by choice.

Over a month ago, maybe closer to two, I lost count, I started building a second system in [Claude Code](https://aiblewmymind.substack.com/p/claude-code-workflow-beginners). It borrows the same folder structure and the same human-in-the-loop thinking, but it exists for the opposite kind of work: **the part I dread**.

For me, that’s distribution. Getting my work in front of people, every day, on every platform.

- Turning a published article into a Reddit post that fits each subreddit, then finding and answering the threads where people ask the exact question I just covered in >2,000 words.
- Drafting a LinkedIn version, making the infographics to go with it, and queuing it for posting.
- Pulling the best lines out of the article and posting them as standalone Substack notes.
- Repurposing it for the rest: [Instagram](https://www.instagram.com/aiblewmymind.official), [Facebook](https://www.facebook.com/people/AI-blew-my-mind/61588569310192), [Threads](https://www.threads.com/@aiblewmymind.official), where I at least have a process, and [X](https://x.com/dariacupareanu), where I’d be starting from scratch.

None of it is hard, all of it takes time, and it has to happen every single day.

So I built a system to carry it. This is the engine for the growth side of my business, running while I do everything else. And it happens on its own, in the cloud, while my laptop is closed and I’m asleep.

> Think of this as Part 1: how the AI agent works today and what I learned building it, so you don’t repeat my mistakes. Part 2 is the DIY guide (your own Claude Code OS, step by step). Even if your work has nothing to do with distribution.

---

## Here’s what we’ll cover

- [Where I draw the line: what I automate and what stays human](https://aiblewmymind.substack.com/i/200892151/where-i-draw-the-line-on-what-gets-automated)
- [How my Claude Code AI agent works, at a glance](https://aiblewmymind.substack.com/i/200892151/how-my-claude-code-ai-agent-works-at-a-glance)
- [What I’m building next: a research layer, more platforms, and products from articles](https://aiblewmymind.substack.com/i/200892151/how-im-growing-the-system)
- [Why I built this in Claude Code, not Cowork](https://aiblewmymind.substack.com/i/200892151/why-i-built-this-in-claude-code-not-cowork)
- [The six automations running now, and what’s still me on purpose](https://aiblewmymind.substack.com/i/200892151/the-six-automations-and-whats-still-me-on-purpose)
- [Where the whole system lives](https://aiblewmymind.substack.com/i/200892151/where-the-whole-system-lives)
- [The folder structure, the memory files, and the engine in the cloud](https://aiblewmymind.substack.com/i/200892151/the-folder-structure-claudemd-memorymd-and-three-new-folders)
- [The anatomy of one automation, taken apart piece by piece](https://aiblewmymind.substack.com/i/200892151/the-anatomy-of-one-automation)
- [The internal wiki (inspired by Andrej Karpathy) that remembers every article I’ve written](https://aiblewmymind.substack.com/i/200892151/the-internal-wiki-that-remembers-every-article-ive-written)
- [The self-learning loop that teaches it to write like me, with the real guardrails](https://aiblewmymind.substack.com/i/200892151/the-self-learning-loop-that-teaches-claude-to-write-and-think-like-me)
- [How to build your own version, for whatever your work is](https://aiblewmymind.substack.com/i/200892151/how-to-build-your-own-claude-code-os)

Buckle up, this one runs longer than usual. It’s the full behind-the-scenes, both how the system works and how I decide what to automate.

## Where I draw the line on what gets automated

I'm starting here, before any of the how, because this one decision shapes everything else. What I automate comes down to one personal call: **what I’m okay handing over and what stays mine**.

Every piece I add, and every one I hold back, comes from it, and it keeps shifting as I get comfortable trusting the system with more.

**The newsletter writing stays mine.** This is the one I’d never automate and I feel strongly about it. The newsletter is what everything else grows from, and most of my articles are builds and experiments. The building takes the time. The [words are how I wrap it all up](https://aiblewmymind.substack.com/p/claude-skills-ai-write-like-you) so you can see what I did and do the same yourself. None of that goes into this system.

**Distribution gets automated, but nothing publishes without me.** I don't enjoy it the way I enjoy the writing, and I don't have the time to do everything that needs doing, so passing the heavy lifting to the system is what I'm after.

But handing it off isn’t the same as stepping away. I’m constantly improving my [Claude skills](https://aiblewmymind.substack.com/p/claude-skills-36-examples) for every kind of writing I do, LinkedIn, Substack notes, Instagram, Facebook, Reddit, X, and I polish every draft until it sounds like me before it goes out.

Plenty of creators post more and faster by letting AI run the whole show and it works for them. I could do that, but I won’t. I’m not trying to become a content machine.

That's my line, and I've made peace with what it costs me: more work and a system that will never be fully hands-off, because I'm not comfortable letting it run without me.

---

## How my Claude Code AI agent works, at a glance

Now, before I take it apart, here’s the whole thing in one view.

What I built is an AI agent, which is just a fancy term for software that doesn't wait to be told. Every six hours it wakes up in the cloud on its own, through a scheduled [Claude Code Routine](https://aiblewmymind.substack.com/p/claude-code-routines-tutorial), and runs whatever task is due.

![The Claude Code Routine that runs my automation OS, set to fire four times a day, with its Gmail, Slack, and Amplifiers connectors, the heartbeat prompt, and a history of successful scheduled runs.](https://substackcdn.com/image/fetch/$s_!KmpT!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F990442e2-98c2-4800-851a-e1a3370ab2bb_2760x1740.png)

The Claude Code Routine that runs my automation OS, set to fire four times a day, with its Gmail, Slack, and Amplifiers connectors, the heartbeat prompt, and a history of successful scheduled runs.

Here's everything it does right now, across a day:

- **Ingests my articles:** the moment I publish, it reads the new article from Gmail and saves it. Then it files it into my internal wiki, built on [Andrej Karpathy’s LLM wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) method (more on that later).
- **Repurposes for Reddit:** it drafts a Reddit post from that article and suggests which subreddits fit.
- **Answers Reddit threads:** it scans subreddits for questions my work already answers, which it knows because of the wiki, and drafts replies.
- **Waits for my call:** every draft comes to my Slack, where I approve, reject, or rewrite it. Each reply teaches it something. Approve, and it knows it’s on the right track. Rewrite, and it learns what I'd say and how I'd say it. Reject, and it learns that thread wasn’t worth answering.
- **Posts to [LinkedIn](https://www.linkedin.com/in/daria-cupareanu/):** it publishes my approved LinkedIn posts, text and image, on schedule, and tells me when they’re live.
- **Tunes itself weekly:** every Monday it reads all my edits from the week and rewrites its own instructions and skills to sound and think more like me, a small kind of self-learning.

The whole thing is just a folder of plain text files. Here’s the GitHub repo:

![The GitHub repository for my Claude Code automation OS, showing the heartbeat routine, the orchestrator with tasks.json, one folder per workflow, and the shared folder holding voice, audience, and the wiki.](https://substackcdn.com/image/fetch/$s_!c8ct!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F8026f9dc-6a4e-43e8-bd8b-4ba86664ebbb_735x1020.png)

The Claude Code AI agent repo — the whole system as plain text files.

And here’s that folder working. One heartbeat run reporting in, a Reddit reply waiting for my approval, and a LinkedIn post it published for me:

![My Claude Code automation system working in Slack: the heartbeat's run summary, a drafted Reddit reply awaiting my approval, and a confirmation that it auto-posted to LinkedIn.](https://substackcdn.com/image/fetch/$s_!KdZb!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F7a05a162-0979-463e-8bf0-377c551ab796_2075x2806.png)

My Claude Code automation system working in Slack: the heartbeat's run summary, a drafted Reddit reply awaiting my approval, and a confirmation that it auto-posted to LinkedIn.

This happens whether I’m at my desk, in line at the market, or on [vacation](https://aiblewmymind.substack.com/p/3-automations-i-built-to-make-returning). The system runs on Anthropic’s computers, not mine.

My laptop can be off for a week, and the drafts keep landing in my Slack, the new articles keep getting filed, and the posts that are safe to publish keep going out on their own.

My phone (and Slack) became the control panel.

---

## How I’m growing the system

What you just saw is where the system is right now. It’s been running for over a month, and the hours it saves every week are the smaller win.

The bigger one: **it got me doing work I’d avoided for months**.

I knew Reddit mattered for growing this newsletter and for getting indexed by LLMs. I knew the same about consistent LinkedIn posting. I just dreaded both, so the work stayed undone.

Now it happens daily, because the part I dreaded belongs to the system and the part that needs me takes minutes.

> That became my golden rule of automation: start with the tasks you dread. Automating work you’d do anyway saves you hours. Automating work you keep avoiding gets it done at all.

The whole system grew out of that one idea and I still have a long list of dreaded things waiting their turn.

### Why I add one workflow at a time

But I’m in no rush to clear that pipeline. The whole system grows slower than my ambition, and that’s deliberate, because I’m a perfectionist about what comes out of it.

What makes it slower than usual is that the work itself is new to me. I’m not automating something I’ve done for a long time. I’m still learning distribution as I go, finding my voice on each platform, seeing what lands on Reddit versus LinkedIn versus X. I have to get good at it by hand before I can teach the system to do it like me.

My [Instagram carousels](https://aiblewmymind.substack.com/p/claude-instagram-carousel-skill) are a good example. The setup is all there: each article is saved with its images embedded in the HTML, so the system could take a new one and build realistic carousels on its own. The visuals come out great. The copy is where I’m not consistently happy yet and I won’t hand the whole thing over, publishing included, until I can steer it reliably.

> **That’s the pattern for everything here:** I do a task by hand long enough to learn how Claude handles it and where my role can safely shrink, then I let the system take it over, review its drafts, and build the next piece when it’s ready.

### The bigger plan

It started with repurposing my own articles, because that was the easiest place to begin. I already have months of [content](https://aiblewmymind.substack.com/archive) that never sees the light of any platform beyond Substack, so there was a backlog just sitting there, waiting to be put to work.

But repurposing is only one direction. I want the system to grow on both sides of it, getting more out of what I’ve already written and helping me create new content from scratch:

- **Feed it before I write.** A research layer that comes earlier, surfacing what people are asking, what nobody has answered (well), what’s going viral, and the cool things worth getting inspired by or resharing, so my ideas come from real signals. Amplifiers already pulls [live data](https://aiblewmymind.substack.com/p/ai-research-tools-claude-chatgpt), and it has research workflows I can plug straight in, like my [content research workflow](https://aiblewmymind.substack.com/p/ai-content-research-workflow) and a [news-tracking system](https://aiblewmymind.substack.com/p/automate-newsletter-with-ai), with more I can keep building. That gives me a steady source of inspiration for new content and pushes the system past repurposing what I’ve already written.
- **Reach more platforms.** Get onto [X](https://x.com/dariacupareanu), where I’m starting from scratch. Fully automate the Instagram, Facebook, and Threads repurposing I still do 20% by hand. Start reposting articles to X (maybe?).
- **Spin [lead magnets](https://aiblewmymind.substack.com/p/create-lead-magnets-with-claude-skill) out of my content.** Pull free guides and resources from my own articles (using my [brand skill](https://aiblewmymind.substack.com/p/how-to-create-claude-brand-skill)), then post them across Instagram, LinkedIn, and X. Wire in ManyChat so when someone comments to get one, the system delivers it and handles the conversation, all from Claude, instead of me setting it up by hand after every post.
- **Turn some of it into products.** Package articles into paid products on [Gumroad](https://dariacupareanu.gumroad.com/), for readers who don’t want a subscription but would happily unlock one good thing.
- And I could keep going.

For all of that to run on its own, in the cloud, while I’m asleep, it had to be built somewhere specific.

---

## Why I built this in Claude Code, not Cowork

This isn’t the Cowork OS with a few extra folders. It’s a second system, in its own folder.

The difference is the role I play. In the Cowork OS, I’m in the middle of everything, deciding each step. This one runs in the cloud on a schedule and pulls me in only for the parts that need my [judgment](https://aiblewmymind.substack.com/p/i-dont-want-ai-to-replace-my-mind).

And the cloud part is the technical reason this had to be Claude Code. Cowork has [scheduled tasks](https://aiblewmymind.substack.com/p/claude-cowork-scheduled-tasks-6-ways) too, and I use them, but they run on my computer, with the app open.

Claude Code has [Routines](https://aiblewmymind.substack.com/p/claude-code-routines-tutorial): scheduled tasks that run in Anthropic’s cloud, so one fires with my laptop closed and me on a beach. Without that, a system that works while I sleep wouldn’t exist.

I keep the two separate on purpose. The Cowork OS is stable, the work I’m hands-on with every day and depend on. This one changes every week, a constant loop of iteration where I hand over a little more each time. That handover takes more than trust. It takes building each skill and workflow until the output is good enough that I'm comfortable letting it go.

---

**Everything below is for premium readers**: the full breakdown of all six automations, the folder structure and memory files, the engine, the internal wiki, the self-learning loop, and my watch-out checklist, so you can start building your own. [Upgrade here](https://aiblewmymind.substack.com/subscribe).

![Hand-drawn map of a Claude Code AI agent that automates content distribution — turning each new article into Reddit and LinkedIn posts across six cloud automations that run while I sleep.](https://substackcdn.com/image/fetch/$s_!7KOL!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F7ed675d7-7e9d-4764-9ad0-16f4c38198da_1122x1402.png)

Hand-drawn map of a Claude Code AI agent that automates content distribution — turning each new article into Reddit and LinkedIn posts across six cloud automations that run while I sleep.