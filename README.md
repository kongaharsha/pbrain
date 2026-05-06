# pbrain

Your AI agent is smart, but strategy projects are messy. pbrain gives Claude Code or Codex a durable working memory.

pbrain is a markdown-first project brain for strategy work: project setup, workstream ledgers, task rollups, source ingestion, research synthesis, weekly summaries, and portfolio-level operating rhythm. It can run as a Codex plugin, and it can also be used directly by Claude Code as a set of agent-readable playbooks. Each project keeps its own local brain. An optional global brain sits outside the projects and links them together.

The operating principle is simple: local project folders are the source of truth; the global brain is an index, rollup, and cockpit. It should help you resume the work, see what changed, find the source behind a decision, and understand what needs attention next.

pbrain is the second version of the earlier [strategy-project](https://github.com/kongaharsha/claude-skills/tree/main/strategy-project) pattern. The first version created durable local project context. pbrain keeps that discipline, then adds a global portfolio brain, scheduled maintenance, ingestion, research, enrichment, weekly summaries, and cleaner routing across skills.

> ~30 minutes to a fully working project brain. No database, no embeddings, no custom CLI. You install the plugin, answer a few setup questions, register your project folders, and schedule recurring checks.

## Install

### Option A: Ask your agent to install it

Open Claude Code or Codex and paste this into a new chat:

```text
Retrieve and follow the instructions at:
https://raw.githubusercontent.com/kongaharsha/pbrain/main/INSTALL_FOR_AGENTS.md
```

That is the recommended path. The agent will clone the repo, install it in the right place for your environment, validate the skill/playbook names, and tell you what to do next.

### Option B: Claude Code playbook install

Claude Code can use pbrain without a plugin runtime. Clone the repo wherever you keep agent playbooks:

```bash
git clone https://github.com/kongaharsha/pbrain.git ~/pbrain
```

Then open Claude Code in a project folder and paste:

```text
Use the pbrain playbooks at ~/pbrain.

Read ~/pbrain/RESOLVER.md first. When I ask for pbrain setup, migration, global brain setup, updates, maintenance, ingestion, research, enrichment, task prep, or weekly summaries, route to the matching SKILL.md under ~/pbrain/skills/.

Treat local project files as the source of truth. Keep routine decisions, changes, findings, source links, open questions, and next steps in WORKSTREAM.md ledgers. Avoid creating extra markdown files unless the output is durable.
```

If you want the instruction to persist for that project, add the same guidance to the project's `CLAUDE.md`.

### Option C: Codex plugin install

Prerequisite: Git must be installed. If `git --version` does not work, install Git and reopen your terminal.

Clone the repo directly into your Codex plugins folder:

```bash
mkdir -p ~/.codex/plugins
git clone https://github.com/kongaharsha/pbrain.git ~/.codex/plugins/pbrain
```

On Windows PowerShell, the same command is:

```powershell
New-Item -ItemType Directory -Force -Path "$HOME\.codex\plugins"
git clone https://github.com/kongaharsha/pbrain.git "$HOME\.codex\plugins\pbrain"
```

Restart Codex. If the plugin appears, you are done.

To update later:

```bash
git -C ~/.codex/plugins/pbrain pull
```

On Windows PowerShell:

```powershell
git -C "$HOME\.codex\plugins\pbrain" pull
```

If the plugin does not appear after restart, open Codex and paste:

```text
Enable the local Codex plugin at:
~/.codex/plugins/pbrain

Make sure it is registered as plugin name "pbrain" and that the visible skill names use the pbrain namespace, for example pbrain:setup and pbrain:migrate.
```

## First Run

Set up pbrain in this order.

### 1. Set up each project

For a new or mostly empty project folder, open Claude Code or Codex in that folder and paste:

```text
Use /pbrain:setup in this folder.

Create a local pbrain for this project. Set up AGENTS.md, the context folder, folder map, TODO & Ideas, writing standards, and an initial workstream ledger.

Before writing, check whether a global pbrain already exists at:
C:\Users\<your-user-name>\Project Brain\

If the global pbrain exists, register this project in it. If it does not exist, finish the local setup and tell me to run /pbrain:global-setup next.
```

For an existing project folder with files already in it, open Claude Code or Codex in that folder and paste:

```text
Use /pbrain:migrate in this folder.

Add pbrain to this existing project without moving, deleting, or renaming existing files. Scan the folder, identify workstreams, preserve the current folder structure, create or update AGENTS.md, create the context layer, and add WORKSTREAM.md ledgers only where they are useful.

Avoid markdown sprawl. Routine decisions, changes, findings, source links, open questions, and next steps should go into the relevant WORKSTREAM.md ledger.

Before writing, check whether a global pbrain already exists at:
C:\Users\<your-user-name>\Project Brain\

If the global pbrain exists, register this project in it. If it does not exist, finish the local migration and tell me to run /pbrain:global-setup next.
```

### 2. Create the global brain

After at least one project has a local pbrain, run:

```text
Use /pbrain:global-setup.

Create the global pbrain at:
C:\Users\<your-user-name>\Project Brain\

Ask me for the project folders I want tracked. For each folder, check whether it already has a local pbrain. If it does not, route that folder through /pbrain:migrate before registering it.

Create the global portfolio files:
PROJECTS.md
PORTFOLIO.md
TASKS.md
INTERDEPENDENCIES.md
DAILY.md
weekly/
projects/

The global brain should link back to local project folders. Do not duplicate detailed workstream context.
```

### 3. Refresh the global index

After global setup, run:

```text
Use /pbrain:global-index.

Scan all registered projects in the global pbrain. Refresh the project registry, active project status, stale workstreams, cross-project dependencies, and links back to local WORKSTREAM.md files.

If a registered project is missing a valid local pbrain, flag it and recommend /pbrain:migrate for that folder.
```

### 4. Schedule recurring maintenance

Run:

```text
Use /pbrain:cron-scheduler.

Set up these recurring pbrain automations:

1. Daily operating brief every weekday at 8:00 AM local time.
Prompt: Use /pbrain:daily-task-prep. Read the global pbrain if it exists, then read the relevant local project pbrains. Produce today's priorities, P0-P3 tasks, blockers, meetings or open threads if available, and recommended next actions. Link every task back to the local project or WORKSTREAM.md source.

2. Weekly project maintenance every Friday at 3:00 PM local time.
Prompt: Use /pbrain:update and /pbrain:maintain across every project registered in the global pbrain. Refresh .context, TODO & Ideas, folder maps, and WORKSTREAM.md ledgers from recent file changes. Check for stale ledgers, missing source links, orphan folders, bloated TODOs, and outdated folder maps. Do not create unnecessary markdown files.

3. Weekly portfolio refresh every Friday at 4:00 PM local time.
Prompt: Use /pbrain:global-index. Refresh PROJECTS.md, PORTFOLIO.md, TASKS.md, INTERDEPENDENCIES.md, and stale project indicators. Keep the global pbrain as a rollup and link back to local source-of-truth files.

4. End-of-week summary every Friday at 4:30 PM local time.
Prompt: Use /pbrain:eow-summary. Scan all workstream ledgers and relevant markdown files changed this week. Write a concise weekly summary covering key accomplishments, decisions, insights, risks, blockers, source links, and next-week priorities. Save it under the global pbrain weekly folder if a global pbrain exists; otherwise save it in the local project context.

Before creating each automation, show me the proposed schedule and prompt for confirmation.
```

## What Gets Created

### Local project brain

Each project keeps its own local brain. This is authoritative.

| File or folder | Purpose |
|---|---|
| `AGENTS.md` | Project operating instructions and the default Mira persona. |
| `.context/` | Durable project context, folder map, writing standards, and current priorities. |
| `TODO & Ideas.md` | Short current task and idea tracker, not a giant backlog. |
| `Folder Map.md` | Navigation guide for the project folder. |
| `workstreams/<name>/WORKSTREAM.md` | Canonical workstream ledger. |

The default agent persona is **Mira**: an engagement-manager-level strategy partner who is MECE, storyline-first, interdependency-aware, warm but direct, careful about fact versus inference, and optimized for decision support.

### Global portfolio brain

The global brain lives outside project folders, usually:

```text
C:\Users\<your-user-name>\Project Brain\
```

| File or folder | Purpose |
|---|---|
| `PROJECTS.md` | Registry of tracked projects and links to local pbrains. |
| `PORTFOLIO.md` | Current cross-project status, priorities, risks, and stale items. |
| `TASKS.md` | Cross-project P0-P3 task rollup. |
| `INTERDEPENDENCIES.md` | Dependencies across projects, decisions, teams, and stakeholders. |
| `DAILY.md` | Daily operating brief surface. |
| `weekly/` | End-of-week summaries. |
| `projects/` | Lightweight project index pages that link back to local project folders. |

The global brain should not become a second copy of every project. It should summarize, index, and link.

## The Skills

pbrain ships 15 skills. The resolver (`RESOLVER.md`) tells Codex which skill to use for each task.

### Setup

| Skill | What it does |
|---|---|
| `pbrain:setup` | Creates a local pbrain in a new project folder. |
| `pbrain:migrate` | Adds pbrain to an existing project while preserving existing files and folder structure. |

### Global brain

| Skill | What it does |
|---|---|
| `pbrain:global-setup` | Creates the global portfolio brain and registers tracked project folders. |
| `pbrain:global-index` | Refreshes cross-project status, stale items, dependencies, and links. |
| `pbrain:global` | Answers portfolio-level questions and manages cross-project context. |

### Daily operations

| Skill | What it does |
|---|---|
| `pbrain:daily-task-manager` | Manages P0-P3 tasks across local and global context. |
| `pbrain:daily-task-prep` | Produces a daily operating brief. |
| `pbrain:cron-scheduler` | Creates recurring Codex automations for daily prep, weekly maintenance, portfolio refreshes, and weekly summaries. |

### Maintenance and reporting

| Skill | What it does |
|---|---|
| `pbrain:update` | Reconciles recent file changes, decisions, and workstream movement into local context and ledgers. |
| `pbrain:maintain` | Audits stale ledgers, missing links, bloated TODOs, orphan folders, and outdated maps. |
| `pbrain:eow-summary` | Writes an end-of-week note with accomplishments, plan for next week, insights, risks, decisions, and links. |

### Knowledge work

| Skill | What it does |
|---|---|
| `pbrain:ingest` | Ingests PDFs, docs, decks, spreadsheets, transcripts, emails, articles, links, and notes into the right ledger. |
| `pbrain:research` | Runs project-aware research and synthesis with source-backed recommendations. |
| `pbrain:enrich` | Deepens context on a workstream, stakeholder, company, market, competitor, decision, or theme. |
| `pbrain:router` | General router when the user does not know which pbrain skill to invoke. |

## How It Works

```text
New signal arrives: file, note, meeting, email, article, transcript, decision, task
  -> pbrain resolves scope: local project, global portfolio, or both
  -> pbrain reads AGENTS.md, context files, folder maps, and active WORKSTREAM.md ledgers
  -> routine project memory is written to the smallest authoritative ledger
  -> durable outputs, substantial research briefs, transcripts, and reusable analysis may become separate files
  -> if a global pbrain exists, project status and task rollups are refreshed there
  -> scheduled maintenance keeps context from going stale
```

## Design Rules

- Local project folders are the source of truth.
- The global brain is a cockpit, not a duplicate archive.
- `WORKSTREAM.md` is the canonical ledger for routine workstream memory.
- Avoid markdown sprawl.
- Preserve existing folder structures when migrating.
- Link decisions, claims, and tasks back to source files wherever possible.
- Distinguish fact, inference, recommendation, and open question.
- Re-running setup, update, maintain, or index should not create duplicate entries.

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

## Lineage

pbrain builds on the original [strategy-project README](https://github.com/kongaharsha/claude-skills/blob/main/strategy-project/README.md), with inspiration from brain-style operating systems such as [GBrain](https://github.com/garrytan/gbrain). It intentionally stays markdown-first in this version: no database, embeddings, MCP server, or custom CLI dependency is required.
