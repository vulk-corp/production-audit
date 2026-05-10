---
name: audit-legal
description: Audit for legal risks before charging users -- privacy policy, AI tool code ownership terms, and copyleft license dependencies.
---

Audit this project for legal risks before charging users. Check the following in order of severity.

1. PRIVACY POLICY
Does this app have a privacy policy? Check for a /privacy or /privacy-policy route. Check the footer and signup/login pages for a link. If the app collects any user data and has no privacy policy, flag it.

2. CODE OWNERSHIP
What AI tools were used to build this app? Check for signs of Lovable, Bolt, v0, Replit, Cursor. Do their terms of service grant full ownership of generated code? Flag any tool whose terms retain rights, use code for training, or restrict commercial use.

3. COPYLEFT DEPENDENCIES
Scan package.json and lock files for dependencies with copyleft licenses (GPL, AGPL, LGPL, MPL). These can require you to release your source code under the same license. Check both direct and significant transitive dependencies.

For each finding, report:
- Number (1, 2, 3...)
- Severity: CRITICAL, HIGH, or OK
- File and line number (if applicable)
- What's wrong (one sentence)
- What could happen if you don't fix it (one sentence)
- How to fix it and what could break (one sentence each)

Sort by severity, then by how fast it could hurt you.

IMPORTANT: This is an audit only. Do NOT modify any code. Report what you find and suggest fixes, but do not apply any changes until I explicitly ask you to.
