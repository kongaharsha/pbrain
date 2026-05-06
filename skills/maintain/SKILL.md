---
name: maintain
description: Audit pbrain health. Use for /pbrain:maintain, stale ledgers, missing source links, outdated folder maps, orphan folders, bloated TODOs, stale portfolio index, and pbrain cleanup.
---

# pbrain Maintain

Run a health check on a local pbrain or global portfolio brain.

## Contract

This skill guarantees:

- Every health dimension is checked and reported, even when clean.
- Each issue has a recommended fix.
- Local project truth is not moved into the global portfolio brain.
- Risky destructive changes are not performed without confirmation.

## Checks

- Missing or stale `WORKSTREAM.md` files.
- Orphan workstream folders.
- `TODO & Ideas.md` acting like a giant backlog.
- Source files not linked from ledgers.
- Change log entries without dates.
- Decisions buried in chat or documents but absent from ledgers.
- Folder map out of date.
- Global portfolio index pointing to missing projects.
- Global `PROJECTS.md` missing registered project directories.
- Local projects registered globally but missing pbrain setup.
- Broken or stale bidirectional links between global and local project brains.

## Phases

1. Resolve scope: local project, global portfolio, or both.
2. Load pbrain context with `pbrain`.
3. If global scope is included, read `PROJECTS.md` and scan each registered project folder.
4. Run each check and count issues.
5. For registered projects missing local pbrain files, recommend or route to `migrate`.
6. Apply straightforward fixes if requested.
7. Report remaining issues and recommended next actions.

## Output

Lead with a concise audit:

- Up to date
- Needs update
- Missing or stale
- Recommended fixes

Apply fixes only when the user requested implementation or the changes are straightforward and low risk.

## Output Format

```markdown
## pbrain Health Report - YYYY-MM-DD

| Dimension | Issues Found | Fixed | Remaining |
|---|---:|---:|---:|
| Stale ledgers |  |  |  |
| Orphan folders |  |  |  |
| Missing source links |  |  |  |
| Bloated TODOs |  |  |  |
| Folder map drift |  |  |  |
| Portfolio index drift |  |  |  |

### Details

### Recommended Fixes
```

## Anti-Patterns

- Marking a dimension clean without checking it.
- Rewriting large context files when a surgical update would do.
- Deleting or moving user files during maintenance.
- Treating global portfolio summaries as authoritative over local ledgers.
