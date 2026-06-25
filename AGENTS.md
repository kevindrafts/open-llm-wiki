# Knowledge Base Schema

## What This Is
A personal knowledge base about interesting businesses, AI tools, product ideas, software patterns, marketing workflows, and project opportunities.

## How It's Organized
- `raw/` contains new, unprocessed source material.
- `processed/` contains source material that has already been ingested. Do not modify these files.
- `wiki/` contains the organized wiki. AI maintains this entirely.
- `outputs/` contains generated reports, answers, and analyses.

## Wiki Rules
- Every topic gets its own `.md` file in `wiki/`.
- Every wiki file starts with a one-paragraph summary.
- Link related topics using `[[topic-name]]` format.
- Maintain an `INDEX.md` that lists every topic.
- When new raw sources are added, update the relevant wiki articles.
- After sources in `raw/` are ingested, move them to `processed/`.

## My Interests
- AI tools and automation workflows
- Interesting bootstrapped, vertical SaaS, and services businesses
- Marketing, distribution, and sales systems
- Project ideas I could build, adapt, or study
- Patterns that connect multiple companies, products, sources, or markets

## Reference
- This is the prompt I'll use to ingest new files from `raw/` : "Ingest everything in raw/ following AGENTS.md . Update wiki/. When done, move ingested raw files to processed/."
