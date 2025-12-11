---
description: Commit local changes in atomic commits
model: github-copilot/gpt-4.1
agent: build
subtask: true
---

# Commit Changes
Analyze git changes and propose a commit plan.

## Additional Instructions
$ARGUMENTS

## Commit Types
- **fix:** Bug fixes
- **feat:** New features
- **chore:** Non-functional tidying
- **refactor:** Code restructuring without behavior change
- **docs:** Documentation updates
- **ci:** CI/CD changes

## Process
1. Run `git status -s` to see changed files
2. Use `git diff` to understand the changes
3. Group related files and draft commit messages in `type: description` format (imperative mood)
4. Return ONLY the proposed commit plan to the main session in this format:

## Proposed Commits
For each commit:
- **Files:** list of files
- **Message:** `type: description`

Do NOT execute any commits. Only return the plan for the user to review in the main session.

