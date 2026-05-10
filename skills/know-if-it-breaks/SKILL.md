---
name: know-if-it-breaks
description: Audit your app for blind spots in monitoring and recovery. Checks error handling, error monitoring (Sentry), uptime alerts, database backups, and version control.
---

# Would you know if it breaks?

Your app could be crashing right now and you would have no idea. No error tracking, no uptime alerts, no backups. Your users find the bugs before you do.

## What this prompt checks

- Error page handling (what users see when something breaks)
- Error monitoring integration (Sentry or similar)
- Uptime monitoring (does someone get alerted when the app goes down?)
- Database backups (would you lose everything if the database breaks?)
- Version control (can you undo a bad change?)

## Prompt

Audit this project for blind spots in monitoring and recovery. Check the following, in order of severity. For each one, tell me if it's a problem, why it matters, and what to do about it.

1. ERROR HANDLING
Visit a URL that doesn't exist in the app (e.g., /this-page-does-not-exist). What happens?
- Does the app show a helpful error page with a way back to the homepage?
- Does it crash, show a blank screen, or display raw error details?
- Check if there's a custom 404 page or error boundary component.

2. ERROR MONITORING
Is there an error tracking service integrated (Sentry, LogRocket, Bugsnag, etc.)?
- Search for Sentry DSN, error reporting initialization, or similar setup
- If there's no error tracking, every bug happens silently -- users hit errors and leave, and you never know why

3. UPTIME MONITORING
Is there anything that checks if the app is up and alerts you if it goes down?
- Search for health check endpoints, uptime monitoring integrations, or cron-based pings
- If not, the app could be down for hours before anyone notices

4. DATABASE BACKUPS
What database does this app use? Check the configuration:
- If Supabase: is it on the free plan (no backups) or Pro plan (daily backups)?
- If Firebase: are there scheduled exports configured?
- If another DB: is there any backup strategy?
- If there's no backup at all, one bad migration or accidental deletion means permanent data loss

5. VERSION CONTROL
Is the code connected to GitHub or similar?
- Check for .git directory, GitHub integration, deployment hooks
- If the code only exists in the builder tool, one bad prompt could destroy the entire project with no way to recover

For each finding, report:
- Number (1, 2, 3...)
- Severity: CRITICAL, HIGH, or OK
- File and line number (if applicable)
- What's wrong (one sentence)
- What could happen if you don't fix it (one sentence)
- How to fix it and what could break (one sentence each)

Sort by severity, then by how fast it could hurt you.

IMPORTANT: This is an audit only. Do NOT modify any code. Report what you find and suggest fixes, but do not apply any changes until I explicitly ask you to.
