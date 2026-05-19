---
name: audit-costs
description: Audit for cost explosion risks. Checks AI provider spending limits, hosting caps, per-user rate limits, and spam protection. Redirects to provider dashboards when settings can't be verified from code.
---

Audit this project for cost explosion risks. Check the following in order of severity. Some of these settings live in provider dashboards, not in code. When you can't verify something from the codebase, tell me exactly where to check (which dashboard, which settings page, which URL) and what questions I need to answer.

1. AI PROVIDER COSTS
Identify which AI APIs this app calls (OpenAI, Anthropic, Google AI, Replicate, etc.). For each one:
- Check the code for any request-level cost controls (token limits, max retries, timeout)
- Can a single user trigger unlimited AI calls (e.g., by spamming a button or looping requests)?
- Spending limits and budget alerts are set in the provider dashboard, not in code. Tell me exactly where to check: for OpenAI it's platform.openai.com/settings/organization/limits, for Anthropic it's console.anthropic.com/settings/limits. Ask me to confirm whether I have limits set.

2. HOSTING COSTS
Identify the hosting platform from the codebase (Vercel, Netlify, Railway, etc.). Check for:
- Serverless functions that could be triggered at scale
- Bandwidth-heavy operations (file uploads, streaming) with no limits
- Database operations on pay-per-use plans
- Spending caps are configured in the hosting dashboard, not in code. Tell me exactly where to find them for my platform and ask me to confirm.

3. PER-USER LIMITS
Check if the app has per-user rate limiting in the code:
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
