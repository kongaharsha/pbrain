---
name: update
description: Refresh local pbrain context and workstream ledgers. Use for /pbrain:update, syncing .context, reconciling recent file changes, recording decisions, updating source links, and keeping WORKSTREAM.md current.
---

# pbrain Update

Bring a local pbrain up to date.

## Contract

This skill guarantees:

- `WORKSTREAM.md` remains the canonical workstream ledger.
- Updates are surgical and append history instead of erasing it.
- New files, decisions, feedback, and findings are linked from the right ledger.
- `.context/` files are updated only when their durable purpose changes.

## Workflow

1. Read `AGENTS.md`, the actual context folder (`.context/`, `0. Context/`, `.GPT/`, or equivalent), and all active `WORKSTREAM.md` ledgers.
2. Scan for new or changed files, recent outputs, source materials, and orphan folders.
3. Compare current files against ledgers:
   - missing decisions
   - missing change log entries
   - new source files
   - stale next steps
   - changed priorities
4. Update surgically:
   - `WORKSTREAM.md` for workstream-level truth
   - `TODO & Ideas.md` for near-term priorities
   - `Project Context.md` only for durable project framing changes
   - `Folder Map.md` for structure changes
5. If global pbrain exists and the update changes cross-project priorities, route the rollup to `global`.

## Rules

- Preserve history. Append decision/change log entries instead of rewriting the past.
- Link to files that were created, added, or changed when relevant.
- Do not create new markdown files for routine updates.
- Re-running the update should not duplicate change log entries.
- Detect the project's actual context folder (`.context/`, `0. Context/`, `.GPT/`, or equivalent) before updating.
- If recent conversation/transcript files exist, check the latest one and flag conflicts with the ledger.
- Update local workstream `Agents.md` only when operating instructions change, not for status/changelog.

## Output Format

```markdown
## pbrain Update

### Updated
- <file> - <what changed>

### Durable Changes Captured
- ...

### Still Open
- ...
```

## Anti-Patterns

- Rewriting all context files because one workstream changed.
- Creating new markdown notes for routine decisions that belong in `WORKSTREAM.md`.
- Guessing dates when metadata or conversation context does not support them.
- Moving source files during an update.
