---
name: project-update
description: Capture a substantial chat or reconcile changed project evidence into durable P-Brain memory. Use when the user asks to save, sync, capture, update context, record decisions, refresh stakeholders, run a daily update, reconcile new files, or make the project ready for a new chat.
---

# P-Brain Project Update

Capture material work in a detailed evidence history, then reconcile the smallest possible current-control change.

## Workflow

1. Read `AGENTS.md`, `Project Operating Ledger.md`, and the relevant recent evolution records. If the project uses the older design, follow its declared ledger until `project-setup` retrofits it.
2. If the project declares a needs-review or duplicate-review queue, inspect it before reconciling other evidence and follow the approval-queue protocol.
3. Identify durable changes: decisions, task changes, stakeholder information, source files, deliverables, folder changes, assumptions, risks, and unresolved questions. For any source in a declared needs-review queue, complete the interactive transcript-review gate before making a durable change.
4. Add a detailed `EV-YYYY-MM-DD-NN` record for a material chat or approved source. Include captured timestamp and event date, source paths, record status, primary domain, linked outcome/workstream/task/decision IDs, synthesis, decisions, actions, evidence gaps or conflicts, and exact current-control changes.
5. Update the affected `Project Operating Ledger.md` entry only where present truth changed. Replace superseded tasks or positions, retain the `EV-` link, and do not copy the full synthesis.
6. Update `Project Context.md`, `Stakeholder Map.md`, `Folder Map.md`, or the global project card only when the change belongs there. Change `AGENTS.md` only for an accepted operating-rule update.

## Daily Reconciliation

When asked for a daily update, reconcile the sources changed since the most recent `DS-YYYY-MM-DD` record. Add one `DS-YYYY-MM-DD` batch even when no current-state change is found. It must state the capture timestamp, sources considered, sources with no durable change, new or linked `EV-` records, current-control changes, open review-queue items, and any learning candidate. `daily-prep` reads this history; it does not write the daily update by default.

## Approval-Queue Protocol

Apply this protocol only when the project declares a needs-review folder.

1. Inspect the needs-review folder on every P-Brain update.
2. For each queued source, read enough content and metadata to infer meeting date, primary decision area, record type, proposed canonical filename, final destination, related workstream/artifact, and likely current-control changes.
3. Use the interactive approval tool for every routing decision. When `request_user_input` is available, invoke it rather than asking in prose; ask up to three transcript-routing questions per batch, each offering: approve the recommended route, choose a different destination, or keep in review. In Codex hosts that expose `AskUserQuestion` instead, invoke that native tool. Each question must show the source file, recommended destination, proposed filename, rationale, confidence, and the ledger/context/artifact pages that would change. Use a numbered prose proposal only when neither interactive tool is available, then wait for an explicit response.
4. Do not rename, move, delete, create an `EV-` record, or update current-control pages for a queued item until the user approves that item's route. Once approved, apply the selected route and related context updates in the same turn, then report the completed changes.
5. Inspect any declared duplicate-review folder. Identify the canonical copy and report redundant candidates, but do not delete them without explicit approval.
6. Include concise queue status in every update output, even when unchanged or empty.

## Rules

- Preserve human-authored assessments and raw source files. Corrections create later records; they do not erase prior evidence.
- Do not create routine chat transcripts or free-standing notes; use the declared evidence log.
- Do not update legacy TODOs, indexes, or distributed ledgers in a centralized project unless explicitly requested.
- Do not treat one chat as sufficient reason to rewrite shared instructions. Record a learning candidate and require recurring evidence plus user acceptance before promoting it.

## Output

List the evolution/daily record created, current-control changes, supporting files updated, queue status, and anything remaining open.
