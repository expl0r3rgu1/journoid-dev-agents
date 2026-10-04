---
description: Import the team's OpenCode setup, preserving only your interface preferences
agent: build
subagent: false
---

Make this user's global OpenCode V2 setup match the current journoid-dev-agents
checkout. Preserve only personal interface preferences, not personal agent or
server behavior. This request authorizes replacement of the managed configuration
after backup, not repository changes, Git pulls, publishing, or service restarts.

1. Load the `opencode` skill. Read this repository's README and source files, then
   inspect the user's existing configuration. Use V2 documentation for syntax;
   do not introduce plugins, dependencies, or orchestration to perform the import.
2. Resolve the destination as `$XDG_CONFIG_HOME/opencode`, or
   `~/.config/opencode` when unset. Check symlinks: never modify this checkout
   through a linked destination; stop and ask if source and destination overlap.
   Create private timestamped backups outside the repository and OpenCode's
   discovery directories before replacing anything. Never print secret values.
3. Preserve the user's interface preferences in global `cli.json`: merge the
   repository's `cli.json` as defaults, with existing user values taking
   precedence, including nested settings. For V1 users, follow
   https://opencode.ai/v2/docs/migrate-v1/ to migrate supported terminal preferences
   from global `tui.json(c)` first if needed; do not copy the repository's legacy
   `tui.json` over them.
4. Replace the global server configuration with repository `opencode.json`, and
   global `AGENTS.md` with repository `AGENTS.md`. Do not merge old providers,
   models, permissions, MCP servers, plugins, or instructions. If both global
   `opencode.json` and `opencode.jsonc` exist, back up and retire the duplicate so
   old settings cannot remain active. Keep separately stored authentication,
   environment variables, and session data untouched; do not retain old server
   settings merely because they contain inline credentials. Report required
   environment variable names without exposing values.
5. Replace the global definitions with the repository's definitions:
   - `agent/*.md` → global `agents/`
   - `commands/*.md` → global `commands/`
   - `skills/<id>/` → global `skills/<id>/`, including supporting files

   Archive stale personal definitions and their V1 discovery aliases (`agent/`,
   `mode/`, `modes/`, `command/`, `skill/`, `plugin/`, `plugins/`) outside discovery
   paths, so extra definitions do not survive the import. Limit replacement to
   these managed paths; do not wipe the configuration directory. **Never import
   `.opencode/`**, especially this command: `/update-opencode` stays project-only.
   Do not import repository configuration backups.
6. Validate configuration and discovery, including the absence of stale global
   definitions. Flag incompatible repository plugins instead of silently
   substituting them. Report imported paths, preserved interface preferences,
   backup location, and blockers. Do not claim checks that were not actually run.
