---
title: "Our Self-Building Slackbot"
source: "https://blog.val.town/slackbot-townie"
author:
  - "[[Charlie Molthrop]]"
published: 2026-08-11
created: 2026-09-08
description: "Experiments in multiplayer vibecoding"
tags:
  - "clippings"
---
On Friday, we made a self-building Slackbot. By the end of the day, it had us rethinking how we collaborate.

Earlier that afternoon, my teammate [Potluck](https://potluckmittal.com/) had a good idea, so I jokingly tagged Townie, the coding agent that lives on Val Town. Only, Townie wasn't actually on Slack! We were tantalizingly close though!

![Slack conversation: Potluck proposes an action button that opens a text-input modal. Charlie replies, “@townie, do your thing!”, notes the demo is close, and Potluck replies, “Yesss.”](https://dcm31--e5fa3a2090fa11f1ad2e1607ee4eb77e.web.val.run/images/5a96956c-76ad-42ab-8bed-860193bd083d.png)

How close? Thanks to our [ai-slackbot](https://www.val.town/x/templates/ai-slackbot) template, about five-minutes-close. In a few clicks, the template had me set up with a Claude Slackbot, powered by the [Vercel AI SDK](https://ai-sdk.dev/).

But it still couldn't ship Potluck's feature idea. It needed the ability to read, write, run, and query our internal tools (which live on Val Town).

Thanks to the [Val Town MCP](https://docs.val.town/guides/prompting/mcp/), that took 9 lines of code:

```ts
const mcpClient = await createMCPClient({
  transport: {
    type: "http",
    url: "https://api.val.town/v3/mcp",
    headers: {
      Authorization: \`Bearer ${token}\`,
    },
  },
});
```

And thus, a star was born:

![](https://dcm31--e5fa3a2090fa11f1ad2e1607ee4eb77e.web.val.run/images/3aa2b541-c62e-4475-8217-525da2eb26ef.png)

Here's the fun part: because "townie-slackbot" lives alongside the rest of our internal tools in our Val Town org, it can edit its own source code!

![](https://dcm31--e5fa3a2090fa11f1ad2e1607ee4eb77e.web.val.run/images/8ad8517a-7bc7-426b-a737-54bc5679ba16.png)

So the first order of business was a bit of self-brain surgery.

![Slack conversation: Charlie tells @townie-slackbot, “Upgrade yourself to Opus 5!” The bot replies that it is now running on Claude Opus 5 and future messages will use the new brain.](https://dcm31--e5fa3a2090fa11f1ad2e1607ee4eb77e.web.val.run/images/e2ba5073-21da-44f0-844b-4239294eb566.png)

From there, things moved pretty quickly. Potluck tagged Townie on a UI bug. I had it merge a duplicate lead. And of course, there were plenty more instances of Townie editing itself. Steve set up an hourly digest to catch the changes as they rolled in. Everyone was working in front of each other, never leaving Slack.

![](https://dcm31--e5fa3a2090fa11f1ad2e1607ee4eb77e.web.val.run/images/51d9fe40-3ab7-4411-b1ae-9b9ff6b22aa2.png)

### Multiplayer Vibecoding

![mutliplayer-vibecoding-even-narrower](https://dcm31--207685866ff511f1a5b41607ee4eb77e.web.val.run/art/mutliplayer-vibecoding-even-narrower-hi)

None of these changes were particularly groundbreaking. We ship stuff like this all day from Claude Code or Codex (or [our phones](https://x.com/CharlieMolthrop/status/2080276492836024787?s=20)!) with the [Val Town Plugin](https://docs.val.town/guides/prompting/plugin). But for the first time, we were showing our work. It felt like the [future of collaboration](https://www.youtube.com/watch?v=ClWD8OEYgp8). And it was fun!

We're all beginning to recognize that point when a Slack thread among humans starts resembling a `plan.md`. In the old times (a week ago), that meant electing a designated [meat proxy](https://gruhn.me/blog/2026-08-03/) to boot up Claude and paste all the context. Now with our new Slackbot, the prototype is just a Townie tag away.

### So we're all vibecoding from Slack now??

Maybe not on prod. But vibecoding is pretty great for quick internal tools where maintenance and stability aren't mission critical. Like whipping up a shareable [artifact](https://www.val.town/x/templates/team-artifacts) for your team to review. Or spinning up a [lead qualifier](https://www.val.town/x/templates/leads) to post to Slack on new signups.

Many of your ideas and planning start in your messaging channels. If lightning strikes in Slack, you might as well bottle it there.

Vibecoding from Slack also solves one of the bigger issues with internal tools: they need a tight feedback loop to stay fresh. If the tool is used in Slack and is edited directly from Slack, that's about as tight as it gets! [The end-user can do a lot more of the "programming"](https://en.wikipedia.org/wiki/End-user_development). Sure, it's important that your more technical teammates are also in that loop. But guess what, they're in Slack too.

### Just one more tool, bro

Got tool fatigue? A Slackbot on steroids might help. Tool-switching is context switching, and it fragments your workflows. Why not double-down on the one tool that ain't goin anywhere? Am I claiming that a Fable Ultracode Slackbot might just be one of the four horsemen of the SaaSpocalypse? I'm not *not* saying that...

## Why Val Town?

Confession: I didn't invent the concept of a powerful AI that can do a lot of things... There are many folks trying pitching you a superbot/claw/Claude Tag/pi/Hermes.

So why should your company's superbot build itself and the rest of your tools on Val Town?

### Instant deploys; We do the hosting

Vals (our name for apps) redeploy in 100 milliseconds on any edit. You don't have to worry about hosting it or keeping it alive. We keep your bot instantly deployed at a live url. You focus on the business logic.

### The bot lives where it builds

No more chasing around different tools. The bot itself is a val. Each tool it builds is a val.

### Features for your whole team

We've got version control, [scoped databases](https://blog.val.town/scoped-databases), and [coding harness plugins](https://docs.val.town/guides/prompting/plugin) for your engineers. We've got [Townie AI](https://blog.val.town/townie-v5) in the sidebar of your vals for when your less technical team members want to learn or make changes.

![](https://dcm31--e5fa3a2090fa11f1ad2e1607ee4eb77e.web.val.run/images/5fe5870a-052c-4c70-9dc5-0afbb92424e3.png)

This is a val.

We're proud that some of the most cracked engineers we know love Val Town. We're also proud that some of our most enthusiastic users consider themselves non-technical.

### Secure collaboration by default with Val Town Access

Auth is one of the most annoying parts of internal tools. We've taken care of that for you. Like Google Docs, each val has customizable permissions. Easily manage who can see and build what:

![](https://dcm31--e5fa3a2090fa11f1ad2e1607ee4eb77e.web.val.run/images/460e380f-e61b-4979-b391-f8546caa2af4.png)

Update: [Val Town Access is live](https://blog.val.town/access) for all paid orgs!

~~Val Town Access is currently in beta. [Let me know](https://charlieslackchat.val.run/) if you want early... access.~~

And the last reason your superbot should live on Val Town? We already made it for you:

## Your very own self-building Slackbot.

![](https://dcm31--e5fa3a2090fa11f1ad2e1607ee4eb77e.web.val.run/images/caec8e98-0438-4595-8338-059628e57b31.png)

Just remix [this val](https://www.val.town/x/templates/townie-slackbot) into your Val Town org (create one if you're new), and follow the steps. Here's Potluck getting set up with a self-building slackbot in **less than four minutes**:

<video src="https://dcm31--e5fa3a2090fa11f1ad2e1607ee4eb77e.web.val.run/videos/slackbot-setup-potluck.mp4" controls=""></video>

Prefer me to walk you through it? Feel free to [grab some time](https://charlieslackchat.val.run/). We can set up a Slack connect and build it together. I won't hang up until your whole team can vibecode artifacts from Slack. Deal?

From there, you can [make your first dashboard](https://cleanshot.com/share/BhSHMYQ4) or [edit a shared artifact](https://cleanshot.com/share/MQJMFhGB).

And remember, if you want something changed about your bot, well, just tell it!

### Acknowledgements

Thank you to Steve, Potluck, and Townie for feedback on this post.

![](https://dcm31--e5fa3a2090fa11f1ad2e1607ee4eb77e.web.val.run/images/1bf2af62-5ba0-41c0-9217-dc2ed9ab1922.png)

the gang

[Edit on val.town](https://blog.val.town/source)

**We're hiring!**

Are you an infra engineer who cares about the joy of programming?

[View position →](https://www.val.town/careers)