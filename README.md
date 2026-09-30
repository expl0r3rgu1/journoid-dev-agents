# Journoid OpenCode configuration

OpenCode settings, custom agents, and commands. `opencode.json` uses native V2
configuration and keeps the project-specific LSP setting enabled.

## Credentials

Set `CONTEXT7_API_KEY` in your environment before using the Context7 MCP server.
API keys and other credentials are not included in this repository.

## Terminal settings

`cli.json` is a template for the global OpenCode V2 terminal configuration. V2
does not load project-local CLI settings. To use it, merge its settings into
`~/.config/opencode/cli.json` (or `$XDG_CONFIG_HOME/opencode/cli.json` when
`XDG_CONFIG_HOME` is set). Preserve any other global preferences you need.

`tui.json` is retained for legacy OpenCode clients. The agent definitions and
existing configuration backups are also preserved.
