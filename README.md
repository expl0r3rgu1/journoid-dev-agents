# Journoid OpenCode configuration

OpenCode settings, custom agents, commands, and skills. `opencode.json` uses native V2
configuration and keeps the project-specific LSP setting enabled.

## Update your local setup

Open OpenCode in this checkout and run:

```text
/update-opencode
```

This project-local command asks the agent to import the shared configuration into
your user-level OpenCode directory (`$XDG_CONFIG_HOME/opencode`, or
`~/.config/opencode`). It backs up changed files, preserves unrelated personal
settings, and asks before overwriting conflicting customizations or weakening
permissions. It uses the current checkout without pulling or changing the repo.

| Repository source | Global destination                                             |
| ----------------- | -------------------------------------------------------------- |
| `opencode.json`   | Existing `opencode.json(c)`, merged; `lsp` stays project-local |
| `cli.json`        | `cli.json`, merged                                             |
| `AGENTS.md`       | `AGENTS.md`, merged                                            |
| `agent/*.md`      | `agents/`                                                      |
| `commands/*.md`   | `commands/`                                                    |
| `skills/<id>/`    | `skills/<id>/`                                                 |

`skills/parallel-work/` contains the minimal worktree and Playwright isolation
workflow. Importing it makes it discoverable in other projects without manually
invoking it for every suitable request.

`.opencode/commands/` is **project-only** and is never imported globally. This
keeps `/update-opencode` visible only inside this repository (including its
subdirectories), unlike the shared commands under `commands/`.

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
