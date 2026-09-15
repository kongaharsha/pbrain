---
name: skill-evals
description: Create or run a privacy-safe, human-reviewed behavioral benchmark for a P-Brain skill, resolver route, or project-control bundle. Use when the user asks to benchmark, evaluate, regression-test, or improve a skill, AGENTS.md, or project context from approved feedback or usage history.
---

# P-Brain Skill Evals

Build evidence for skill changes; do not rewrite skills.

## Workflow

1. Require a named target: a P-Brain skill, resolver route, or project-control bundle. For a project-control evaluation, define the exact bundle and desired behavior before reading it: for example, whether `AGENTS.md` and the operating ledger make a new transcript route and approval gate unambiguous.
2. Mine only user-approved, locally available feedback or usage windows. An explicitly exported project conversation in `0. Context/Conversation Archive/` is a valid private substrate. A usable window includes the ask, the response/action, and the follow-up correction or outcome. Do not claim history exists when it has not been inspected.
3. If no usable history exists, write an honest no-history report or, at the user's request, stage a clearly labeled `SPEC-DERIVED` baseline. Never fabricate realistic-looking history.
4. Stage a reusable-skill evaluation at `skills/<target>/eval/autobench-YYYY-MM-DD.md`, or a project-control evaluation at `0. Context/Conversation Archive/Evaluations/autobench-YYYY-MM-DD.md`, with `status: PENDING-HUMAN-APPROVAL`. Include an evaluation contract, 4-8 replayable cases where enough evidence exists, expected behavior, hard failures, and source labels (`HISTORY-IMPLIED` or `SPEC-DERIVED`).
5. De-identify every case that enters the reusable repository. Project-local control evaluations may cite their private archive record and source paths but must not be copied to the reusable skill repository. If safe de-identification is not possible, keep the case private and report the coverage gap.
6. Ask the user to approve, edit, defer, or discard the staged evaluation. Use `request_user_input` or native `AskUserQuestion` when available; otherwise wait for explicit prose approval.
7. Only after approval, run the cases in a non-mutating/dry-run form where possible. Record the tested files/content hash, date, case outcomes, failures, and limitations next to the staged evaluation under `benchmark-runs/YYYY-MM-DD.md`.
8. Route failures to `improve-skill` as proposals. Skill Evals never changes `SKILL.md`, `RESOLVER.md`, schedules, or project control files.

## Evaluation rules

- A user correction is the strongest evidence; preserve its pattern, not its private wording.
- Keep routing tests separate from behavioral tests. A skill firing when it should not is a routing-miss case for `RESOLVER.md`, not a quality score for the skill body.
- Do not present a score as authoritative when cases are thin, synthetic, or manually judged. State coverage and limitations.
- Multi-model judging, paid tooling, external connectors, and scheduled runs are opt-in. Verify that every requested judge actually returned before relying on a panel result.
- A scheduled benchmark may create a report only from previously approved cases. It may never generate or apply a skill edit.
- Autobench can evaluate whether a project control bundle works: routing clarity, source traceability, approval-gate compliance, current-vs-history separation, and task/ledger consistency. It cannot prove that prose is universally "good"; each test needs a concrete expected behavior.

## Output

State the target skill, evidence coverage, staged/approved status, pass/fail results when run, limitations, and the next proposed improvement (if any).
