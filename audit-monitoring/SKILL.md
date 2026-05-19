---
name: audit-monitoring
description: Audit for blind spots in monitoring and recovery. Checks error handling, error monitoring, uptime alerts, database backups, and version control. Asks questions when settings can't be verified from code.
---

Audit this project for blind spots in monitoring and recovery. Check the following in order of severity. Some of these can be verified from code, others can't. When you can't verify something from the codebase, tell me exactly where to check and ask me to confirm.

1. ERROR HANDLING
Check if the app has a custom 404 page or error boundary component.
- What happens when a user visits a URL that doesn't exist?
- Does it show a helpful error page or crash/blank/raw error?

2. ERROR MONITORING
Search the codebase for error tracking integration (Sentry, LogRocket, Bugsnag):
- Look for Sentry DSN, error reporting initialization, or similar setup
- If nothing is found, flag it

3. UPTIME MONITORING
This can't be fully verified from code. Check for health check endpoints or monitoring SDK integration. Then ask me:
- Do you use an uptime monitoring service (UptimeRobot, Pingdom, Better Uptime)?
- Does anyone get alerted when your app goes down?
If I don't have uptime monitoring, tell me the simplest free options to set up.

4. DATABASE BACKUPS
Identify the database from the codebase (Supabase, Firebase, PlanetScale, etc.). Backup settings live in the provider dashboard, not in code. Tell me exactly where to check:
- Supabase: dashboard.supabase.com > Project Settings > Database > Backups (free plan has no backups, Pro has daily)
- Firebase: console.firebase.google.com > Project Settings > Backups
- Other providers: tell me where to look
Ask me to confirm whether backups are enabled.

5. VERSION CONTROL
Check for a .git directory or GitHub integration in the project. If the code only exists inside the builder tool, ask me:
- Is this project connected to GitHub?
- If not, walk me through how to connect it

For each finding, report:
- Number (1, 2, 3...)
- Severity: CRITICAL, HIGH, or OK
- File and line number (if applicable)
- What's wrong (one sentence)
- What could happen if you don't fix it (one sentence)
- How to fix it and what could break (one sentence each)

Sort by severity, then by how fast it could hurt you.

IMPORTANT: This is an audit only. Do NOT modify any code. Report what you find and suggest fixes, but do not apply any changes until I explicitly ask you to.
