# P-Brain Resolver

P-Brain has eight everyday skills and two explicit improvement skills. Use the smallest one that matches the request.

| User intent | Skill |
|---|---|
| Create or retrofit a project and its Central Brain registration | `project-setup` |
| Deepen a project, workstream, stakeholder, source set, or strategic question | `enrich-brain` |
| Capture material work from this chat or reconcile project changes into durable memory, including an end-of-day / daily update | `project-update` |
| Start the day with a focused project or portfolio brief and plan | `daily-prep` |
| Add, complete, defer, or review a task in the appropriate project or portfolio control view | `daily-task-manager` |
| Propose a recurring project check, status reconciliation, review queue, or reminder | `automation-scheduler` |
| Assess P-Brain/project health and publish advisory guidance | `operating-review` |
| Export an explicitly selected Codex conversation to the private project archive and extract review candidates | `conversation-capture` |
| Explicitly improve a P-Brain skill or project-control workflow from approved feedback | `improve-skill` |
| Explicitly build or run a privacy-safe behavioral benchmark | `skill-evals` |

## Shared Operating Model

- **Project Brain:** a project folder in OneDrive is the private source of truth for its evidence, current operating ledger, conversation archive, and deliverables.
- **Central Brain:** a separately configured private OneDrive folder is the cross-project source of truth for the portfolio index, cross-project tasks, aggregate advisor guidance, and an improvement backlog. It links to project brains; it does not mirror their evidence.
- **P-Brain repository:** a local Git checkout is the shareable operating-system layer: skills, templates, generic tests, and approved de-identified improvements. It must never be used as a working project archive or Central Brain.
- Each project declares its operating model in `AGENTS.md`.
- The preferred local authority is a concise context-folder `Project Operating Ledger.md`; `Evidence & Evolution Log.md` is its append-only, timestamped, source-linked history. Existing `Workstream Ledger.md` files may remain as reference history.
- Tasks can sit under a workstream or a cross-cutting outcome. Link records by stable IDs instead of duplicating them.
- File a transcript once by primary decision area; link secondary relevance from the operating ledger and evolution log.
- When a project declares a needs-review queue, `project-update` and `enrich-brain` present transcript-routing proposals for explicit approval before moving a transcript or changing durable project context.
- `Project Context.md`, `Stakeholder Map.md`, and `Folder Map.md` hold only durable framing, people, and navigation.
- The Central Brain contains `AGENTS.md`, `PROJECTS.md`, compact `PORTFOLIO.md`, cross-project-only `TASKS.md`, `INTERDEPENDENCIES.md`, and an `Improvement Backlog.md` of generalized cross-project candidates.
- Do not create duplicate TODOs, indexes, or per-folder ledgers unless the project explicitly uses the distributed-ledger exception.
- `P-Brain Advisor Guidance.md` is advisory only: it can inform another skill's review, but never overrides an operating ledger, source, or explicit user instruction.
- Skill feedback, benchmarks, and optimization proposals are kept separate from project evidence. Never put client names, transcripts, or proprietary examples into reusable P-Brain skill-evaluation artifacts.
- A project-local `0. Context/Conversation Archive/` may hold explicitly approved conversation exports. It is a private evidence corpus, not part of the reusable P-Brain skill repository. Reusable benchmark cases retain only de-identified behavior patterns.
