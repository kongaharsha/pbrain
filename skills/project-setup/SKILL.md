---
name: project-setup
description: Set up or retrofit a P-Brain for a new or existing OneDrive project. Use for project setup, migration, creating AGENTS.md and context files, operating ledgers, stakeholder/folder maps, or Central Brain registration.
---

# P-Brain Project Setup

Set up one coherent operating layer for a new or existing project without disturbing its source library.

## Workflow

1. Resolve the target folder and inspect its instructions, context layer, workstreams, sources, deliverables, and dates.
2. Detect whether the project is new, partially structured, or already operating. Preserve useful conventions such as `0. Context/` or `.context/` and all existing source files.
3. Resolve the private OneDrive Central Brain from the user's stated path or project instructions. Create it when absent only when asked, with `AGENTS.md`, `PROJECTS.md`, `PORTFOLIO.md`, `TASKS.md`, `INTERDEPENDENCIES.md`, and `Improvement Backlog.md`.
4. Create or reconcile the local operating layer:
   - `AGENTS.md`
   - `Project Context.md`
   - `Project Operating Ledger.md` — concise current priorities, tasks, cross-cutting outcomes, workstream state, and decision positions
   - `Evidence & Evolution Log.md` — append-only, timestamped, source-linked history
   - `Stakeholder Map.md` when stakeholder coordination matters
   - `Folder Map.md`
5. Preserve an existing `Workstream Ledger.md` as historical reference. Migrate only the active control state into the operating ledger; do not copy the full history.
6. Register the project in the Central Brain with its OneDrive path, context folder, declared current operating view, status, and a compact portfolio card.

## Rules

- Do not move, rename, delete, or rewrite user source files during setup.
- Seed each active outcome or workstream with a clear current state, 1–3 actionable tasks, owner / decision right, dependency, done condition, and source or evolution-log link.
- Treat cross-cutting outcomes as first-class records. Link a task to every relevant outcome or workstream instead of duplicating it.
- Make AGENTS.md explicit about the two layers, source filing, and the legacy status of previous TODOs or ledgers.
- Record the Central Brain location in project instructions when configured. Keep the P-Brain Git checkout separate; never copy project evidence, conversation exports, or Central Brain records into it.
- Do not create a separate project TODO by default.

## Output

Report the context folder, current-control and evidence-history design, active outcomes/workstreams, Central Brain registration, and any unresolved source-of-truth gaps.
