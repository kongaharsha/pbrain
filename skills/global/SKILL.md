---
name: global
description: Manage the global pbrain portfolio cockpit. Use for /pbrain:global, cross-project questions, portfolio status, task rollups across projects, active project index review, stale project checks, and routing local project next steps into the global brain when it exists.
---

# pbrain Global

Use this skill for the cross-project portfolio brain.

## Contract

This skill guarantees:

- Local project brains remain authoritative.
- The global pbrain summarizes and links; it does not duplicate detailed workstream truth.
- Cross-project tasks link back to their local project and workstream source.
- If the global pbrain is not set up, local project workflows still work.

## Phases

1. Check whether the global pbrain exists. Default path: `C:\Users\harsha.konga\Project Brain\`.
2. If it does not exist and the user asks for global behavior, route to `global-setup`.
3. Read global `PROJECTS.md`, `PORTFOLIO.md`, `TASKS.md`, `INTERDEPENDENCIES.md`, `DAILY.md`, and recent `weekly/` notes when present.
4. If there are no registered project folders, ask the user to paste the project directories to track.
5. For each active project, read only the minimum local files needed: `TODO & Ideas.md`, active `WORKSTREAM.md`, and folder map/context if needed.
6. If a registered project folder is not pbrain-ready, route to `migrate` before treating it as an active local source.
7. Update global portfolio files with:
   - active projects and current focus
   - cross-project task rollup
   - stale projects or workstreams
   - dependencies and asks
   - links back to local authoritative files

## Task Rollup Rules

- P0: urgent blocker, deadline, or decision needed this week.
- P1: important this week.
- P2: useful next action but not urgent.
- P3: parking lot.
- Each task should include project, workstream, owner if known, due date if known, and source link.

## Output Format

```markdown
## Global pbrain Update

### Active Projects

### Cross-Project Priorities

### Dependencies / Asks

### Stale Items

### Recommended Next Actions
```

## Anti-Patterns

- Copying full local workstream detail into the global brain.
- Creating global tasks without source links.
- Treating global summaries as more authoritative than local ledgers.
- Failing when no global pbrain exists; local mode should continue.
- Guessing tracked project directories without user confirmation.
