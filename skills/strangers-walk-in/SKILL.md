---
name: strangers-walk-in
description: Audit your app for unauthorized access. Checks authentication, unprotected routes, IDOR (data access by ID), input validation, and role-based permissions.
---

# Can strangers walk into your app?

If your app has no login, anyone with the URL sees everything. If it has a login but no server-side checks, anyone who guesses a URL can still see other people's data.

## What this prompt checks

- Whether the app requires authentication to access
- API routes and pages that return user data without checking login status
- Whether a logged-in user can see another user's data by changing the ID in the URL
- Forms that accept input without validation or sanitization
- User roles and permissions -- whether admin and regular users have the same access

## Prompt

Audit this project for unauthorized access. Check the following, in order of severity.

1. OPEN ACCESS
Does this app require login to use? Check if there's an authentication system (login/signup page, auth provider like Supabase Auth, Firebase Auth, Clerk, etc.). If the app is wide open, flag it as critical -- anyone with the URL can use every feature and see all data.

2. UNPROTECTED ROUTES
Find every API route and page that accesses user data. Check if each one verifies that the user is authenticated before returning data. Look for routes that fetch from the database without checking the session/token. Flag any route where an unauthenticated request would succeed.

3. DATA ACCESS BY ID
Check every route or query that loads data using an ID from the URL or request (e.g., /users/:id, /orders/:id). Does it verify the logged-in user owns that data, or can any logged-in user see anyone else's records by changing the ID? Flag any query that uses a user-supplied ID without checking ownership.

4. INPUT VALIDATION
Check all forms and API endpoints that accept user input. Are inputs validated before processing? Could someone submit a script tag, SQL query, or excessively long string? Check for XSS, SQL injection, and basic input sanitization.

5. ROLE-BASED ACCESS
If the app has different user types (admin, regular user, etc.), check if permissions are enforced. Can a regular user access admin routes by changing the URL? Are role checks done server-side or only in the UI?

For each finding, report:
- Number (1, 2, 3...)
- Severity: CRITICAL, HIGH, or OK
- File and line number
- What's wrong (one sentence)
- What could happen if you don't fix it (one sentence)
- How to fix it and what could break (one sentence each)

Sort by severity, then by how fast it could hurt you.

IMPORTANT: This is an audit only. Do NOT modify any code. Report what you find and suggest fixes, but do not apply any changes until I explicitly ask you to.
