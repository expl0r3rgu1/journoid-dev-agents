---
description: Update your global OpenCode setup from this repository, preserving personal settings
agent: build
subagent: false
---

Update this user's global OpenCode V2 setup from the current journoid-dev-agents
checkout. This request authorizes the local configuration import, not changes to
the repository, Git pulls, publishing, or shared-service restarts.

1. Load the `opencode` skill. Read this repository's README and source files, then
   inspect the user's existing configuration. Use V2 documentation for syntax;
   do not introduce plugins, dependencies, or orchestration to perform the import.
2. Resolve the destination as `$XDG_CONFIG_HOME/opencode`, or
   `~/.config/opencode` when unset. Create private timestamped backups of files
   that will change, outside this repository and OpenCode's discovery directories.
   Never print credentials or secret configuration values.
3. Merge shared `opencode.json` settings into the existing global
   `opencode.json`/`opencode.jsonc`, preserving JSONC comments and unrelated user
   settings. Keep the repository's `lsp` setting project-local. Preserve personal
   providers, models, credentials, and stricter permission rules; ask before
   overwriting conflicting personal customizations or relaxing restrictions.
   Permission rules are ordered: keep personal restrictions after broad shared
   allows so the import cannot silently override them.
   Merge `cli.json` into global `cli.json` and `AGENTS.md` into global `AGENTS.md`,
   preserving unrelated preferences and instructions. If both global JSON and
   JSONC files exist, resolve their precedence before editing; do not create a
   competing configuration file.
4. Import repository-managed definitions using these mappings:
   - `agent/*.md` → global `agents/`
   - `commands/*.md` → global `commands/`
   - `skills/<id>/` → global `skills/<id>/`, including supporting files
   Update matching shared definitions; keep unrelated user definitions. **Never
   import `.opencode/`**, especially this command: `/update-opencode` must remain
   available only in this project. Do not import `tui.json` or configuration
   backups into a V2 setup.
5. Validate the edited configuration and check that the imported agents, commands,
   and skills are discoverable. Report changed paths, backup location, conflicts
   left unresolved, and missing environment variables without exposing values.
   Do not claim successful validation for checks that were not actually run.
