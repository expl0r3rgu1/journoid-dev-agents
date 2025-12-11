---
description: Plan a feature or task with structured output to PLAN.md
agent: plan
---

# Planning

$ARGUMENTS

## PLAN.md Output Requirement

You MUST write and maintain a `PLAN.md` file in the project root throughout this planning session.

**Update PLAN.md frequently** - after each significant insight or decision. This prevents losing work if the context window fills up.

The ONLY file you may write to is `PLAN.md`. Do not implement anything.

## PLAN.md Structure

```markdown
# Plan: [Feature/Task Name]

## Overview
Brief description of what will be implemented.

## Goals
- Goal 1
- Goal 2

## Tasks
- [ ] Task 1
  - [ ] Subtask 1.1
- [ ] Task 2

## Implementation Details
Technical approach and architecture decisions.

## Files to Modify/Create
- `path/to/file.ts` - Description

## Dependencies
- Libraries or services needed

## Risks and Considerations
- Edge cases, performance, security

## Open Questions
- Remaining uncertainties
```
