---
name: ingest
description: Ingest content into pbrain. Use for /pbrain:ingest with PDFs, docs, decks, spreadsheets, transcripts, emails, articles, links, notes, pasted source material, or mixed source packets that should update a local workstream ledger.
---

# pbrain Ingest

Ingest inbound material into the right local workstream ledger.

## Contract

This skill guarantees:

- Content type is identified before summarizing.
- Ingestion updates the local workstream ledger, not a pile of new markdown files.
- Durable facts, decisions, tasks, and source links are captured.
- Raw content is preserved separately only when it is itself a durable artifact.

## Phases

1. Read local project context and identify the target workstream.
2. Classify the source type:
   - documents: PDFs, docs, decks, sheets, reports, source packs
   - transcripts: meetings, interviews, voice notes
   - emails: pasted threads, stakeholder updates, exported email text
   - articles/links: web articles, market news, competitor announcements
   - mixed packets: inspect each item and summarize by source
3. Extract durable signal:
   - decisions
   - findings
   - source files/links
   - stakeholder signal
   - tasks, owners, deadlines
   - caveats and open questions
4. Update `WORKSTREAM.md` sections as appropriate:
   - `Artifact Index`
   - `Decisions And Working Assumptions`
   - `Activity Timeline / Changelog`
   - `Key Findings`
   - `Open Questions`
   - `Next Steps`
5. Create a separate markdown artifact only for substantial transcripts/notes, reusable research briefs, or deliverables.

## Shared Rules

- Read local project context before ingesting.
- Identify the relevant workstream.
- Extract durable project truth, not every detail.
- Update `WORKSTREAM.md` findings, source files, decisions, change log, open questions, and next steps.
- Create separate markdown only for substantial notes/transcripts or reusable briefs.
- If the global pbrain exists, route cross-project tasks or dependencies to `global` after local ledger updates.

## Output Format

```markdown
## Ingestion Result

### Source Type

### Durable Signal Captured

### Ledger Updates

### Global pbrain Updates

### Open Questions
```

## Anti-Patterns

- Creating one markdown page per uploaded/pasted item by default.
- Summarizing raw content without identifying the target workstream.
- Dropping tasks or decisions because they were embedded in a source.
