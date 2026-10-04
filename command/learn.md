---
description: Extract non-obvious learnings from session to the AGENTS.md file to build codebase understanding
---

Analyze this session and extract non-obvious learnings to add to this project's AGENTS.md file.

What counts as a learning (non-obvious discoveries only):
- Preferences or directions from me (that didn't cause subsequent issues) that wouldn't have been followed unless explicitly requested
- Hidden relationships between files or modules
- Execution paths that differ from how code appears
- Non-obvious configuration, env vars, or flags
- Debugging breakthroughs when error messages were misleading
- API/tool quirks and workarounds
- Build/test commands not in README
- Architectural decisions and constraints
- Files that must change together

What NOT to include:
- Obvious facts from documentation
- Standard language/framework behavior
- Things already in an AGENTS.md
- Verbose explanations
- Session-specific details
- Commit workflow guidance, including message style and conflict handling; this belongs to the global `/commit` command

Process:
1. Review session for discoveries, errors that took multiple attempts, unexpected connections
2. Read existing AGENTS.md file
3. Create or update AGENTS.md
4. Keep entries to 1-3 lines per insight
5. Remove or update any information that you recognize as outdated based on the current session

After updating, summarize if the AGENTS.md file was created/updated and how many learnings you added/removed.

$ARGUMENTS
