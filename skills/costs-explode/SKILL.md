---
name: costs-explode
description: Audit your app for cost explosion risks. Checks AI provider spending limits, hosting caps, per-user rate limits, and spam protection on API routes.
---

# Could your costs explode overnight?

One viral moment, one bot, or one buggy loop can turn a $5/month app into a $500 invoice. Most AI-built apps have no spending caps, no per-user limits, and no spam protection.

## What this prompt checks

- AI provider spending limits (OpenAI, Anthropic, etc.)
- Hosting platform spending caps (Vercel, Netlify, Railway)
- Per-user rate limits on expensive operations
- Spam and abuse protection on API routes

## Prompt

Audit this project for cost explosion risks. Check the following, in order of severity. For each one, tell me if it's a problem, why it matters, and what to do about it.

1. AI PROVIDER COSTS
Does this app call any AI APIs (OpenAI, Anthropic, Google AI, Replicate, etc.)? If yes:
- Are there spending limits or budget alerts set up with the provider?
- Is there anything in the code that limits how many AI calls a single user can make?
- Could a single user trigger unlimited AI calls (e.g., by spamming a button or sending requests in a loop)?
- What's the estimated cost per request? What happens if someone makes 10,000 requests?

2. HOSTING COSTS
What hosting platform is this deployed on? Check for:
- Serverless functions that could be triggered at scale (each invocation costs money)
- Bandwidth-heavy operations (large file uploads, video streaming) with no limits
- Database operations that scale with usage (reads/writes on pay-per-use plans)

3. PER-USER LIMITS
Check if the app has any per-user rate limiting:
- Can one user make unlimited requests to expensive endpoints?
- Is there a daily or monthly cap per user?
- Is there any usage tracking in the database?
If there's no per-user limiting at all, flag it.

4. SPAM PROTECTION
Check API routes for rate limiting middleware:
- Can someone send 1,000 requests per second to any endpoint?
- Are there any rate limiters (express-rate-limit, upstash ratelimit, etc.)?
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
