---
name: global-setup
description: Create the global pbrain portfolio folder outside individual projects. Use for /pbrain:global-setup, global project index setup, cross-project operating brain, or creating a portfolio cockpit that links to multiple local pbrains.
---

# pbrain Portfolio Setup

Create the global portfolio brain outside project folders.

## Default Location

Use `~/Project Brain/` unless the user specifies a different path.

On Harsha's Windows machine, this resolves to:

`C:\Users\harsha.konga\Project Brain\`

## Structure

Create:

- `PORTFOLIO.md` - active project index and operating cockpit.
- `PROJECTS.md` - registry of project folders tracked by global pbrain.
- `TASKS.md` - cross-project priority rollup.
- `INTERDEPENDENCIES.md` - dependencies across projects.
- `DAILY.md` - latest daily operating brief or links to daily notes.
- `weekly/` - end-of-week summaries.
- `projects/` - optional lightweight project registry pages only when helpful.

## Project Registration

After creating the global pbrain, discover or collect project folders:

1. If the user invoked global setup from inside a project folder, offer to register the current folder first.
2. If existing project folders are not obvious, ask the user to paste the directories that should be tracked.
3. For each project folder:
   - check whether it has a local pbrain (`AGENTS.md` plus context folder plus at least one `WORKSTREAM.md` or equivalent)
   - if it is not pbrain-ready, route to `migrate` before registering it as active
   - add it to `PROJECTS.md` and `PORTFOLIO.md` with path, status, context folder, active workstreams, and next check date
4. Do not guess project folders from broad home/OneDrive scans without user confirmation.

## Rules

- Do not duplicate local workstream detail.
- Store links to local project folders and key ledgers.
- Treat local pbrains as authoritative.
- Use portfolio files for cross-project priority, dependency, stale-item, and cadence management.
- Global setup should bootstrap the registry. A global brain without tracked project paths is incomplete.
