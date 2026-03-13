# skillcraft ⚡

A curated collection of 45 Agent Skills for Claude Code and any [agentskills.io](https://agentskills.io)-compatible agent.

## What's inside

Skills are organized into two categories:

### 🛠 Claude Code Workflow (13 skills)

| Skill | Description |
|---|---|
| `/orchestrate` | Plan-first workflow orchestration for complex tasks |
| `/update-claude-md` | Update CLAUDE.md after every correction to prevent recurring mistakes |
| `/techdebt` | Find and eliminate duplicated/dead code at end of session |
| `/fix-bugs` | Autonomously fix bugs from Slack threads, CI logs, or docker logs |
| `/grill-me` | Adversarial code review before PRs; elegant rewrites; spec-driven dev |
| `/subagents` | Throw more compute at hard problems via parallel subagents |
| `/data-query` | Natural language analytics against any DB (BigQuery, Postgres, etc.) |
| `/terminal-setup` | Optimal terminal setup — Ghostty, statusline, tmux, voice dictation |
| `/systems-architect` | Full technical blueprint for web infra / SaaS products |
| `/visual-system-architect` | Production design system — colors, type, grid, 30+ components |
| `/conversion-copy` | High-converting website copy across all page sections |
| `/interaction-engineer` | React component architecture for complex interactive modules |
| `/figma-translator` | Convert technical specs into 5 Figma Make–ready prompts |

### 📈 Marketing (32 skills)

A full marketing skills suite by [Corey Haines](https://corey.co) — CRO, copywriting, SEO, paid ads, email, pricing, and more.

`ab-test-setup` · `ad-creative` · `ai-seo` · `analytics-tracking` · `churn-prevention` · `cold-email` · `competitor-alternatives` · `content-strategy` · `copy-editing` · `copywriting` · `email-sequence` · `form-cro` · `free-tool-strategy` · `launch-strategy` · `marketing-ideas` · `marketing-psychology` · `onboarding-cro` · `page-cro` · `paid-ads` · `paywall-upgrade-cro` · `popup-cro` · `pricing-strategy` · `product-marketing-context` · `programmatic-seo` · `referral-program` · `revops` · `sales-enablement` · `schema-markup` · `seo-audit` · `signup-flow-cro` · `site-architecture` · `social-content`

> Marketing skills sourced from [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) (MIT)

## Installation

### Claude Code

```bash
# Clone into your Claude skills directory
git clone https://github.com/rajit/skillcraft ~/.claude/skills/skillcraft-repo

# Copy all skills
cp -r ~/.claude/skills/skillcraft-repo/* ~/.claude/skills/
```

Then invoke any skill with `/skill-name` in Claude Code.

### Other agents

Skills follow the [agentskills.io](https://agentskills.io) open standard and work with any compatible agent (Cursor, Gemini CLI, GitHub Copilot, OpenCode, and more). Install to `.agents/skills/` per your agent's documentation.

## Format

Every skill is a directory containing a `SKILL.md` with YAML frontmatter:

```
skill-name/
├── SKILL.md          # Required: metadata + instructions
├── scripts/          # Optional: executable scripts
├── references/       # Optional: reference docs
└── assets/           # Optional: templates, data files
```

## License

MIT — see [LICENSE](LICENSE) for details.
Marketing skills © Corey Haines, MIT licensed.
