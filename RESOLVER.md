# pbrain Resolver

Use this file as the routing table for the pbrain plugin. Local pbrains are authoritative. The global portfolio brain is an index, rollup, and operating cockpit that links back to local projects.

## Always-On When pbrain Is Active

| Trigger | Skill |
|---|---|
| Any pbrain read/write/lookup/update | `router` |
| Any durable project decision, file arrival, feedback, or status change | `update` |
| Any cross-project priority or dependency question | `global-index` then `global` |

## Skill Groups

Keep skill folders flat under `skills/` so Codex can discover them. Use these groups as the mental model.

### Core

| User intent | Skill |
|---|---|
| Route any pbrain request and load context | `router` |

### Setup And Migration

| User intent | Skill |
|---|---|
| Create a new local pbrain from scratch | `setup` |
| Add pbrain to an existing project folder | `migrate` |

### Global Portfolio Brain

| User intent | Skill |
|---|---|
| Create the global portfolio brain | `global-setup` |
| Manage global portfolio brain or roll up cross-project tasks | `global` |
| Refresh the global active-project index | `global-index` |

### Daily Operations

| User intent | Skill |
|---|---|
| Manage P0-P3 tasks | `daily-task-manager` |
| Prepare the day | `daily-task-prep` |
| Schedule recurring checks or summaries | `cron-scheduler` |

### Maintenance And Reporting

| User intent | Skill |
|---|---|
| Update local context and workstream ledgers | `update` |
| Audit brain health and stale context | `maintain` |
| Write the weekly project summary | `eow-summary` |

### Knowledge Work

| User intent | Skill |
|---|---|
| Deepen a stakeholder, company, competitor, market, or workstream | `enrich` |
| Do project-aware research, strategic reading, or synthesis | `research` |
| Ingest documents, transcripts, emails, articles, links, notes, or mixed source packets | `ingest` |

## Routing Rules

1. Prefer the most specific active skill. Use `ingest` for all source ingestion and `research` for all research/synthesis.
2. When a request changes durable project truth, update the relevant local `WORKSTREAM.md` or present the exact update before editing.
3. Do not create new markdown files for routine thoughts. Use the active `WORKSTREAM.md` ledger unless the artifact is a durable deliverable, substantial research brief, meeting note/transcript, or reusable analysis.
4. For cross-project questions, start in the global portfolio brain, then follow links into local pbrains for source truth.
5. For project-specific questions, start in the local project folder. Use the global brain only for portfolio-level priorities, dependencies, and cross-project task rollups.

## Chaining Rules

1. Ingested content that creates durable signal should chain into `update`.
2. Entity or topic ingestion that needs more context should chain into `enrich`.
3. Research should start with `router` so existing project truth frames what is new.
4. Weekly summaries should chain into `global-index` when the project is registered in the global brain.
5. Cron jobs should be thin: schedule a prompt that invokes the relevant pbrain skill, not a long inline procedure.

## Disambiguation Rules

1. If the user says "set up" and the folder is empty or new, use setup.
2. If the user says "set up" and the folder already has substantial files, use migrate.
3. If the user asks "what should I work on", use `daily-task-prep` for today and `global` for portfolio-wide prioritization when the global brain exists.
4. If the user asks "what happened this week", use end-of-week summary.
5. If the user shares content, route by type before doing synthesis.

## Memory Model

- `AGENTS.md`: project-specific operating instructions and Mira persona.
- Context folder: usually `.context/`, but preserve existing equivalents such as `0. Context/` or `.GPT/`.
- `Project Context.md`: durable project framing.
- `TODO & Ideas.md`: short current priority tracker, not a giant backlog.
- `Writing & Slide Standards.md`: output quality and communication standards.
- `Folder Map.md`: navigation guide.
- `workstreams/<name>/WORKSTREAM.md`: canonical ledger for workstream decisions, changes, findings, sources, open questions, and next steps.
- Existing workstream layouts are valid. Do not force a nested `workstreams/` folder if the project already uses numbered folders or direct workstream folders.
- Local `Agents.md` or SOP files inside workstreams are operating guides, not long-term changelogs.
- Global portfolio brain: active project index, cross-project tasks, daily prep, weekly summaries, stale items, and interdependencies.

## Cross-Cutting Quality Rules

- Every factual claim in a briefing, weekly summary, or research synthesis should link to a source file, workstream ledger, or external citation.
- User-provided decisions are highest-authority project signal; preserve them in the relevant ledger.
- Updates should be idempotent: re-running a maintenance or summary skill should not duplicate entries.
- Timeline/change log entries require a date. Use `DATE TIME` when known, otherwise `DATE`.
- Never silently overwrite a human-authored assessment. Add a dated update or mark the conflict.
