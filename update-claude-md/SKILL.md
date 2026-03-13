---
name: update-claude-md
description: After any correction from the user, update CLAUDE.md with a rule to prevent the same mistake from recurring. Use when the user corrects your behavior or says "don't do that again". Ruthlessly iterate CLAUDE.md until mistake rate measurably drops.
license: MIT
compatibility: Designed for Claude Code
metadata:
  author: rajit
  version: "1.0"
allowed-tools: Read Edit Write
---

After every correction the user gives you, do the following:

## Steps

1. **Identify the mistake pattern** — What went wrong? What should have been done instead? Be specific.

2. **Write a rule** — Formulate it as a clear, actionable rule that prevents this class of mistake. Lead with the rule, then add context if needed.

3. **Update CLAUDE.md** — Append the rule to the relevant CLAUDE.md (project-level if in a project, global `~/.claude/CLAUDE.md` if it's a general behavior). Add it under a "Corrections" or "Rules" section.

4. **Confirm** — Tell the user: "Updated CLAUDE.md with: [rule summary]"

## Principles

- After EVERY correction, end the session with: "Update your CLAUDE.md so you don't make that mistake again."
- Ruthlessly edit CLAUDE.md over time — if a rule isn't reducing mistakes, rewrite it
- If the project has a `/memory` or `tasks/` notes directory, update it there too and point CLAUDE.md at it
- Claude is eerily good at writing rules for itself — trust the process

## Rule Format

```
## Rules / Corrections

- [Rule]: [What to do / not do]. [Why: brief context from the mistake]
```

## Example

User: "Stop wrapping every response with a summary of what you just did."

Claude updates CLAUDE.md:
```
- No trailing summaries: Do not summarize actions at the end of responses. The user can read the diff.
```
