---
name: daily-task-manager
description: Manage task lifecycle in P-Brain project operating ledgers or the global cross-project task register. Use for add task, complete task, defer task, task review, or task prioritization.
---

# P-Brain Daily Task Manager

Maintain tasks where their operating context already lives; do not invent a second task system.

## Workflow

1. Resolve scope. Use the relevant project's `AGENTS.md` and `Project Operating Ledger.md`; use the global `TASKS.md` only for genuinely cross-project work.
2. Read the existing task section and linked outcome/workstream IDs. Preserve the project's declared schema. If no task schema exists, use stable IDs of the form `T-YYYY-MM-DD-NN`, status (`open`, `in-progress`, `blocked`, `deferred`, `done`), owner, priority, and optional due date.
3. Route intent: add, start, complete, defer, revise, or review. Match a referenced task by stable ID first. If multiple plausible tasks match, present candidates and do not mutate.
4. For add, require a description; record an explicit priority/due date when supplied, otherwise mark them unset rather than inventing them. Link the task to its outcome/workstream when known.
5. For complete, defer, or revise, update only the affected task entry and add a concise source-linked `EV-` record when the change reflects material project progress or a decision. Do not add an evolution record for trivial personal housekeeping.
6. For review, return open work grouped by priority, due date, and blocker. Flag stale tasks for review; never silently complete, defer, or reprioritize them.

## Guardrails

- The operating ledger is the project task authority; the global register is only for cross-project tasks.
- Preserve unknown sections and other people's entries. Apply minimal edits.
- Explicit deletion is destructive: ask for confirmation and prefer completion or archival.
- A scheduled task review is read-only/proposal-only unless its prompt explicitly authorizes a narrow, idempotent update and the project's operating model permits it.

## Output

Return action, task ID, scope, resulting status, affected control record, and any ambiguity or review item.
