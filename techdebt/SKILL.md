---
name: techdebt
description: Find and eliminate technical debt — duplicated code, dead code, redundant abstractions. Use at the end of a coding session or when the codebase feels bloated. Scans, reports, and fixes issues with user confirmation.
license: MIT
compatibility: Designed for Claude Code. Requires a git repository.
metadata:
  author: rajit
  version: "1.0"
allowed-tools: Bash Read Grep Glob Edit
---

Scan the current codebase for technical debt and eliminate it. This is meant to be run at the end of a work session or periodically to keep quality high.

## What to Look For

1. **Duplicated code** — Copy-pasted logic that should be a shared utility or function
2. **Dead code** — Unused functions, variables, imports, exports, commented-out blocks
3. **Redundant abstractions** — Over-engineered helpers used in only one place
4. **Inconsistent patterns** — The same operation done 3+ different ways across files
5. **Stale TODOs / FIXMEs** — Old comments that are no longer relevant

## Process

1. Use Grep and Glob to identify candidates across the codebase
2. Confirm each item is truly dead/duplicated (check all usages)
3. For each issue found, present:
   - File + line number
   - What the problem is
   - Proposed fix
4. Ask the user to confirm before making changes, or batch fixes if they say "just fix it"
5. After fixes, run tests to verify nothing broke

## Output Format

```
## Tech Debt Found

### Duplicated Code
- `src/utils/formatDate.ts:12` and `src/helpers/dates.ts:45` — identical date formatting logic
  Fix: consolidate into `src/utils/formatDate.ts`, remove `src/helpers/dates.ts`

### Dead Code
- `src/api/legacyAuth.ts` — no imports found anywhere
  Fix: delete file

### Stale TODOs
- `src/components/Modal.tsx:89` — TODO from 6 months ago, feature was shipped
  Fix: remove comment
```

## Tips

- If you do something more than once a day, turn it into a skill or command
- Run `/techdebt` at the end of every coding session
- Focus on the highest-leverage items first (most duplication, most confusion)
