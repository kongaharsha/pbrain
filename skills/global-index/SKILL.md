---
name: global-index
description: Refresh the global pbrain portfolio index. Use for /pbrain:global-index, scanning registered project folders, updating active project status, stale items, interdependencies, and links back to local pbrains.
---

# pbrain Portfolio Index

Refresh the global portfolio brain from registered local pbrains.

## Workflow

1. Locate the global portfolio brain.
2. Read `PROJECTS.md`, `PORTFOLIO.md`, `TASKS.md`, and registered project paths.
3. If `PROJECTS.md` is missing or empty, ask the user to paste the project directories that should be tracked.
4. For each project, verify the local pbrain exists:
   - `AGENTS.md` or equivalent instructions
   - context folder (`.context/`, `0. Context/`, `.GPT/`, or equivalent)
   - at least one `WORKSTREAM.md` or clear workstream ledger equivalent
5. If a registered project is not pbrain-ready, flag it and route to `migrate` before relying on it for global summaries.
6. For each ready project, read local `TODO & Ideas.md`, `Project Context.md`, folder map, and recent `WORKSTREAM.md` files.
7. Update the global index with:
   - project status
   - current focus
   - stale workstreams
   - major blockers
   - cross-project dependencies
   - links to authoritative local files

## Rules

- Summarize, do not copy detailed findings.
- Preserve human-written notes unless stale.
- When a local pbrain is missing or broken, flag it instead of guessing.
- Keep global links bidirectional where possible: global files link to local project ledgers, and local folder maps/AGENTS mention the global pbrain path when registered.
