---
name: leaking-private-stuff
description: Audit your app for exposed API keys, open databases, and data over-exposure. Checks client-side secrets, database security rules (Supabase RLS, Firebase), and API responses returning more data than the UI needs.
---

# Is your app leaking private stuff?

Most AI-built apps ship with API keys in the client code and databases wide open. Anyone with a browser can find them. You would never know until someone runs up your bill or downloads your users' data.

## What this prompt checks

- API keys, passwords, or secrets hardcoded in client-side code
- Database security rules (Supabase RLS, Firebase rules) that block unauthenticated access
- Data over-exposure -- API responses returning more fields than the UI actually needs

## Prompt

Audit this project for data leaks. Check the following, in order of severity. For each one, tell me if it's a problem, why it matters, and what to do about it.

1. SECRETS IN CLIENT CODE
Search every file served to the browser for hardcoded API keys, passwords, database URLs, or tokens. Check for any string that looks like a secret: OpenAI keys (sk-...), Supabase keys, Stripe keys, Firebase credentials, .env values pasted directly into code. Check environment variable usage -- are secrets properly loaded from env vars or hardcoded?

2. DATABASE SECURITY
Check my database configuration. If I'm using Supabase, check if Row Level Security (RLS) is enabled on every table. If RLS is off, anyone with the Supabase URL and anon key can read and write all data. If I'm using Firebase, check Firestore/RTDB security rules for open access. Flag any table or collection where unauthenticated users can read or write.

3. DATA OVER-EXPOSURE
Check every API call and database query that returns data to the browser. For each one:
- Does it use select('*') or return entire rows when the UI only needs a few fields?
- Are sensitive fields (emails, phone numbers, internal IDs, metadata) being sent to the client even though the UI never displays them?
- Could someone open the browser network tab, inspect the API responses, and see data they shouldn't?
List each endpoint or query that returns more data than the UI consumes.

For each finding, report:
- Number (1, 2, 3...)
- Severity: CRITICAL, HIGH, or OK
- File and line number
- What's wrong (one sentence)
- What could happen if you don't fix it (one sentence)
- How to fix it and what could break (one sentence each)

Sort by severity, then by how fast it could hurt you.

IMPORTANT: This is an audit only. Do NOT modify any code. Report what you find and suggest fixes, but do not apply any changes until I explicitly ask you to.
