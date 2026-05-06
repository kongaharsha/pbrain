---
name: migrate
description: Add pbrain to an existing project folder without altering existing user files. Use for /pbrain:migrate, existing project setup, scanning scattered project work, identifying workstreams, and creating AGENTS.md, .context, and WORKSTREAM.md ledgers.
---

# pbrain Migrate

Add a pbrain context layer to an existing project folder.

## Workflow

1. Identify the target project folder.
2. Check whether the global pbrain exists at `C:\Users\harsha.konga\Project Brain\`.
   - If it exists, plan to register or refresh this project in the global portfolio brain after migration.
   - If it does not exist, continue migration locally and mention that global registration can happen later with `global-setup`.
3. Scan before writing:
   - top-level folders and one level deep
   - existing `AGENTS.md`, `CLAUDE.md`, READMEs, summaries, proposals, docs, decks, sheets
   - existing context layers such as `.context/`, `0. Context/`, or `.GPT/`
   - likely workstream folders
   - local workstream `Agents.md`, SOPs, `Conversations/`, and `transcripts/`
   - source material and output locations
   - file dates that help reconstruct progress
4. Present a concise migration readout if there are multiple plausible workstream groupings.
5. Create new pbrain files only. Do not move, rename, edit, or delete existing user files.
6. If `AGENTS.md` already exists, merge carefully or create a clearly named pbrain section only after confirming compatibility.
7. If global pbrain exists, update its project registry/index with this project path, context folder, active workstreams, status, and next check date.

## Migration Output

- `AGENTS.md` with Mira persona and local file discipline.
- context files synthesized from actual folder evidence, preserving the project's current context folder convention where one exists.
- `WORKSTREAM.md` ledgers for each confirmed or strongly inferred workstream.
- `Folder Map.md` that explains what exists and where fresh direction lives.

## Ledger Rules

- Reconstruct timeline only from reliable evidence.
- Label inferred context as inferred.
- Link source files in `Important Source Files`.
- Keep separate markdown creation minimal.
- Preserve existing folder conventions. Do not create a nested `workstreams/` folder when the current folder structure already has numbered/direct workstream folders.
- Keep local `Agents.md` files lightweight as operating guides. Put session history, decisions, and status in `WORKSTREAM.md`.
- Always check for the global pbrain during migration. Do not silently ignore it.
- If a global pbrain exists, migration should leave a backlink trail: global project registry points to the local project, and local `AGENTS.md` or folder map notes the global pbrain path.
