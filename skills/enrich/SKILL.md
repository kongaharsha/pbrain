---
name: enrich
description: Enrich a pbrain topic. Use for /pbrain:enrich, deepening a workstream, stakeholder, company, market, competitor, decision, source file, or strategic theme with compiled truth, timeline updates, caveats, and source links.
---

# pbrain Enrich

Deepen project understanding around one topic.

## Contract

This skill guarantees:

- Existing pbrain context is read before external research.
- Effort scales to importance.
- Findings are source-backed and caveated.
- Durable enrichment is routed to the right local workstream ledger.

## Enrichment Tiers

| Tier | Use for | Effort |
|---|---|---|
| Tier 1 | Core workstream, board-level decision, major competitor, key stakeholder | Deep research and synthesis |
| Tier 2 | Important but bounded topic | Project files plus targeted web/source research |
| Tier 3 | Minor context needed for continuity | Quick pbrain lookup and concise ledger update |

## Workflow

1. Identify the target: workstream, stakeholder, company, market, competitor, decision, or theme.
2. Read existing local project context and relevant workstream ledgers.
3. Gather supporting sources from project files or web research if requested.
4. Produce:
   - compiled truth
   - implications for the project
   - caveats and uncertainty
   - source links
   - recommended ledger updates
5. Update the relevant `WORKSTREAM.md` findings, decision log, or source list when durable.

## Rules

- Do not create a separate enrichment page unless the topic becomes a durable reusable artifact.
- Label fact, inference, and hypothesis clearly.

## Output Format

```markdown
## Enrichment: <topic>

### Compiled Truth

### What Changed

### Implications

### Caveats

### Recommended Ledger Updates
```

## Anti-Patterns

- Enriching without checking local project context first.
- Treating one source as settled truth.
- Creating stakeholder/company/topic pages for passing mentions.
- Overwriting prior project assessments without preserving the dated change.
