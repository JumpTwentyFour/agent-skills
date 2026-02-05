---
name: create-github-issue
description: Writing and maintaining GitHub issues. Use when creating new issues, editing issue titles/bodies or cleaning up issue metadata (types, labels).
agent: Explore
allowed-tools: Read, Bash, Grep, Glob, AskUserQuestion
---

### Determine the repository

1. Determine the target repository by running:
```bash
   git remote get-url origin
```
2. Parse the owner and repo name from the URL
3. Use these values when calling the GitHub MCP tools

# Writing and maintaining GitHub issues
Standards for issues.

## Title Standards
- **Sentence case** - Capitalize only the first word and proper nouns.
- **No type prefixes** - Use GitHub issue types, not Bug:, Feature: etc...
- **Imperative mood for enhancements** - "Fix N+1 issue" not "Fixing N+1 issue"
- **Descriptive for bugs** - Describe the symptom "Failed to allocate booking to staff member"
- **Specific** - "Be specific, it must be understandable without opening the issue body"

## Issue types
Set via the `issue_write` after creating the issue:

- **Bug** - Something isn't working as expected
- **Feature** - New capability or improvement
- **Task** - Internal task or chore
- **Epic** - Large feature or project

## Bug

When writing a bug issue, after the user has explained what the problem is, explore the codebase for possible solutions. Use Chrome if needed to explore the problem. Do not implement the fix, instead write clear and concise explanation under "Proposed Solution" in the issue body.

## Big Task Detection

Before creating an issue, evaluate whether the request is a "big task" that should be an Epic with subtasks. A task qualifies as big if it has:

- **Multiple distinct components** - The work involves several separate features or pieces
- **Cross-cutting concerns** - Requires work across different areas (frontend, backend, database)
- **Extended scope** - Would take more than a few days to complete
- **Multiple acceptance criteria** - Has several user stories or distinct outcomes
- **System-wide impact** - Affects multiple parts of the codebase

When a big task is detected, follow the Epic Creation Workflow below instead of creating a single issue.

## Epic Creation Workflow

When you identify a big task:

1. **Gather context using AskUserQuestion:**
    - What are the main goals or outcomes?
    - What user stories or acceptance criteria exist?
    - Are there dependencies between different parts?
    - What priority should the subtasks have?

2. **Create the Epic issue first** using the Epic Body Standards below

3. **Create individual subtask issues** linked to the Epic

4. **Apply appropriate labels** to Epic and all subtasks

### Epic Body Standards

Epic issues should follow this structure:

```markdown
## Overview
[1-2 sentence goal statement]

## User Stories / Acceptance Criteria
- [ ] As a [user], I want [feature] so that [benefit]
- [ ] [Additional criteria]

## Subtasks
- [ ] #XX - [Subtask title]
- [ ] #XX - [Subtask title]

## Dependencies
[Note any ordering requirements between subtasks]

## Milestone
[Target milestone or timeline if applicable]
```

### Subtask Linking

When creating subtasks for an Epic:

1. **Create each subtask** with GitHub MCP `issue_write`
2. **Reference the parent Epic** in each subtask body:
   ```markdown
   Part of #[epic-number]
   ```
3. **Update the Epic** after creating subtasks to add issue links to the Subtasks checklist
4. **Set appropriate issue type** (usually Task or Feature) for each subtask

## Labels

| name | color | description                       |
|------|-------|-----------------------------------|
| Security | e11d48 | Security issue                    |
| Performance | f59e0b | Performance issue                 |
| Stability | 8b5cf6 | Stability issue                   |
| Backend | 3b82f6 | Backend work with Laravel/PHP     |
| Frontend | 06b6d4 | Frontend work with JavaScript/CSS |
| Database | 10b981 | Work involving the database       |
| Code Quality | 6366f1 | Code quality issue                |
| Upgrade | ec4899 | Dependency upgrade work           |
| Critical | dc2626 | Critical issue                    |
| High | ea580c | High urgency issue                |
| Medium | f59e0b | Medium urgency issue              |
| Low | 84cc16 | Low urgency issue                 |


### Label Management Process

**IMPORTANT:** Before applying labels to an issue, you must ensure the labels exist in the repository. Follow this process:

1. **Check existing labels:**

Use the GitHub MCP  `list_label` tool to list labels.

2. **Create missing labels:** 

For each label you need that doesn't exist, create it with the appropriate color using the GitHub MCP `label_write` tool.

3. **Apply labels to the issue:**

After ensuring labels exist, apply the appropriate ones using the GitHub MCP `issue_write` passing the `labels`.

**Apply labels based on issue content:**
- Security issues → Security, Critical (if P1), appropriate technical area (Backend/Frontend/Database)
- Performance issues → Performance, appropriate urgency label, appropriate technical area
- Stability issues → Stability, appropriate urgency label, appropriate technical area
- Code quality issues → Code Quality, appropriate technical area

## Issue Body Standards

### Bug Reports
1. Clear description of issue.
2. Steps to reproduce
3. Expected vs actual behaviour
4. Proposed solution

### Feature Requests
1. Problem statement (What problem will this feature solve)
2. Proposed solution (How will it be implemented technically)
3. Tradeoffs (Any particular tradeoffs)
4. Affected areas (Areas of the codebase it will affect)

## IMPORTANT
- Never include "Generated with Claude Code"
- Never use title case for descriptions - use sentence case
- **Always follow the Label Management Process** - Check for existing labels, create missing ones, then apply appropriate labels to every issue you create
- When creating issues from the Future Work Checklist, map the priority (P1=Critical, P2=High, P3=Medium, P4=Low) and category (Security, Performance, Stability, Code Quality) to appropriate labels

