---
name: audit-costs
description: Audit for cost explosion risks -- AI provider spending limits, hosting caps, per-user rate limits, and spam protection.
---

Audit this project for cost explosion risks. Check the following in order of severity.

1. AI PROVIDER COSTS
Does this app call any AI APIs (OpenAI, Anthropic, Google AI, Replicate)? If yes:
- Are there spending limits or budget alerts set up with the provider?
- Can a single user trigger unlimited AI calls?
- What's the estimated cost per request and what happens at 10,000 requests?

2. HOSTING COSTS
What hosting platform is this deployed on? Check for:
- Serverless functions that could be triggered at scale
- Bandwidth-heavy operations with no limits
- Database operations that scale with usage on pay-per-use plans

3. PER-USER LIMITS
Check if the app has per-user rate limiting:
- Can one user make unlimited requests to expensive endpoints?
- Is there a daily or monthly cap per user?
- Is there any usage tracking in the database?
If there's no per-user limiting at all, flag it.

4. SPAM PROTECTION
Check API routes for rate limiting middleware:
- Can someone send 1,000 requests per second to any endpoint?
- Are there rate limiters (express-rate-limit, upstash ratelimit, etc.)?
- Are login/signup endpoints protected against brute force?

For each finding, report:
- Number (1, 2, 3...)
- Severity: CRITICAL, HIGH, or OK
- File and line number
- What's wrong (one sentence)
- What could happen if you don't fix it (one sentence)
- How to fix it and what could break (one sentence each)

Sort by severity, then by how fast it could hurt you.

IMPORTANT: This is an audit only. Do NOT modify any code. Report what you find and suggest fixes, but do not apply any changes until I explicitly ask you to.
