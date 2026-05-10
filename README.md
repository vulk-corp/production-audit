# production-audit

Free audit prompts for AI-built apps. Paste them into your builder tool (Lovable, Bolt, v0, Replit). They audit your project and report what's wrong, ordered by severity. They don't change any code.

Built by [BWORLDS](https://www.bworlds.co) -- the production team for AI app builders.

## The prompts

| # | Prompt | What it audits |
|---|--------|----------------|
| 1 | [Is your app leaking private stuff?](skills/audit-secrets/SKILL.md) | API keys in client code, database security rules, data over-exposure |
| 2 | [Can strangers walk into your app?](skills/audit-access/SKILL.md) | Authentication, unprotected routes, IDOR, input validation, roles |
| 3 | [Could your costs explode overnight?](skills/audit-costs/SKILL.md) | AI spending caps, hosting limits, per-user rate limits, spam protection |
| 4 | [Would you know if it breaks?](skills/audit-monitoring/SKILL.md) | Error handling, monitoring, uptime alerts, backups, version control |
| 5 | [Are you legally covered to sell your app?](skills/audit-legal/SKILL.md) | Privacy policy, code ownership, copyleft dependencies |
| 6 | [Is your codebase a mess?](skills/audit-code-quality/SKILL.md) | File size, god components, duplicated logic, naming, structure |

## Install

```bash
npx skills add vulk-corp/production-audit
```

Or copy the prompts directly from the SKILL.md files.

## How it works

1. Pick a prompt
2. Paste it into your AI builder tool
3. It audits your project and reports findings by severity
4. For each finding: what's wrong, what could happen, how to fix it, what could break
5. Nothing gets modified until you say so

## Want continuous monitoring?

These prompts are a one-time check. [BWORLDS](https://www.bworlds.co) runs these checks automatically, continuously, and fixes what it finds. It's your AI production team.

## License

MIT
