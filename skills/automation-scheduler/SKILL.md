---
name: automation-scheduler
description: Design, validate, and only after explicit approval create or update a recurring P-Brain project cadence using the host scheduler. Use for schedules, recurring status updates, review queues, reminders, or project check-ins.
---

# P-Brain Automation Scheduler

Make recurring work safe, thin, observable, and reversible.

## Workflow

1. Define the job with the user: project/scope, purpose, skill to run, cadence, timezone, allowed writes, notification policy, and owner. Use a heartbeat for ongoing work in this Codex task unless the user explicitly asks for a standalone project cron.
2. Select a narrow, idempotent skill prompt. Examples: run `project-update` in proposal-only review mode; prepare `daily-prep`; run `operating-review`; run `skill-evals` only on already approved cases.
3. Inspect existing related automations before creating one. Avoid duplicate jobs and stagger jobs that share a project so their reports and edits cannot race.
4. Test the job once in the current conversation on a small scope before scheduling it. Confirm expected output location, idempotency, notification behavior, and that it will not mutate project control files outside its stated permission.
5. Present the complete proposed schedule in plain language and wait for explicit approval. Do not create schedules, connectors, paid services, or notifications implicitly.
6. After approval, use the host's native automation mechanism. Save an automation receipt in the project's declared context area or the private Central Brain's automation register only when the project permits it; include name, purpose, cadence, write permission, and how to pause it.

## Common approved recipes

- **Morning operating scan:** run `daily-prep`, optionally with the Outlook calendar plus recent Outlook/Teams messages from named project stakeholders. It prepares a briefing; it does not file messages or change task state.
- **Evening reconciliation:** run `project-update` against sources in the declared needs-review/inbox locations. It must surface routing and ledger proposals for approval; it cannot autonomously file transcripts, emails, or messages.
- **Weekly health and learning review:** run `operating-review`, which may refresh advisory guidance and surface recurring conversation/archive candidates. It does not change skills or operating records.
- **Periodic regression check:** run `skill-evals` only against already approved cases. It records results and proposes, rather than applies, improvements.

Email, Teams, calendar, and other connector scans are optional. Before scheduling one, confirm the connector is available, the included people/folders/time window, retention location, and whether its output is briefing-only or enters a human-reviewed source queue.

## Rules

- Scheduled `project-update`, `enrich-brain`, and transcript routing runs must remain proposal/approval-gated when they encounter new source material.
- Scheduled advisors and benchmarks may publish advisory/report artifacts, but they never apply organizational, skill, or task-status changes by themselves.
- Jobs must be idempotent: a retry must not duplicate a daily record, task, or report. Use date/run identifiers and check for an existing receipt.
- Respect user-requested quiet hours and notify only on meaningful change, failure, or required approval.
- Never embed long instructions in an automation prompt; tell it which P-Brain skill to read and the narrowly scoped outcome.

## Output

Before approval, report the proposed job, cadence, write scope, notifications, test result, and pause path. After creation, report the actual scheduler record and next intended run.
