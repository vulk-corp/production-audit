# production-audit

Free audit prompts for AI-built apps. Paste them into your builder tool (Lovable, Bolt, v0, Replit). They audit your project and report what's wrong, ordered by severity. They don't change any code.

Built by [BWORLDS](https://www.bworlds.co) -- the production team for AI app builders.

## The prompts

| # | Prompt | What it audits | Import into Lovable |
|---|--------|----------------|---------------------|
| 1 | [Is your app leaking private stuff?](https://github.com/vulk-corp/audit-secrets) | API keys in client code, database security rules, data over-exposure | `vulk-corp/audit-secrets` |
| 2 | [Can strangers walk into your app?](https://github.com/vulk-corp/audit-access) | Authentication, unprotected routes, IDOR, input validation, roles | `vulk-corp/audit-access` |
| 3 | [Could your costs explode overnight?](https://github.com/vulk-corp/audit-costs) | AI spending caps, hosting limits, per-user rate limits, spam protection | `vulk-corp/audit-costs` |
| 4 | [Would you know if it breaks?](https://github.com/vulk-corp/audit-monitoring) | Error handling, monitoring, uptime alerts, backups, version control | `vulk-corp/audit-monitoring` |
| 5 | [Are you legally covered to sell your app?](https://github.com/vulk-corp/audit-legal) | Privacy policy, code ownership, copyleft dependencies | `vulk-corp/audit-legal` |
| 6 | [Is your codebase a mess?](https://github.com/vulk-corp/audit-code-quality) | File sizes, god components, duplicated logic, naming, structure | `vulk-corp/audit-code-quality` |

## Import into Lovable

1. Go to **Settings → Skills**
2. Click **Add → Import from GitHub**
3. Paste any repo URL from the table above (e.g. `https://github.com/vulk-corp/audit-secrets`)
4. Repeat for each audit you want

## Or copy-paste

Open the SKILL.md in any repo above and paste the content directly into your AI builder tool.

## How it works

1. Pick an audit
2. Import it or paste it into your AI builder tool
3. It audits your project and reports findings by severity
4. For each finding: what's wrong, what could happen, how to fix it, what could break
5. Nothing gets modified until you say so

## Want continuous monitoring?

These prompts are a one-time check. [BWORLDS](https://www.bworlds.co) runs these checks automatically, continuously, and fixes what it finds. It's your AI production team.

## License

MIT
