# pbrain

pbrain is a Codex plugin for running strategy projects as living project brains.

It gives each project a durable local memory, then optionally connects those projects to a global portfolio brain that acts as an operating cockpit across active work. The core rule is simple: local project folders are the source of truth; the global brain indexes, summarizes, and links back.

pbrain is the second version of the earlier [strategy-project](https://github.com/kongaharsha/claude-skills/tree/main/strategy-project) pattern. The first version created durable project context and workstream discipline. As it got used on real projects, the need became clearer: the brain should stay current, reduce markdown sprawl, preserve workstream ledgers, support ingestion and research, and make cross-project work easier to operate. pbrain is that next iteration.

## What pbrain Does

pbrain helps Codex answer and maintain the questions that make strategy work hard to resume:

- What is the project trying to decide?
- What changed this week?
- Which workstreams are moving, blocked, or stale?
- What are the open questions, next steps, and dependencies?
- What source file or conversation supports this claim?
- What should I work on today across all projects?

Instead of creating markdown files for every thought, pbrain treats each `WORKSTREAM.md` as the canonical ledger for decisions, changes, findings, sources, open questions, and next steps. Separate markdown files are reserved for durable outputs, substantial research briefs, transcripts, meeting notes, and reusable analysis.

## 30-Minute Setup

The recommended sequence is:

1. Install and enable the pbrain plugin in Codex.
2. In each project folder, run `/pbrain:setup` for a new project or `/pbrain:migrate` for an existing project.
3. Run `/pbrain:global-setup` to create the global portfolio brain.
4. Register the project folders you want tracked, then run `/pbrain:global-index`.
5. Run `/pbrain:cron-scheduler` to schedule recurring maintenance, portfolio refreshes, and weekly summaries.

After setup, pbrain should feel like a working operating layer: local workstreams stay current, the global brain tracks the portfolio, and scheduled checks keep stale context from quietly drifting.

## Local Project Brain

Each project keeps its own local pbrain. This remains authoritative.

Typical files:

| File or folder | Purpose |
|---|---|
| `AGENTS.md` | Project instructions and the default Mira persona. |
| `.context/` | Durable project context, writing standards, folder map, and current priorities. |
| `workstreams/<name>/WORKSTREAM.md` | Canonical workstream ledger. |
| Existing workstream folders | Preserved when migrating an existing project. |

The generated `AGENTS.md` uses **Mira** by default: an engagement-manager-level strategy partner who is MECE, storyline-first, interdependency-aware, warm but direct, and careful about separating fact from inference.

## Global Portfolio Brain

The global pbrain lives outside individual projects. The default location is:

```text
C:\Users\harsha.konga\Project Brain\
```

Typical files:

| File or folder | Purpose |
|---|---|
| `PROJECTS.md` | Registry of tracked projects and links to local pbrains. |
| `PORTFOLIO.md` | Cross-project status, priorities, risks, and stale items. |
| `TASKS.md` | Cross-project P0-P3 task rollup. |
| `INTERDEPENDENCIES.md` | Dependencies between projects, stakeholders, and decisions. |
| `DAILY.md` | Daily operating brief surface. |
| `weekly/` | End-of-week summaries. |
| `projects/` | Lightweight project index pages that link back to source folders. |

The global brain should not duplicate every project detail. It should point back to the local project brain for source truth.

## Skills

| Skill | What it does | Use it when |
|---|---|---|
| `/pbrain:setup` | Creates a new local pbrain from scratch. | You are starting a new project folder. |
| `/pbrain:migrate` | Adds pbrain to an existing project without changing existing files. | A project already has scattered folders, files, decks, or notes. |
| `/pbrain:global-setup` | Creates the global portfolio brain. | You want one cockpit across multiple projects. |
| `/pbrain:global-index` | Refreshes the global project registry and cross-project index. | Projects changed, new folders were added, or links need refreshing. |
| `/pbrain:global` | Answers and manages portfolio-level questions. | You need cross-project status, priorities, risks, or dependencies. |
| `/pbrain:daily-task-manager` | Manages P0-P3 tasks across local and global context. | You need to clean up tasks, assign priority, or resolve blockers. |
| `/pbrain:daily-task-prep` | Creates a daily operating brief. | You want today's priorities, open loops, meetings, and next actions. |
| `/pbrain:cron-scheduler` | Schedules recurring pbrain routines using Codex automations. | You want weekly maintenance, daily prep, or end-of-week summaries to run automatically. |
| `/pbrain:update` | Reconciles recent project changes into context and workstream ledgers. | Files, decisions, tasks, or workstreams changed. |
| `/pbrain:maintain` | Audits brain health. | You want stale ledgers, missing links, bloated TODOs, or orphan folders caught. |
| `/pbrain:eow-summary` | Writes an end-of-week summary. | You need a weekly note with accomplishments, insights, risks, and next-week priorities. |
| `/pbrain:enrich` | Deepens a topic inside the brain. | You need more complete context for a stakeholder, market, competitor, company, workstream, or decision. |
| `/pbrain:research` | Runs project-aware research and synthesis. | You need source-backed research, recommendations, or synthesis through a project lens. |
| `/pbrain:ingest` | Ingests documents, transcripts, emails, articles, links, and notes. | New source material should update the right ledger and source list. |
| `/pbrain:router` | Router and general entry point. | You are not sure which pbrain skill to use. |

## How It Works

```text
Signal arrives: file, meeting note, email, transcript, article, decision, task
  -> pbrain resolves scope: local project, global portfolio, or both
  -> It reads AGENTS.md, .context, folder maps, and active WORKSTREAM.md ledgers
  -> It updates the smallest authoritative surface, usually WORKSTREAM.md
  -> It links to created or changed files instead of duplicating them
  -> If global pbrain exists, it refreshes project links, task rollups, and stale items
  -> Scheduled maintenance keeps the local and global brains from drifting
```

## Operating Cadence

Suggested cadence after setup:

| Cadence | Routine |
|---|---|
| Daily | Run `/pbrain:daily-task-prep` or schedule it with `/pbrain:cron-scheduler`. |
| Weekly | Run `/pbrain:update`, `/pbrain:maintain`, `/pbrain:global-index`, and `/pbrain:eow-summary`. |
| When new source material arrives | Run `/pbrain:ingest`. |
| When a topic becomes important | Run `/pbrain:enrich` or `/pbrain:research`. |
| When projects are added or reorganized | Run `/pbrain:migrate` locally, then `/pbrain:global-index`. |

## Design Principles

- Local project brains are authoritative.
- The global brain is an index and operating cockpit, not a duplicate project archive.
- `WORKSTREAM.md` is the canonical ledger for routine project memory.
- Avoid markdown sprawl.
- Preserve existing folder structures during migration.
- Every important claim should link to a source file, ledger entry, or citation.
- Updates should be idempotent, so re-running maintenance does not duplicate entries.
- Cron jobs should run thin pbrain routines, not long custom procedures.

## Repository Layout

```text
.codex-plugin/plugin.json
RESOLVER.md
assets/templates/
skills/
  router/
  setup/
  migrate/
  global-setup/
  global-index/
  global/
  daily-task-manager/
  daily-task-prep/
  cron-scheduler/
  update/
  maintain/
  eow-summary/
  enrich/
  research/
  ingest/
```

## Local Development

To test changes locally, copy or sync this plugin folder into:

```text
C:\Users\harsha.konga\.codex\plugins\pbrain
```

Then make sure the local Codex marketplace points at the plugin and restart Codex. Once restarted, the available skills should appear with the `pbrain:` prefix.

## Lineage

pbrain builds on the original [strategy-project README](https://github.com/kongaharsha/claude-skills/blob/main/strategy-project/README.md), with inspiration from brain-style operating systems such as [GBrain](https://github.com/garrytan/gbrain). It intentionally stays markdown-first in v1 of this plugin: no database, embeddings, or custom CLI dependency required.
