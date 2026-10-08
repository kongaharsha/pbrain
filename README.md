# pbrain

pbrain gives strategy projects durable working memory: source-grounded context, workstream action logs, daily priorities, and a cross-project Central Brain. Use it as a Codex plugin or as markdown playbooks with an agent that can read local files.

Project folders hold evidence and operating truth. The Central Brain summarizes and links across projects. This repository contains reusable skills and templates; project evidence and conversation archives stay in private project folders.

## Skills

pbrain ships ten skills. Read [RESOLVER.md](RESOLVER.md) to choose the smallest workflow that matches the request.

| Skill | Purpose |
|---|---|
| `pbrain:project-setup` | Set up or retrofit a project, its workstream controls, and Central Brain registration. |
| `pbrain:project-update` | Capture material work or reconcile changed sources into durable project memory. |
| `pbrain:enrich-brain` | Ingest sources, research, and deepen project or stakeholder context. |
| `pbrain:daily-prep` | Prepare a meeting-aware daily brief and action plan. |
| `pbrain:daily-task-manager` | Add, complete, defer, review, or prioritize project and cross-project tasks. |
| `pbrain:operating-review` | Assess operating health and publish advisory guidance. |
| `pbrain:automation-scheduler` | Propose and, after approval, configure recurring project cadences. |
| `pbrain:conversation-capture` | Export an explicitly selected conversation into a private project archive. |
| `pbrain:improve-skill` | Propose a small, evidence-backed improvement from explicit feedback. |
| `pbrain:skill-evals` | Build or run a de-identified behavioral benchmark. |

Older instructions may mention `setup`, `migrate`, `global-setup`, `global-index`, `update`, `maintain`, `daily-task-prep`, `cron-scheduler`, `ingest`, `research`, or `enrich`. These are not separate skills in this package. Setup and retrofit use `project-setup`; reconciliation uses `project-update`; ingestion and research use `enrich-brain`; daily preparation uses `daily-prep`; health reviews use `operating-review`; scheduling uses `automation-scheduler`. Central Brain setup is handled by `project-setup` when explicitly requested.

## Install

For an agent-assisted installation, ask your agent to read [INSTALL_FOR_AGENTS.md](INSTALL_FOR_AGENTS.md), summarize the proposed changes, and install the package for your environment.

For a markdown-playbook checkout:

```bash
git clone https://github.com/kongaharsha/pbrain.git ~/pbrain
```

Tell your agent:

```text
Use the pbrain playbooks at ~/pbrain. Read RESOLVER.md first and follow the
matching SKILL.md under skills/. Project folders are the source of truth;
keep the Central Brain as a compact index and rollup.
```

For a Codex plugin checkout on Windows:

```powershell
New-Item -ItemType Directory -Force -Path "$HOME\.codex\plugins"
git clone https://github.com/kongaharsha/pbrain.git "$HOME\.codex\plugins\pbrain"
```

Enable that local plugin through your host's plugin registration mechanism. Registration may be required in addition to cloning. The package's entry point is [.codex-plugin/plugin.json](.codex-plugin/plugin.json), with skills under `./skills/`. See the installation guide for checks and update instructions.

## First run

1. Open your project folder and ask for `pbrain:project-setup`. Preserve existing sources and useful folder conventions.
2. If you want cross-project controls, provide a separate private Central Brain folder and explicitly ask `project-setup` to create or reconcile it and register the project.
3. Use `project-update` after material work or changed evidence. Use `enrich-brain` for source ingestion or research.
4. Use `daily-prep` for priorities, `daily-task-manager` for task changes, and `operating-review` for health checks.
5. Ask `automation-scheduler` to propose a cadence when recurring checks would help. Review its schedule and prompt before creation.

For example:

```text
Use pbrain:project-setup in this folder. Preserve the source library and
existing folder structure. Create a concise Workstream Ledger.md dashboard
and one Workstream - <Name>.md page for each active workstream in the
existing context folder. Register the project in my configured Central
Brain if one exists; flag any missing location rather than guessing it.
```

## Operating model

| Location | Responsibility |
|---|---|
| Project `AGENTS.md` | Declares the operating model, context paths, and source-filing rules. |
| Context `Workstream Ledger.md` | Thin dashboard and cross-workstream P0-P3 priority register. |
| Context `Workstream - <Name>.md` | Compiled current truth, live tasks, and timestamped source-linked action log. |
| `Project Context.md`, `Stakeholder Map.md`, `Folder Map.md` | Durable framing, people, and navigation. |
| Central Brain | `PROJECTS.md`, compact `PORTFOLIO.md`, cross-project-only `TASKS.md`, `INTERDEPENDENCIES.md`, and `Improvement Backlog.md`. |
| Project conversation archive | Explicitly approved exports; private evidence, outside this repository. |

Preserve existing `WORKSTREAM.md` files and older ledgers as historical sources. A project may declare a distributed-ledger exception; follow its instructions rather than creating competing control views. Some bundled templates support these existing conventions and should be adapted to the operating model declared in the project's `AGENTS.md`.

Routine project memory goes into the relevant workstream page. Update the thin dashboard only when status, ownership, outcomes, priorities, or the next control point changes. Link decisions and tasks to their sources, distinguish facts from assumptions, and avoid duplicate TODOs or indexes.

Transcript routing follows any review queue declared by the project. Advisory guidance and improvement candidates never override operating truth. Reusable evaluation cases and improvements must be approved and de-identified before entering this repository.

## Repository layout

```text
.codex-plugin/plugin.json
INSTALL_FOR_AGENTS.md
RESOLVER.md
assets/templates/
skills/
  automation-scheduler/
  conversation-capture/
  daily-prep/
  daily-task-manager/
  enrich-brain/
  improve-skill/
  operating-review/
  project-setup/
  project-update/
  skill-evals/
```

## Lineage and license

pbrain builds on the original [strategy-project](https://github.com/kongaharsha/claude-skills/tree/main/strategy-project) pattern and takes inspiration from [GBrain](https://github.com/garrytan/gbrain). It stays markdown-first: no database, embeddings, or custom server is required by this package. Licensed under [MIT](LICENSE).
