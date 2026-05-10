---
name: know-if-it-breaks
description: Audit for blind spots in monitoring and recovery -- error handling, error monitoring, uptime alerts, database backups, and version control.
---

Audit this project for blind spots in monitoring and recovery. Check the following in order of severity.

1. ERROR HANDLING
Visit a URL that doesn't exist in the app (e.g., /this-page-does-not-exist). Does it show a helpful error page or crash/blank/raw error?

2. ERROR MONITORING
Is there an error tracking service integrated (Sentry, LogRocket, Bugsnag)? Search for Sentry DSN, error reporting initialization, or similar setup.

3. UPTIME MONITORING
Is there anything that checks if the app is up and alerts when it goes down? Search for health check endpoints, uptime monitoring integrations, or cron-based pings.

4. DATABASE BACKUPS
Check if automated backups are configured for the database provider in use. If Supabase, check if it's on the free plan (no backups) or Pro (daily backups). If Firebase, check for scheduled exports.

5. VERSION CONTROL
Is the code connected to GitHub or similar? Check for .git directory, GitHub integration, deployment hooks.

For each finding, report:
- Number (1, 2, 3...)
- Severity: CRITICAL, HIGH, or OK
- File and line number (if applicable)
- What's wrong (one sentence)
- What could happen if you don't fix it (one sentence)
- How to fix it and what could break (one sentence each)

Sort by severity, then by how fast it could hurt you.

IMPORTANT: This is an audit only. Do NOT modify any code. Report what you find and suggest fixes, but do not apply any changes until I explicitly ask you to.
