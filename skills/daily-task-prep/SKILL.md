---
name: daily-task-prep
description: Prepare a daily operating brief from pbrain context. Use for /pbrain:daily-task-prep, morning prep, today's priorities, meetings, blockers, open loops, and recommended next actions across one or more projects.
---

# pbrain Daily Task Prep

Prepare the user's day from local and global project context.

## Workflow

1. Determine scope: one project or global portfolio.
2. Read local current tasks and relevant workstream ledgers.
3. If the global pbrain exists at `C:\Users\harsha.konga\Project Brain\`, also read active project index, stale items, and global `TASKS.md`.
4. If it does not exist, produce local project prep only.
5. Produce a concise daily prep:
   - top priorities
   - meetings or decision moments if known
   - blockers to clear
   - open loops
   - recommended order of attack
6. Update global `DAILY.md` only if the user wants a durable daily note and global pbrain exists.

## Rules

- Prefer an inline brief unless a durable record is requested.
- Link to source ledgers for tasks and blockers.
- Local context wins for project-specific details; global context is a rollup.
