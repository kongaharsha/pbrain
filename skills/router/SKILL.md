---
name: router
description: pbrain router for strategy project and portfolio work. Use when the user invokes /pbrain:* commands or asks to set up, migrate, update, maintain, summarize, enrich, research, synthesize, ingest, or manage tasks across one or more pbrains.
---

# pbrain

pbrain manages local pbrains and an optional global portfolio brain.

First read the plugin root `RESOLVER.md`, then route to the most specific pbrain skill. If a request combines multiple intents, run them in this order:

1. Resolve scope and load existing context.
2. Setup or migrate missing brain structure.
3. Ingest or research source material.
4. Update local workstream ledgers.
5. Refresh global portfolio index or task rollup.
6. Produce task prep or weekly summaries.

## Core Rules

- Local project folders are authoritative.
- Global portfolio brain is an index, task rollup, and operating cockpit.
- Each `workstreams/<name>/WORKSTREAM.md` is the canonical ledger for workstream truth.
- Preserve existing context/workstream conventions such as `0. Context/`, `.GPT/`, numbered workstream folders, or direct workstream folders.
- Avoid markdown sprawl. Create separate markdown only for durable outputs, substantial research briefs, transcripts/notes, or reusable analysis.
- Use Mira's default posture: engagement-manager-level strategy partner, MECE, storyline-first, interdependency-aware, warm but direct.
- Each skill should follow the pattern: Contract, Phases, Output Format, Anti-Patterns.

## Commands

- `/pbrain:setup`
- `/pbrain:migrate`
- `/pbrain:global`
- `/pbrain:global-setup`
- `/pbrain:global-index`
- `/pbrain:daily-task-manager`
- `/pbrain:daily-task-prep`
- `/pbrain:cron-scheduler`
- `/pbrain:update`
- `/pbrain:maintain`
- `/pbrain:eow-summary`
- `/pbrain:enrich`
- `/pbrain:research`
- `/pbrain:ingest`
- `/pbrain:router`
