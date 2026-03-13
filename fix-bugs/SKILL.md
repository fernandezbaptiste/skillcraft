---
name: fix-bugs
description: Autonomously fix bugs from any source — Slack threads, failing CI tests, docker logs, or a plain description. Use when you have a bug report or failing test and want Claude to investigate and fix without step-by-step guidance.
license: MIT
compatibility: Designed for Claude Code. Works best with access to CI logs, Slack MCP, or docker CLI.
metadata:
  author: rajit
  version: "1.0"
allowed-tools: Bash Read Grep Glob Edit Write
---

Fix the bug described or linked. Do not wait for step-by-step instructions — investigate and fix autonomously.

## Input Sources (handle any of these)

- **Slack thread URL or paste** — Read the thread, extract the bug report, reproduce and fix
- **"Go fix the failing CI tests"** — Run or read CI output, identify failures, fix them
- **Docker logs** — Parse logs for errors/stack traces, trace to root cause, fix
- **Plain description** — Understand the bug, find the relevant code, fix it

## Process

1. **Gather context** — Read the error message, stack trace, or thread in full. Do not skip this.
2. **Locate the code** — Find the exact file(s) and line(s) responsible. Use Grep/Glob aggressively.
3. **Understand before fixing** — Read the surrounding code. Do not patch symptoms.
4. **Fix** — Make the minimal correct change. Do not refactor unrelated code.
5. **Verify** — Run tests or check that the specific failure condition is resolved.
6. **Summarize** — One sentence: what was wrong and what you changed.

## Principles

- Do not micromanage the approach — just say "fix" and trust the process
- Point at docker logs for distributed system issues — Claude can trace across service boundaries
- If CI is failing: read the test output first, then the test code, then the implementation
- Do not add workarounds or feature flags — fix the root cause
- If you cannot reproduce or find the root cause, say so clearly rather than guessing

## Examples

```
User: fix this https://slack.com/archives/C07VBSH.../p1234
→ Claude reads Slack thread, finds the bug, fixes it

User: go fix the failing CI tests
→ Claude reads CI logs/test output, traces failures, patches code, reruns

User: look at these docker logs and fix whatever's broken
[paste logs]
→ Claude parses errors, finds the service + file, fixes it
```
