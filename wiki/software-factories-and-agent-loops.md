Software factories and agent loops turn software work from one-off prompting into bounded systems that ingest requests, gather context, produce changes, verify them, learn from review, and run many work items concurrently; the durable advantage comes from contracts, test harnesses, observability, feedback encoding, and product judgment rather than from raw code generation alone.

# Software Factories and Agent Loops

## Core Idea

A software factory is an AI-driven system, plus the organization around it, that can turn raw customer requests, RFEs, bugs, and product signals into designed, built, tested, and deployed software. A loop is the smaller primitive inside that factory: goal, context, evaluation, and an agent that keeps working until the evaluation passes or the task off-ramps.

The distinction matters. Prompting asks an agent to do a task. A loop gives the agent a goal, the context it can fetch, and a way to check its own work. A factory composes many loops across product triage, design, implementation, testing, review, deployment, rollout monitoring, and feedback.

## Factory Requirements

The strongest factory definition sets a high bar:

- It accepts raw customer-generated inputs rather than only pre-scoped engineering tickets.
- Humans primarily review, approve, and off-ramp rather than pair continuously.
- Reviews feed back into durable contracts, tests, and code so the same failure is less likely later.
- Multiple requests can run concurrently without being bottlenecked by one human-owned branch, staging environment, deploy slot, or reviewer.

Useful first-order metrics are cycle time, review volume, off-ramp rate, and percentage of requests that are factory-applicable. The second-order metrics are more important over time: incidents, rollbacks, customer feedback, factory costs, latency, and whether shipped changes create product outcomes.

## Loops as the Primitive

PostHog's loop framing reduces agentic work to four parts:

- Goal: the loop needs a concrete outcome, such as fix this bug, get CI green, reduce benchmark latency, or remove flaky tests.
- Context: tools, skills, analytics, errors, memories, docs, traces, and customer signals should be fetchable as the loop runs rather than dumped all at once.
- Evaluation: tests, CI, evals, metrics, browser checks, LLM judges, benchmarks, logs, and product analytics let the agent verify progress.
- Agent: Claude Code, Codex, a cron-run harness, `/loop`, `/goal`, subagents, or a purpose-built platform executes the work.

Good examples include PR babysitters, bug fixers, flaky-test hunters, performance autoresearchers, and paper-cut loops that mine product data for small improvements. This connects to [[agent-skills-and-agent-native-tools]] because skills, MCPs, CLIs, cloud execution, and subagents are the practical interface layer for loops.

## Contracts Over Summaries

Factories need project contracts, often markdown files such as `AGENTS.md`, that make future work more reliable. A good contract is not a file inventory or one-off spec. It should capture stable principles, validation methods, risk boundaries, ownership rules, and context an agent cannot infer from code.

Strong contracts:

- Predict how the project should evolve.
- Explain what can and cannot be validated automatically.
- Stay mostly stable across normal feature work.
- Define architectural joints and complexity boundaries.
- Are forward-tested by asking an agent to attempt roadmap tasks without steering.
- Cache product, audience, compliance, and operating context that code alone does not reveal.

This overlaps with [[llm-maintained-knowledge-bases]] and [[design-systems-for-ai-built-products]]: markdown becomes operational memory when it constrains future agent behavior, not when it merely summarizes the present.

## Test Harnesses as Human Leverage

In factory-style development, human effort shifts from hand-writing every feature toward designing harnesses and contracts. A strong test loop gives the agent a reward signal it can hillclimb: stack traces, screenshots, browser states, integration results, product metrics, and reviewer feedback.

Useful verification tiers:

- Linting and typing.
- Unit tests.
- Security and compliance scanning.
- Single-service integration tests with mocks or shims.
- Multi-service integration tests.
- Product-surface tests that use the actual UI.
- Rollout monitoring against expected logs and metrics.

The loop weakens when a human has to manually provision every test deploy or when the test environment is one shared mutable bottleneck. Better patterns include agent-controlled verification scripts, dynamic test plans, browser-use screenshot checks, and per-test service routing when a shared dependency is broken.

## Feedback and Off-Ramps

Not every request should stay in the factory. If an implementation is badly off, the reviewer should be able to divert it to manual mode or rerun the prior stage with tighter constraints. The important part is making feedback sticky: traces, review comments, failures, and rollout outcomes should later become changes to contracts, tests, code organization, or workflow instructions.

Two loops matter:

- Immediate loop: human review catches a bad output and gives targeted feedback.
- Second-order loop: accumulated failures produce reviewed updates to contracts, harnesses, and architecture.

Fully autonomous second-order feedback can degrade into self-reinforcing noise, so high-leverage humans still need to review changes to the factory itself.

## Product Loops and Self-Driving Products

Software loops are not limited to engineering hygiene. Product engineers already run a manual loop: collect analytics and user feedback, build improvements, evaluate results, and repeat. Agent loops make that cycle more continuous, especially for bugs, UX paper cuts, conversion tweaks, and low-strategy improvements.

The phrase "self-driving product" should not mean autonomy from engineers. It means autonomy from explicit user instruction as the starting point. Humans still own direction, taste, empathy, risk boundaries, and major product calls. Agents can keep the 1% improvements moving.

## Source Summaries

`processed/Designing Software for Software Factories.md`: Defines software factories as AI-driven systems that ingest raw customer requests and produce shipped software with human review and off-ramps. The strongest lessons are contracts, roadmap-aware markdown, agent-controlled test harnesses, concurrency, off-ramp design, and feedback loops that update the system rather than only one PR.

`processed/Why we're bullish on loops.md`: PostHog frames loops as the practical unit of agentic work: goal, context, evaluation, and agent. It argues that better models, subagents, cloud execution, harnesses, and built-in loop commands make long-running agent work realistic, especially for PR babysitting, bug fixing, flaky-test cleanup, performance research, and product paper cuts.

## Related

- [[agent-skills-and-agent-native-tools]]
- [[ai-native-startup-strategy]]
- [[llm-maintained-knowledge-bases]]
- [[design-systems-for-ai-built-products]]
- [[ai-marketing-automation-workflows]]
