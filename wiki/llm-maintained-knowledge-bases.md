LLM-maintained knowledge bases replace one-off retrieval with a persistent, interlinked markdown wiki that compounds over time: raw sources stay immutable, the agent updates the wiki layer, and the schema tells the agent how to ingest, query, cross-link, and maintain the system.

# LLM-Maintained Knowledge Bases

## Core Pattern

The main idea from `llm-wiki` is that a personal or team knowledge base should not rely only on retrieval at question time. Instead, an LLM agent reads raw sources once, compiles durable pages, links related concepts, flags contradictions, and updates existing pages as new sources arrive. This makes the wiki a persistent artifact rather than a temporary answer.

The architecture has three layers:

- Raw sources: immutable files that remain the source of truth.
- Wiki: agent-maintained markdown pages with summaries, concept pages, comparisons, and cross-links.
- Schema: instructions such as `AGENTS.md` that define conventions, page types, maintenance rules, and workflows.

This vault already follows that model: `processed/` is immutable, `wiki/` is AI-maintained, and `AGENTS.md` defines the topic-page and index rules.

## Operating Loop

The workflow has three recurring operations:

- Ingest: read new sources, summarize them, create or update relevant pages, add links, and update the index.
- Query: answer questions from the wiki first, then optionally file useful answers back into the wiki.
- Lint: periodically look for stale claims, thin pages, missing links, orphan pages, and concepts that deserve their own pages.

This links directly to [[agent-skills-and-agent-native-tools]] because the agent needs repeatable skills and local tools to keep the wiki consistent.

## Wiki Builder Plugin

The Wiki Builder source describes a Claude Code plugin that turns this pattern into a scaffolded workflow. It creates a folder structure, local config file, prompt templates, maintenance log, and starter index. The plugin supports flavors such as research, paper, domain, product, person, organization, and project, so the same pattern can be adapted to different knowledge-base types.

The important implementation lesson is not the specific Claude plugin, but the productized workflow: setup should be repeatable, provenance should be explicit, and useful answers should have a place to land. At small and medium scale, this markdown-first approach can outperform heavier RAG setups because the synthesis has already been compiled.

## Source Summaries

`processed/llm-wiki.md`: Andrej Karpathy's gist argues for persistent LLM-maintained wikis as an alternative to plain RAG. The key difference is accumulation: the LLM updates entity and concept pages over time instead of rediscovering chunks on every query. It also recommends index and log files, optional local search tools, and periodic linting.

`processed/Wiki Builder A Claude Code Plugin for Building LLM Knowledge Bases.md`: DAIR Academy presents Wiki Builder, an open-source Claude Code plugin that scaffolds an LLM wiki with config, prompts, logs, raw sources, and compiled pages. It frames the plugin as removing setup friction from the ingest/query/lint loop, with provenance and local configuration as core design requirements.

## Related

- [[agent-skills-and-agent-native-tools]]
- [[ai-marketing-automation-workflows]]
- [[social-media-competitor-intelligence]]
