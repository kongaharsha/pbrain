---
name: eow-summary
description: Write an end-of-week pbrain summary. Use for /pbrain:eow-summary, weekly project recap, scanning all workstream files and markdown files, recording progress, decisions, risks, links, and next-week priorities.
---

# pbrain End Of Week Summary

Produce a durable weekly summary for one project or the global portfolio.

## Contract

This skill guarantees:

- The week is summarized from actual workstream ledgers, markdown files, source files, and outputs.
- Decisions, progress, risks, and next-week priorities are linked to authoritative local files.
- The summary is concise enough to be useful as an executive/status note.
- Missing ledger entries discovered during the scan are flagged or fixed.

## Workflow

1. Determine week range. Default to the current Monday-Friday in the user's timezone.
2. Scan all local workstream ledgers and relevant markdown files changed during the week.
3. Include source files and outputs created or materially updated.
4. Identify what the note is for:
   - internal pbrain weekly record
   - stakeholder/email-ready EOW update
   - portfolio-level cross-project update
5. Write the summary to:
   - local project: `.context/weekly/YYYY-MM-DD.md` or `weekly/YYYY-MM-DD.md`
   - global portfolio: `weekly/YYYY-MM-DD.md`
6. Update `WORKSTREAM.md` change logs only if the weekly scan reveals missing material events.

## Structure Guidance

Do not force a single rigid format. Choose the structure that matches the project and audience, but make sure the note answers these questions:

- What was accomplished this week?
- What materially changed in the project?
- What are the key insights, decisions, or emerging implications?
- What is planned for next week?
- What risks, blockers, asks, or dependencies need attention?
- Which outputs, source files, dashboards, or attachments should the reader open?

For product/war-room style updates, include:

- key highlights
- product / workstream updates
- KPI dashboard or key metric movements
- competitor and market updates
- key risks / decisions needed
- plan for next week

For consulting/project-status style EOW emails, include:

- brief greeting and one-sentence context if needed
- focus of this week
- key accomplishments or emerging answer
- plan for next week
- process metrics such as calls completed, costs, interviews, or workplan progress when relevant
- attachments or links to materials

For internal pbrain weekly records, include:

- Executive summary
- Work completed
- Decisions made
- Important findings
- Risks and blockers
- Cross-workstream or cross-project dependencies
- Files created or updated
- Priorities for next week

## Rules

- Link back to authoritative local workstream ledgers.
- Avoid turning the note into a raw activity dump.
- Prefer one weekly note per scope/week. Re-running should update or replace the same note, not create duplicates.
- If a weekly summary changes portfolio priorities, refresh the global pbrain via `global`.

## Output Format

Use this markdown shape for a durable pbrain record:

```markdown
# End-of-Week Summary - Week Ending YYYY-MM-DD

## Executive Summary

## Work Completed

## Decisions Made

## Important Findings

## Risks And Blockers

## Dependencies

## Files Created Or Updated

## Priorities For Next Week
```

Use this shape when the user wants an email-ready status note:

```markdown
Subject: <Project> End-of-Week Update - <date>

Hello,

This week's focus was <one-sentence focus>.

## Key Accomplishments This Week

## Key Insights / Emerging Answer

## Plan For Next Week

## Process / Metrics

## Risks, Blockers, Or Asks

## Attachments / Links

Best,
<sender>
```

## Anti-Patterns

- Listing every file touched without explaining why it matters.
- Duplicating full workstream details already captured in ledgers.
- Omitting source links for decisions or factual claims.
- Creating multiple weekly notes for the same project/week.
- Writing a vague "busy week" status note with no accomplishments, next-week plan, or asks.
