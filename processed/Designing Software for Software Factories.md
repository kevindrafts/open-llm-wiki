---
title: "Designing Software for Software Factories"
source: "https://blog.sshh.io/p/designing-software-for-software-factories?utm_source=post-email-title&publication_id=1943298&post_id=201891732&utm_campaign=email-post-title&isFreemail=true&r=467kkp&triedRedirect=true&utm_medium=email"
author:
  - "[[Shrivu Shankar]]"
published: 2026-06-13
created: 2026-06-15
description: "Reflections on turning software engineering into agentic loops."
tags:
  - "clippings"
---
Article voiceover

0:00

\-17:12

Since my [AI-powered Software Engineering](https://blog.sshh.io/p/ai-powered-software-engineering) (2024) post, the overton window has shifted from whether AI can even aid software development in any way to what parts of it even remain human. At work, we’ve been building out what I call our “software factory”, and this post I wanted to chat through how it’s come together, the hardest parts we’ve run into, and what actually works.

## What is a software factory?

While it's becoming a bit of a buzzword with different definitions depending on who you ask — I define it as an AI-driven system and the organization that surrounds it that solutions, designs, builds, tests, and deploys software products. If you've read [The Transposed Organization](https://blog.sshh.io/p/the-transposed-organization), a "software factory" is just one of many 'loops' a modern AI native company must develop as a core part of EPD (eng, product, design) operations.

![](https://substackcdn.com/image/fetch/$s_!Obi8!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3be44370-5b90-4b88-a1fc-4e514679db2f_1536x1024.png)

The software factory absorbs the raw, unscoped stream of customer requests and resolves it into shipped software — with the human entering (For now) at exactly one point. Style inspired by background-agents.com.

IMO a full Software Factory must:

- Be able to operate on the raw distribution of customer generated RFEs and bug reports as input. It does not count if a PM needs to scope every ticket or an engineer needs to break the solution into smaller pieces.
- Only require humans for off-ramping (pressing the big red stop button) and review at certain stages. It does not count if there’s an explicit “pairing” step anywhere in the loop or [if the system runs on an individual’s laptop](https://background-agents.com/).
- Feed every review back into the system such that the review gate deprecates itself over time. It does not count (or work well) if reviews only apply to a single instance of software generation.
- Be able to run many requests through the loop concurrently, not one ticket at a time. It does not count if requests must be serialized because stages share mutable state (one test/staging env, one branch, one deploy slot) or if throughput is capped by a human-owned resource rather than by spend.

You measure the first order [^1] efficacy of a software factory typically via:

- Cycle time — The wall time for customer request to deploy (or per stage).
- Review volume — How much feedback is given across stages on AI-drafted outputs (per stage).
- Off-ramps — How often a request gives up and falls back to a human-in-the-loop development process (per stage). This can also be reframed as %-factory applicable.

## Seeding a software factory

At the risk of being less useful, I'm going to focus this post on high level tips given you already have some semblance of a software factory setup. Exactly how one works, how end-to-end it goes, whether it's home grown or purchased is really going to vary company by company. I've mostly seen two buckets:

- AI-native startups
	- Typically have a lot more room to build an AI-friendly tech stack and the contractual and compliance risks are typically lower. The downside is they can't afford to have a dedicated AI dev ops team to build any sort of "software factory platform".
		- **Recommendation**: If Claude picked your stack, it's very likely you can actually just find something to buy as like a factory-as-a-service. It's also critical to set the expectation up front: with no central platform team, every engineer is the software-factory architect for the systems they own.
- Enterprise software companies (me irl)
	- Moving to AI-friendly stacks becomes quite a large migration and the appetite for risk (often around service stability) is low to none. They do and have started software factory platform like teams.
		- **Recommendation**: Today at least, it's likely easier to build than buy and do this via one more dedicated AI-readiness platform teams. A common failure mode is buying something with a low ceiling that actually can't get you to the same compliance and level of testing needed to actually ship a "real" feature. Another option, for those bold enough, is to fork all new products onto an AI-native stack but this only really pays off if it's isolated enough to not share the same compliance and stability risks.

### Don’t start a product or platform as a software factory

Another perhaps counterintuitive observation is that software factories work best when there's patterns, contracts, and scaffolding to match against. Pure greenfield projects don't have this and pre-maturely factorifying has led to code-bloat and a reduced ability to understand the project as it evolves. Another risk is just lack of data for how the project evolves and will evolve — a factory works best when the system itself is "roadmap aware". Brownfield projects on the flip side are often complex, unintuitive, with significant undocumented behavior (at least from a coding agents POV). With or without AI, a well-designed brownfield project is actually the ideal place to apply a factory.

- If you are just starting a project (greenfield), I’d build the first 3-10k LoC pairing with a coding agent and same with the first few E2E features. At modern development time scales this phase should take around ~1-3 weeks. Product-prototype loops likely take longer and I consider those out of scope — for the most part those are just vibe coded demos that become an input to the actual production project.
- If you are working with a mega-complex enterprise service (very brownfield), I'd apply these strategies:
	- (1) Make all changes testable by an agent. To the deepest extent physically possible, an AI, with no human in the loop, should be able to tell you if a given PR breaks service functionality.
		- (2) In a manual loop, prompt a coding agent to build out an upcoming feature (don’t steer, just let it both design, implement, and test e2e). Adjust the code organization and/or sprinkle markdown files until this works.
		- If (1) or (2) are infeasible at scale you should just rebuild or decompose and rebuild a subcomponent of the service to make those both true. I realize that's non-trivial but I'll make the claim that often \[# eng hours to do this - eng hours reduced by having a factory\] « \[# of eng hours to continue building features with engs in the loop\]

### Understand and maintain factories with contracts

You can absolutely build and understand tens of thousands of lines of code shipped a day provided you have the right "contracts" for how those projects should be developed. Contracts can take a variety of forms (schemas, typing, etc) but typically my focus is on markdown ones (often AGENTS.md or.md files co-located and referenced with the code).

A good markdown contract:

- Makes predictions about how the future of the project will evolve (what I mean by “roadmap” aware)
- Makes it clear how to validate changes and what can’t be validated
- Does not change 90% of the time feature to feature (e.g. % of future PRs that modify this file is very low)
- Establishes clear complexity and risk boundaries (e.g. x are examples of things that are easy, y are examples of things that are hard or risky)
- Is forward-tested on roadmap tasks (e.g. throwaway vibe code, with no steering, the next 3 items on the roadmap, if they are way off then the contract is bad)
- Defines key context an agent won’t see (e.g. often product and audience context, ~ a cache of “what should the agent know that’s not in the codebase”)

The “ [I wrote a markdown file and my agent still sucks](https://arxiv.org/abs/2602.11988) ” crowd often include 0 of 6 of these because often the easiest (but wrong) thing to do is to just use the markdown as a summary of the project or as a storage for one-off tech specs.

Here’s some snippets from util skills I have used for writing these [^2]:

```markup
- Principles are the choices about what this service is and isn't, what it optimizes for, and what trade-offs it accepts. They are the decisions that *produced* the current code shape, not summaries of that shape. A good test: if you replaced every file in the directory with a different implementation that respected the principle, would the principle still read true?
- Where does stuff live? The high-level layout a reader needs to know to *find* things — what kinds of files exist, what naming conventions disambiguate them, where shared helpers live, what subfolders mean. This should stay true across normal feature work; you should NOT have to edit it on every code change. Do not enumerate files — for the live file list, point the reader at a command (e.g., \`ls <dir>\`, \`tree <dir>\`, \`find <dir> -name '*.py'\`) that returns the current state.
- What's the architectural contract? Which invariants must a change respect, and which boundaries — when crossed — mean this isn't a routine change but an architectural decision. These are the joints a reviewer looks for; name them by the symbols, interfaces, or middleware that anchor them.
- Which categories of change can a single engineer ship after a normal PR review, vs which categories likely require a design conversation before they're written.
```

An interesting question to think about — I would argue that often SWE1-2 or even SWE3 don’t actually have the full context to actually answer and validate correctness on all 6 bullets (some parts of this being experience-related but more so as an organizational artifact). In that case who writes the contract? It has to be owned one of two ways: by a group (a contract design review meeting?), or by a single “ *[transposed](https://blog.sshh.io/p/the-transposed-organization)* product engineer” who owns the contract end to end.

## Testing, testing, testing

Agents being able to run E2E tests is still extremely underrated among engineers. I think a lot of folks still think the ROI of agents being able to run tests comes from the fact that it saves them as the human from just running the test command and so given the priorities of "make agents run my test" vs "build new feature and I run the test command" it doesn't feel like it has to happen this sprint.

The reality is that today's models can write surprisingly correct and complex software given a well-designed test harness. I like to think it's somewhat analogous to "reward" functions in reinforcement learning — define a function that maps a solution to a score and let the agent hillclimb that until it maximises it. The crux then becomes how do you actually define both:

- What does it mean, holistically, to be correct? From unit tests, to integration tests, to play tests, to alignment with the project “contract”.
- When not correct, how do we provide enough signal to the agent to actually work towards a higher score efficiently? From stack traces, to well crafted subagent judges, to browser-use screenshot verification.

In other words, in this new world of AI native factory development, the manual eng effort to build any given feature should actually come from the effort to setup a test harness and contract rather than build the feature itself. If you are doing it right, your roadmap should look like:

![](https://substackcdn.com/image/fetch/$s_!IxgF!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc50be44b-6969-4fce-8451-a895c97b24d0_1536x1024.png)

The effort inversion: human work front-loads into the harness and contract, then features become mostly tokens.

### Testing in tiers

My mental model is often:

- Linting, typing
- Unit tests
- Security and compliance scanning
- Single service integration tests (mock/shim everything else)
- Multi-service integration tests
- Multi-service integration tests from a product surface (click buttons on the actual UI)
- Rollout monitoring (post code-review if production, verifying logs and metrics against expected set)

You can implement each tier as an MCP or CLI the agent runs after completing the tier before [^3]. It’s critical the agent controls the full testing loop — a common design mistake I see is making these tiers human-gated stages (e.g. a human is required for a test deploy) because this completely collapses the autonomous cycle time of the factory. Another common mistake is making the tests too rigid (e.g. hardcoded playwright test) vs giving the agent enough flexibility to dynamically determine the test plan and actually change the test plan through the test loop. The goal is to define a set of test tiers that if passes (along with some contract review subagent signoff) — you have high confidence the factory produced a high-quality compliant feature.

Three additional recommendations:

- Give your agents a dumping ground for verification scripts (e.g. every project gets a scripts/ folder). Just let it dump stuff there and let it decide when a script no longer works and when to just write a new one.
- Let your testing agent be a customer. Tests don’t have to be purely “did x thing work”, they can also be “would this be a delightful experience for x audience”. As models get better you can often get away with more abstract and end-user meaningful definitions of correctness.
- Give your agents the ability to build test environments. We have started using an interesting strategy (worthy of its own blog post) for multi-service integration tests. Instead of trying to maintain or bootstrap entire test/staging instances of our platform (which is both hard and extremely costly), we let the agents all access a shared test env with the ability to respawn certain services dynamically and re-route their own test’s traffic to those. If AuthAPI is broken in staging because of another agent, our agent will spawn a new node from a previous Git SHA and alias its tests against that.

![](https://substackcdn.com/image/fetch/$s_!6a9r!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff2946bca-c765-4b9e-a6ef-3974563c0b2e_2560x1440.png)

Don't rebuild the world. When a shared service breaks, an agent spawns one node from an old SHA and reroutes only its own traffic.

## Off-ramps, observability, and feedback loops

Factories won't be able to cover 100% of all feature requests nor will they always produce perfect code but when they don't it's fundamental that those failures feedback into the system. I see typically two algorithms for this depending on whether a human is gating a stage (for QA and/or compliance reasons).

**Human-reviewer (e.g. post-code generation and testing, pre-merge** [^4]**)**

1. If the implementation is completely off, provide the option to either divert completely to manual-mode or re-run the previous stage with some additional clarification (”let’s not touch auth.py, do this using the xyz framework”). The review rarely occurs on the raw artifact (the full diff) but on curated should-review highlights derived from the project contract and test-loop artifacts.
2. Store (agent traces, feedback) somewhere
	- In batch (on the order of a week), an agent pushes changes to markdown contracts and code to prevent that failure again. Often these are also human reviewed and aggregated over all feedback and failure modes.
		- In batch (on the order of rolling weeks to months), an agent pushes changes to markdown contracts and code with context on second order effects:
		- Factory stage costs and latency
				- Incidents, post-mortems, rollbacks
				- Online system logs and metrics
				- Product feedback and outcomes

**No human-reviewer (e.g. post-merge, rollout verification)**

1. Store agent traces somewhere
	1. In batch (on the order of rolling weeks to months), an agent pushes changes to markdown contracts and code with context on second order effects:
		- Factory stage costs and latency
				- Incidents, post-mortems, rollbacks
				- Online system logs and metrics
				- Product feedback and outcomes

Both paths share the long second-order loop; only the human-reviewer path adds immediate feedback encoding. And in practice, the second-order feedback PRs themselves always get detailed human reviews regardless of path, by the same person who wrote them originally. My attempts to get autonomous second order feedback factories working have so far resulted in [positive feedback slop loops](https://en.wikipedia.org/wiki/Positive_feedback).

The hardest parts here often come down to managing reviewer cognitive load and making feedback sticky (i.e. converting feedback given on a factory instance to a systematic pattern to adopt). I don’t really have a great answer to that besides “get good at writing contracts that make changes easy to review most of the time”.

## Some final takes

Overheard (quote + my take):

> “AI isn’t good enough for <insert factory stage that isn’t writing code: product decisions, designing tech specs from those decisions, complex trustable testing>”

At this point it’s mostly a skill, context, or stack issue — and those are within your team’s control. The models and harnesses are good enough for E2E SWE factories.

> “We don’t need human review in the software factory even for QA because we can apply more agents to fix the bugs they shipped super quickly”

I’m a big believer in “shift-left” philosophy which means problems are solved and mitigated as early in the loop or ideally out of the loop as much as possible. Shipping broken changes (even momentarily) is a recipe for getting out AI-engineered by a company that used AI to ship good changes faster and for getting stuck in situations where no one understands the system at any level of depth to know the difference between a good and a bad change.

---

[^1]: The first-order metrics are fairly easy to measure but they are not the full picture. Incidents, customer feedback, factory output related code reversions, etc. both help convert production into business outcomes.

[^2]: You can also just drop this entire blog post into claude to figure out next steps.

[^3]: Testing MCPs interfaces can actually be quite simple — exec\_bash\_in\_environment(). The complexity comes from doing this with the right data governance and security guarantees.

[^4]: Pull request review and merge is often a very natural checkpoint in a software factory for human review. It's both what gates correctness ("if code is merged it is deemed correct") and is used by compliance teams as a controls surface (e.g. SOC compliance). The artifact of this is that I do think we'll need to break the "changes should be of a certain size" contract as the PR becomes a unit of factory work over anything else.