---
title: "Now we have a timeline of the OpenAI accidental attack against Hugging Face"
source: "https://simonw.substack.com/p/now-we-have-a-timeline-of-the-openai?utm_source=post-email-title&publication_id=1173386&post_id=210294481&utm_campaign=email-post-title&isFreemail=true&r=8o4uhp&triedRedirect=true&utm_medium=email"
author:
  - "[[Simon Willison]]"
published: 2026-08-06
created: 2026-08-13
description: "Plus One-shotting a Raccoon Heist game using Claude Fable 5, and a big new LLM release"
tags:
  - "clippings"
---
In this newsletter:

- One-shotting a Raccoon Heist game using Claude Fable 5
- New release of LLM adds support for reasoning traces, OpenAI Responses, server-side tools, and smarter logging

#### Setting Claude Code for web up to use GitHub Pages

A frustrating thing about Claude Code for web is that it can be hard to test what it’s working on while it’s still working.

I’ve been using GitHub Pages to work around that limitation, and found it to work really well.

Here’s my process:

1. Create a new repository for the project at [https://github.com/new](https://github.com/new) - this can be public or private, the trick works equally well for both.
2. Start a Claude Code for web session, in the Claude iPhone or Desktop apps or in the browser at [https://claude.ai/code](https://claude.ai/code)
3. Tell Claude what to work on, and encourage it to commit an `index.html` page as quickly as possible. This will create a branch with a name like `claude/3d-raccoon-heist-game-50n293`
4. Navigate to the Settings -> Pages area for the repository (`github.com/simonw/raccoon-heist/settings/pages` in my case), select “Deploy from a branch”, pick the branch name, and hit Save.

That’s all it takes! Within about 30 seconds of each push the latest content will be visible at `yourname.github.io/your-repo/`.

If you do this with a private repo, anyone who can guess the name of the repo will be able to view the published content. I don’t worry much about this myself.

