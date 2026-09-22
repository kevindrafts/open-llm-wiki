Internal tool platforms give a team a shared place to build, run, and revise small apps with hosting, storage, authentication, and agent access already connected. Val Town's accounts of Shopify Quick and its own self-building Slackbot show how this can shorten the path from a team conversation to a working tool, while leaving ownership, permissions, and production reliability as separate concerns.

# Internal tool platforms and collaborative agents

## A shared home for small tools

Pete Millspaugh's June 22, 2026 article describes Shopify Quick as an internal service where employees upload HTML and assets and receive a secure company URL. The account also describes APIs for data, files, LLMs, and websockets. These are Val Town's descriptions of Quick, rather than an independent evaluation of Shopify's platform.

The same article presents Val Town as a hosted option for experiments and internal tools. Each app is a folder of code, called a val, with a live URL. The source describes a Deno runtime, SQLite, S3 blob storage, Slack and Google connectors, LLM APIs, and execution through HTTP, manual runs, MCP, cron, or email. Val Town claims edits deploy in about 100 milliseconds. The useful pattern is that an agent can publish and revise a running tool through the same interface it uses to write code.

This extends the Growbots deployment example in [[agent-skills-and-agent-native-tools]] and [[ai-marketing-automation-workflows]]. Shared hosting removes repeated setup work across many small tools. Examples in the article include email-based publishing, preorder tracking, voice demos, and a personal assistant with scheduled jobs.

## Building from the conversation

Charlie Molthrop's August 11, 2026 account describes connecting a Claude Slackbot built with the Vercel AI SDK to Val Town's MCP server. The bot could read, write, run, and query the team's tools. Because its own code lived in the same organization, it could also edit itself.

The team used Slack mentions to request a UI fix, merge a duplicate lead, and change the bot. An hourly digest helped teammates follow the edits. The distinctive workflow is shared context: the discussion, request, and visible result stay where the team already collaborates. A teammate no longer has to copy a planning thread into a separate coding session.

The source focuses on quick internal tools and shareable artifacts where stability is less critical. It also argues that tools used and revised in Slack get faster feedback, with technical teammates present in the same conversation. This is a concrete example of [[software-factories-and-agent-loops]], though the account does not establish a production-grade review or testing system.

## Permissions and capability changes over time

The June article describes Val Town as public by default, with OAuth middleware and paid private-code options. It says websockets were unavailable and SOC 2 work was underway. Those are dated source claims, not a current capabilities checklist.

The later Slackbot clipping includes an update saying Val Town Access is live for paid organizations, with per-app viewing and editing permissions. The clipping does not date that update separately. Keep that later access model alongside the June account rather than treating their descriptions as simultaneous defaults.

Synthesis: a bot that can edit its own code needs an identifiable owner, recoverable versions, and access limited to the work it should perform. Shared chat makes changes visible, but visibility alone does not verify correctness or authorize every participant to change every tool. The caller-permission model discussed in [[agent-skills-and-agent-native-tools]] remains relevant.

## Project opportunities

An opportunity suggested by these sources is a managed internal-tool service for a narrow business workflow, such as lead qualification, proposal preparation, or a team dashboard. Reuse the hosting and access setup, then charge for maintaining a useful workflow. This connects to [[service-business-ai-consulting]] and [[micro-saas-and-bootstrapped-apps]]. It is an inference from the examples, not evidence of customer demand or a proven recurring revenue model.

## Source summaries

- `processed/What if every company had an internal hosting platform like Shopify’s Quick.md`: Val Town's June 2026 comparison with Shopify Quick, including deployment, runtime, storage, triggers, examples, and platform constraints.
- `processed/Our Self-Building Slackbot.md`: Val Town's August 2026 account of a Slackbot with MCP access to its own code and team tools, shared editing in Slack, and a later access-control update.

## Related

- [[agent-skills-and-agent-native-tools]]
- [[software-factories-and-agent-loops]]
- [[ai-marketing-automation-workflows]]
- [[service-business-ai-consulting]]
- [[micro-saas-and-bootstrapped-apps]]
