# pbrain Install For Agents

Use this file when a user asks you to install pbrain into Codex from GitHub.

Repository:

```text
https://github.com/kongaharsha/pbrain
```

## Goal

Install pbrain as a local Codex plugin, enable it, and verify that the visible skills are cleanly namespaced as `pbrain:<skill>`.

Do not set up project brains during plugin installation unless the user explicitly asks. Installation and first-run setup are separate steps.

## Ask Before Writing

Confirm these three values if they are not obvious:

1. Operating system.
2. Codex home directory. Default on Windows: `%USERPROFILE%\.codex`.
3. Where to keep the cloned GitHub repo. Default on Windows: `%USERPROFILE%\Documents\pbrain`.

On Harsha's Windows machine, the expected defaults are:

```text
Repo clone: C:\Users\harsha.konga\Documents\pbrain
Plugin dir: C:\Users\harsha.konga\.codex\plugins\pbrain
```

## Windows Install

Run this in PowerShell:

```powershell
$RepoUrl = "https://github.com/kongaharsha/pbrain.git"
$CloneDir = "$env:USERPROFILE\Documents\pbrain"
$PluginDir = "$env:USERPROFILE\.codex\plugins\pbrain"

if (Test-Path -LiteralPath $CloneDir) {
  git -C $CloneDir pull
} else {
  git clone $RepoUrl $CloneDir
}

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.codex\plugins" | Out-Null
robocopy $CloneDir $PluginDir /MIR /XD .git | Out-Host
if ($LASTEXITCODE -gt 7) { throw "robocopy failed with exit code $LASTEXITCODE" }
```

## Enable In Codex

If Codex does not automatically discover the plugin, merge pbrain into the user's local Codex plugin marketplace and enable it. Preserve existing plugins and marketplaces.

Expected local plugin folder:

```text
%USERPROFILE%\.codex\plugins\pbrain
```

Expected plugin manifest:

```text
%USERPROFILE%\.codex\plugins\pbrain\.codex-plugin\plugin.json
```

The plugin manifest must have:

```json
{
  "name": "pbrain",
  "skills": "./skills/"
}
```

If this Codex installation uses a local marketplace file, ensure it has a pbrain entry without deleting other entries:

```text
%USERPROFILE%\.codex\.agents\plugins\marketplace.json
```

If this Codex installation uses `config.toml` plugin enablement, preserve existing config and ensure pbrain is enabled. A typical local setup uses:

```toml
[marketplaces.pbrain-local]
source_type = "local"
source = "C:\\Users\\<user>\\.codex"

[plugins."pbrain@pbrain-local"]
enabled = true
```

Use the user's actual home path. Do not overwrite unrelated config.

## Validate

After copying and enabling, verify:

1. `.codex-plugin/plugin.json` parses as JSON.
2. The `skills/` folder exists.
3. Every skill folder has a `SKILL.md`.
4. Folder names match SKILL frontmatter `name`.
5. The skill list is:

```text
cron-scheduler
daily-task-manager
daily-task-prep
enrich
eow-summary
global
global-index
global-setup
ingest
maintain
migrate
research
router
setup
update
```

Expected visible names after Codex restart:

```text
pbrain:setup
pbrain:migrate
pbrain:global-setup
pbrain:global-index
pbrain:global
pbrain:daily-task-manager
pbrain:daily-task-prep
pbrain:cron-scheduler
pbrain:update
pbrain:maintain
pbrain:eow-summary
pbrain:enrich
pbrain:research
pbrain:ingest
pbrain:router
```

## Final User Message

Tell the user:

1. Where the repo was cloned.
2. Where the plugin was installed.
3. Whether the plugin was enabled.
4. Whether validation passed.
5. That they should restart Codex if the UI has not refreshed.
6. The first command to run next:
   - `/pbrain:setup` in a new project folder.
   - `/pbrain:migrate` in an existing project folder.
   - `/pbrain:global-setup` after at least one local project is ready.
