---
name: operating-review
description: Assess P-Brain and project operating health, then publish ranked advisory guidance without changing source truth. Use for a brain checkup, project health check, workflow improvement, cadence advice, or weekly P-Brain guidance.
---

# P-Brain Operating Review

Recommend the next highest-leverage maintenance action; never silently fix the brain.

## Workflow

1. Resolve a Project Brain, the private Central Brain, or the P-Brain repository scope. Read only the applicable `AGENTS.md`, thin `Workstream Ledger.md`, relevant workstream pages/action records, review queues, task register, `RESOLVER.md`, and existing advisor guidance. Do not use the Git repository as a source of private project truth.
2. Assess: source/review freshness, unresolved decisions, stale or blocked tasks, missing source links, duplicate control state, unclear workstream ownership, archival/supersession gaps, automation collisions, and recurring feedback/benchmark failures. Identify learning opportunities only when the same correction, context failure, or workflow friction has recurred or has a clear testable prevention rule.
3. Rank only the top 1-3 findings by leverage and urgency. Distinguish `critical`, `review`, and `opportunity`. Do not repeat unchanged low-value recommendations from a prior guidance file.
4. Write or refresh `0. Context/P-Brain Advisor Guidance.md` only when the user asks for a saved report or an approved scheduled run. Mark it `status: advisory`, include generation date, evidence examined, findings, proposed next action, and a link to the applicable source/control record. Maintain distinct sections: `Active Guidance`, `Learning and Evaluation Candidates`, `Automation Candidates`, and `Decisions Required`.
5. When invoked interactively without a request to save, report the guidance in chat only. For every proposed fix, identify the responsible P-Brain skill and ask the user before invoking it or making changes.
6. When feedback/process issues recur, add an approval-needed learning/evaluation candidate to the guidance report and offer a handoff to `feedback-and-learnings:capture-learnings`, `conversation-capture`, `skill-evals`, or `improve-skill`; do not promote a learning directly into a skill.

When the same pattern appears across projects, write a generalized candidate to the private Central Brain's `Improvement Backlog.md`. Promote it to the P-Brain Git repository only after explicit review and de-identification.

## Rules

- Advisor guidance is not source truth and never overrides the operating ledger, evidence record, or user instruction.
- Read-only assessment and advisory-report writing are allowed; folder reorganizations, ledger changes, task changes, schedules, and skill edits each require their own explicit approval.
- State uncertainty and evidence gaps instead of manufacturing recommendations.
- Keep advice bounded: no more than three actionable recommendations unless the user requests a full audit.

## Output

Lead with the highest-leverage action, then show each finding, evidence, recommended skill/owner, and whether it needs approval.
