Context compaction for coding agents is the harness discipline of pruning stale tool output, summarizing older turns, preserving a reconstructable audit trail, and managing a smaller working-memory budget than the model's raw context maximum so long-running sessions stay useful instead of rotting under their own transcript size.

# Context Compaction for Coding Agents

## Core Problem

Stateless coding-agent harnesses resend the entire conversation history on every turn: user messages, model responses, and tool results. In practice, context often grows fastest through file reads, shell output, logs, and scans rather than through the conversation itself. That creates a systems problem long before a user notices it. The harness needs a policy for what to keep verbatim, what to prune, and when to summarize older state so the next turn still fits and still performs well.

## Prune Before You Summarize

The strongest implementation lesson is that not all old context deserves summarization. Tool outputs are often the cheapest thing to discard because the agent can usually re-run a command or re-read a file later, and the original output may already be stale. A better pattern is to replace older tool output with an explicit placeholder that says it was removed and can be reacquired.

That creates a practical priority order:

- Keep the most recent user turns intact.
- Preserve recent tool outputs needed for the current task.
- Prune older tool outputs first.
- Compact older conversational context only after pruning fails to free enough space.

This is more robust than blindly summarizing everything, because summaries of giant command outputs often waste tokens while still losing detail.

## Own the Compaction in the Harness

The source argues against relying entirely on provider-side compaction features when they return opaque, provider-specific items that cannot be inspected or reconstructed later. A harness that owns compaction can store the original messages, the inserted summary, and the cut point in an auditable history such as `session.jsonl`.

That matters for several reasons:

- Portability across model providers.
- Human-debuggable audit trails.
- Recovery after crashes or partial failures.
- The ability to replay pruning and compaction operations in sequence.

This aligns with the broader wiki pattern in [[llm-maintained-knowledge-bases]]: durable systems prefer explicit files and reconstructable state over hidden platform memory.

## Working Budget Versus True Limit

One of the most useful distinctions in the source is that the model's true context window and the harness's chosen working budget should not be treated as the same thing. A harness may intentionally compact or reject earlier than the provider's maximum because performance degrades as context grows, caches get invalidated, or prompt quality falls before the hard limit is reached.

So the system needs two separate values:

- The factual maximum context accepted by the model.
- The policy budget the harness is willing to use before pruning or compacting.

Separating those prevents a misleading "context full" story when the real issue is that the harness has exhausted its self-imposed quality budget, not the model's technical maximum.

## Failure Modes Matter

Compaction is not a harmless cleanup step. It is a lossy transformation that can fail in several ways:

- The compaction request itself may be too large.
- The summarizer may return something empty, too long, or truncated.
- The summary may technically succeed but fail to reduce the transcript meaningfully.
- A retry loop can thrash if the same bad prompt keeps being resent.

The practical defenses are to truncate the compaction prompt view without mutating the actual conversation, remove whole messages only as a last resort, retry with smaller budgets, and discard summaries that do not materially shrink the session.

## Compaction as a Commit

Another useful systems idea is to treat compaction like a commit. The harness should append the compaction record to durable history first, then swap the in-memory conversation to the compacted view. If the process crashes between those steps, reconstruction from the log can still recover the right state.

This makes pruning and compaction part of the system's event log rather than invisible in-memory tricks. The result is more debuggable and more trustworthy for long-running autonomous work.

## Strategic Lesson

Better models and more tools do not remove the need for memory policy. In fact, tool-rich coding agents need context compaction more urgently because they generate so much transcript material on their own. Reliable agent systems therefore need not just skills, CLIs, MCPs, and test harnesses, but also explicit rules for transcript pruning, summary creation, auditability, retries, and cache-aware timing. This connects directly to [[agent-skills-and-agent-native-tools]] and [[software-factories-and-agent-loops]].

## Source Summaries

`processed/The Hard Parts Of Context Compaction.md`: Explains how a coding-agent harness can manually compact long conversations by pruning stale tool output, summarizing older prefixes, storing reconstructable compaction records, separating working budgets from true context limits, and defending against failed or useless summaries.

## Related

- [[agent-skills-and-agent-native-tools]]
- [[software-factories-and-agent-loops]]
- [[llm-maintained-knowledge-bases]]
