---
name: conversation-capture
description: Export an explicitly selected Codex conversation into a private P-Brain project archive and stage its reusable learnings or evaluation candidates for review. Use when the user asks to save, export, archive, or evaluate a project chat/conversation.
---

# P-Brain Conversation Capture

Turn selected conversations into private project evidence and reviewable improvement signals without harvesting chat history by default.

## Workflow

1. Confirm the project or private global-brain destination and the conversation scope: current task, named Codex task, or user-provided transcript. Do not enumerate or export conversations across projects unless the user has explicitly selected them or opted into a defined project-level capture policy.
2. Use the host's native conversation-read/export capability when available. If it is unavailable, ask for an exported transcript or capture only the material supplied in the current chat. Never scrape local session stores opportunistically.
3. Ask whether to save a decision-focused summary or the full transcript. Default to a decision-focused summary. Full transcript export requires explicit consent because it may contain sensitive project material.
4. Use the declared project archive location, defaulting to `0. Context/Conversation Archive/YYYY/MM/YYYY-MM-DD--short-title.md`. Create the archive folder only on the first explicitly approved capture. Include date, source task identifier when available, project/workstream, capture mode, sensitivity, source links, decisions, actions, unresolved questions, and a short summary. Keep the raw export alongside it only when explicitly approved.
5. Update `0. Context/Conversation Archive/Archive Index.md` with a compact link and status. Do not duplicate the conversation in the Workstream Ledger; link it from the relevant workstream page/action log only when it changes project truth.
6. Extract only genuine candidates: recurring feedback becomes an item in `Improvement Review.md`; a testable observed behavior can become a proposed Autobench case. Keep these candidates private until a user approves their de-identification and promotion to a reusable P-Brain skill evaluation.
7. If the conversation changed current project truth, hand the decision/action evidence to `project-update`. If it is a reusable workflow miss, hand the candidate to `improve-skill` or `skill-evals`; each remains approval-gated.

## Rules

- The conversation archive is private project evidence, not the P-Brain plugin repository and not a substitute for the operating ledger.
- Record the source, event date, and capture date. Later corrections append or supersede; they do not rewrite history.
- Never infer that every chat should be remembered. Default capture is explicit; any project-level automatic capture must be separately opted into and narrowly scoped.
- Do not export another person's conversation or use unavailable connector/session data.

## Output

Report the archive record, capture mode, source scope, proposed learning/evaluation candidates, and any `project-update` handoff required.
