# Journoid OpenCode configuration

OpenCode settings, custom agents, commands, and skills. `opencode.json` uses native
V2 configuration.

## Update your local setup

Open OpenCode in this checkout and run:

```text
/update-opencode
```

This project-local command asks the agent to import the shared configuration into
your user-level OpenCode directory (`$XDG_CONFIG_HOME/opencode`, or
`~/.config/opencode`). It backs up the managed files and replaces non-interface
configuration with this repository's configuration. Only personal interface
preferences in `cli.json` are preserved; existing values take precedence over
the repository's interface defaults. Personal models, providers, permissions,
MCP settings, instructions, and extra global definitions are not carried forward.
Separately stored authentication and session data remain untouched. It uses the
current checkout without pulling or changing the repo.

| Repository source | Global destination                                                    |
| ----------------- | --------------------------------------------------------------------- |
| `opencode.json`   | `opencode.json(c)`, replaced; competing file retired                  |
| `cli.json`        | `cli.json`, defaults merged underneath personal interface preferences |
| `AGENTS.md`       | `AGENTS.md`, replaced                                                 |
| `agent/*.md`      | `agents/`, replaced                                                   |
| `commands/*.md`   | `commands/`, replaced                                                 |
| `skills/<id>/`    | `skills/`, replaced                                                   |

Stale global definitions and legacy discovery directories are archived outside
OpenCode's discovery paths. Other projects' local configuration is not changed.

`skills/parallel-work/` contains the minimal worktree and Playwright isolation
workflow. Importing it makes it discoverable in other projects without manually
invoking it for every suitable request.

`.opencode/commands/` is **project-only** and is never imported globally. This
keeps `/update-opencode` visible only inside this repository (including its
subdirectories), unlike the shared commands under `commands/`.

## Credentials

Set `CONTEXT7_API_KEY` in your environment before using the Context7 MCP server.
API keys and other credentials are not included in this repository. Old inline
credentials are kept in the private backup, not merged into the team configuration.

## Terminal settings

`cli.json` is a template for the global OpenCode V2 terminal configuration. V2
does not load project-local CLI settings. To use it, merge its defaults into
`~/.config/opencode/cli.json` (or `$XDG_CONFIG_HOME/opencode/cli.json` when
`XDG_CONFIG_HOME` is set), with existing personal interface preferences winning.

`tui.json` is retained for legacy OpenCode clients. The agent definitions and
existing configuration backups are also preserved.
