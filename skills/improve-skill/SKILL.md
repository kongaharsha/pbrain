---
name: improve-skill
description: Convert explicit feedback about a P-Brain skill or project-control workflow into a small, evidence-backed, approval-gated improvement. Use when the user asks to improve a skill, reports that a skill response was unhelpful, or asks to capture a project-chat correction for future behavior.
---

# P-Brain Improve Skill

Improve skills from real feedback without silently changing the operating model.

## Workflow

1. Capture feedback from the current chat only when the user explicitly says to capture it, invokes this skill, or has enabled project-level feedback capture. Useful entry phrases include `P-Brain feedback: ...`, `capture that as an improvement`, and `improve the update skill`. Do not assume every disagreement, clarification, or rewrite is reusable feedback.
2. Identify the target: a P-Brain skill, resolver route, or project-control bundle (`AGENTS.md`, operating ledger, and context files). Read the relevant surface and any existing approved evaluation artifacts.
3. If the feedback concerns a current deliverable, fix that deliverable first. Then extract only the reusable rule: the failure pattern, desired behavior, and a testable prevention criterion. Do not record a one-off preference as a permanent rule.
4. Write the private, source-linked candidate to `0. Context/Conversation Archive/Improvement Review.md` for a project-control target, or stage a de-identified candidate in `skills/<target>/eval/feedback-candidates.md` for a reusable P-Brain skill. Never copy project names, people, client data, transcripts, or raw chat excerpts into the reusable repository.
5. Check for duplicates or conflict with existing guidance. Classify the candidate as one of: `prompt-fixable`, `routing-miss`, `context-health`, `spec-gap`, or `deterministic-codifiable`.
6. Produce a compact proposed change set: exact file and section, behavior gained, risk/trade-off, evidence, and one acceptance test. Prefer the smallest change that prevents the recurrence.
7. Ask for approval before changing any `SKILL.md`, resolver, `AGENTS.md`, operating ledger, automation, or benchmark. When `request_user_input` is available, use it for up to three independent proposals; in Codex hosts exposing `AskUserQuestion`, use that native UI. Otherwise present a numbered proposal and wait for explicit approval.
8. After approval, apply only the approved edit, validate a target skill with the skill-creator quick validator, and add a dated receipt in the target's private or reusable evaluation location.

## Guardrails

- Feedback capture is not automatic memory. Save only explicit feedback or a user-approved opt-in capture.
- A project opt-in may capture correction turns from its own archived conversations into the private review queue. It cannot silently export or read every Codex conversation across projects.
- Never mutate frontmatter, triggers, or routing merely to improve wording; change them only when the approved problem is actually routing or invocation scope.
- Do not use a benchmark derived from the skill's own specification as proof of user value. Label it `SPEC-DERIVED`; label cases based on observed, approved feedback `HISTORY-IMPLIED`.
- Never auto-apply an optimizer proposal, including when invoked by a scheduled job.
- Treat a skill change as a hypothesis until it passes an approved benchmark or a clearly stated manual verification.

## Output

Report the candidate rule, classification, proposal, acceptance test, and approval status. After an approved change, report the modified files and validation result.
