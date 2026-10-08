# pbrain installation for agents

Use this guide when the user asks to install pbrain from https://github.com/kongaharsha/pbrain.

Read this guide and [RESOLVER.md](RESOLVER.md) before making changes. Resolve the user's operating system, agent environment, intended checkout, and Codex home from existing context. Summarize the concrete changes before installation; obtain approval when the user has not already authorized them. Preserve unrelated configuration and existing checkouts. Installation does not authorize project setup or recurring automations.

## Markdown playbooks

Clone to a stable playbook folder:

```bash
git clone https://github.com/kongaharsha/pbrain.git ~/pbrain
```

Tell the agent to read `RESOLVER.md` first and follow the matching `skills/<name>/SKILL.md`. If the user wants persistent project guidance, add the actual checkout location to the project's agent instructions with their authorization.

## Codex plugin checkout

The default Windows checkout is `%USERPROFILE%\.codex\plugins\pbrain`; use a configured Codex home when it differs.

```powershell
New-Item -ItemType Directory -Force -Path "$HOME\.codex\plugins"
git clone https://github.com/kongaharsha/pbrain.git "$HOME\.codex\plugins\pbrain"
```

On macOS or Linux:

```bash
mkdir -p ~/.codex/plugins
git clone https://github.com/kongaharsha/pbrain.git ~/.codex/plugins/pbrain
```

If the target exists, inspect its origin, branch, status, and local changes before updating. For a clean checkout on the tracked branch:

```bash
git -C ~/.codex/plugins/pbrain pull --ff-only
```

```powershell
git -C "$HOME\.codex\plugins\pbrain" pull --ff-only
```

Do not overwrite a non-Git directory, reset local changes, or replace another repository. Reconcile the existing installation with the user when necessary.

## Registration

Cloning the folder does not confirm that the host has enabled the plugin. Use the host's available plugin registration mechanism and inspect its existing local marketplace/configuration format. Preserve other plugins and settings; do not invent a registration format or assume automatic discovery.

The package entry point is `.codex-plugin/plugin.json`:

```json
{
  "name": "pbrain",
  "skills": "./skills/"
}
```

Verify registration and visible names using the host's tools when available. A restart may be needed to reload skills. Report enabled status as unverified if it cannot be checked.

## Package validation

1. Parse `.codex-plugin/plugin.json` as JSON and confirm its skill path exists.
2. Confirm all ten skill directories contain `SKILL.md` and their frontmatter names match their directories.
3. Confirm `RESOLVER.md` and `assets/templates/` are present.
4. Confirm the package contains reusable instructions and templates rather than project evidence or conversation archives.

The expected visible skill names are:

```text
pbrain:automation-scheduler
pbrain:conversation-capture
pbrain:daily-prep
pbrain:daily-task-manager
pbrain:enrich-brain
pbrain:improve-skill
pbrain:operating-review
pbrain:project-setup
pbrain:project-update
pbrain:skill-evals
```

For playbook-only use, these names identify the corresponding directory under `skills/`; a plugin runtime is not required.

## Handoff

Report the checkout location, installed form, package validation, and plugin enablement status if applicable. The first project workflow is `project-setup` for either a new folder or an existing project. Central Brain creation is part of `project-setup` only when explicitly requested. Follow [RESOLVER.md](RESOLVER.md) for subsequent work.
