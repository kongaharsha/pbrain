---
name: setup
description: Set up a new local pbrain from scratch. Use for /pbrain:setup, new strategy projects, new consulting workspaces, or when the user wants AGENTS.md, .context, and workstream ledgers created in an empty or new project folder.
---

# pbrain Setup

Create a local pbrain inside a new project folder.

## Workflow

1. Establish the target folder. Default to the current folder if the user already gave no other path.
2. Understand the project through existing prompt context and any supplied files: objective, decision, stakeholders, output format, workstreams, sources, and constraints.
3. Check whether the global pbrain exists at `C:\Users\harsha.konga\Project Brain\`.
   - If it exists, plan to register this project in the global portfolio brain after local setup.
   - If it does not exist, continue local setup and mention that global registration can happen later with `global-setup`.
4. Before editing, summarize the proposed structure if major details are ambiguous. If the user already supplied the plan clearly, proceed.
5. Create:
   - `AGENTS.md`
   - context folder files, defaulting to `.context/` for new projects unless the user requests `0. Context/` or another convention
   - `Project Context.md`
   - `TODO & Ideas.md`
   - `Writing & Slide Standards.md`
   - `Folder Map.md`
   - optional `Stakeholder Map.md` in the context folder
   - `<workstream-folder>/WORKSTREAM.md`, defaulting to `workstreams/<workstream>/WORKSTREAM.md` only when no existing/numeric folder convention applies
6. Use the template style in `assets/templates/local-agents-template.md` and `assets/templates/workstream-ledger-template.md`, but write real project-specific content.
7. If global pbrain exists, update its project registry/index with the new project path, context folder, active workstreams, status, and next check date.

## Content Rules

- `AGENTS.md` must define Mira as the default project agent persona.
- Seed each workstream with purpose, current status, artifact index, key questions, decisions and working assumptions, activity timeline/changelog, key findings, open questions, and next steps.
- Keep `.context/TODO & Ideas.md` short. It is current working memory, not a backlog archive.
- Do not create extra markdown files unless the project already needs a durable deliverable or research brief.
- If path length or existing numbering conventions matter, use direct workstream folders rather than adding an extra nesting layer.
- Always check for the global pbrain during setup. Do not silently ignore it.
- Local setup must work even when no global pbrain exists.
