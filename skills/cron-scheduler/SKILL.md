---
name: cron-scheduler
description: Schedule recurring pbrain checks using Codex automations. Use for /pbrain:cron-scheduler, reminders, daily prep, end-of-week summaries, portfolio refreshes, stale project checks, and recurring project maintenance.
---

# pbrain Cron Scheduler

Use Codex automations to schedule recurring pbrain routines.

## Contract

This skill guarantees:

- Jobs use thin prompts that invoke pbrain skills instead of embedding long procedures.
- Recurring jobs are idempotent and safe to re-run.
- Schedules avoid obvious collisions by staggering jobs in 5-minute offsets.
- Quiet hours are respected unless the user explicitly asks for wake-up behavior.
- Outputs are saved to the correct local project or global portfolio brain.

## Workflow

1. Clarify cadence only if not already specified.
2. Choose the correct automation type:
   - heartbeat for follow-up in the current thread
   - cron for detached recurring workspace jobs
3. Suggested recurring jobs:
   - daily task prep each weekday morning
   - portfolio index refresh daily or weekly
   - end-of-week summary on Friday afternoon
   - `update` weekly for active local projects
   - `maintain` weekly for local projects and/or global pbrain
   - weekly global reconciliation that scans registered folders, updates local ledgers, then refreshes `PROJECTS.md`, `PORTFOLIO.md`, `TASKS.md`, and stale items
4. The automation prompt must name the pbrain folder/project paths and expected output.

## Phases

1. Define job name, scope, target brain path, cadence, and output file.
2. Validate whether the job is local project or global portfolio.
3. For global jobs, read registered project folders from `PROJECTS.md`; if missing, ask the user to provide the list before scheduling.
4. For weekly maintenance, use this order: `update` on each registered local project, `maintain` on each registered project, then `global-index` / `global`.
5. Stagger schedule away from other pbrain jobs when possible.
6. Ensure prompt is thin: "Use $eow-summary for <path> and write the result to <output>."
7. Register the automation through Codex automations.

## Output Format

```markdown
Scheduled: <job name>
Cadence: <human schedule>
Target: <project or portfolio path>
Skill: <pbrain skill>
Output: <file or thread response>
Next run: <if known>
```

## Rules

- Do not hand-write raw scheduler files.
- Use the app automation tool when available.
- Keep recurring prompts self-sufficient.
- Do not schedule duplicate jobs for the same target/cadence.
- Do not send notifications during quiet hours unless requested.
- Installing the plugin should not silently create automations. Ask or act only when the user explicitly requests recurring maintenance.
- Weekly global reconciliation should keep links fresh in both directions: global registry/index to local project ledgers, and local folder maps/AGENTS to the global pbrain when registered.

## Anti-Patterns

- Creating one giant recurring prompt with all pbrain instructions inline.
- Scheduling every job at the same minute.
- Making jobs that append duplicate weekly summaries or task entries.
- Scheduling portfolio jobs that cannot find registered project paths.
