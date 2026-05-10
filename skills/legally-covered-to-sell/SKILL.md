---
name: legally-covered-to-sell
description: Audit your app for legal risks before charging users. Checks for a published privacy policy, AI tool code ownership terms, and copyleft license dependencies (GPL, AGPL).
---

# Are you legally covered to sell your app?

You want to charge money for this. But do you have a privacy policy? Do you actually own the code your AI tool generated? Are any of your dependencies forcing you to open-source your entire app?

## What this prompt checks

- Privacy policy published and accessible from the app
- Code ownership terms in your AI tool's terms of service
- Dependencies with copyleft licenses (GPL, AGPL) that could force you to open-source your code

## Prompt

Audit this project for legal risks before I start charging users. Check the following, in order of severity. For each one, tell me if it's a problem, why it matters, and what to do about it.

1. PRIVACY POLICY
Does this app have a privacy policy?
- Check for a /privacy, /privacy-policy, or similar route
- Check the footer and signup/login pages for a privacy policy link
- If the app collects any user data (emails, names, usage data, analytics) and has no privacy policy, it's a legal liability in the EU (GDPR) and California (CCPA)

2. CODE OWNERSHIP
What AI tools were used to build this app?
- Check for signs of Lovable, Bolt, v0, Replit, Cursor, or other AI builder tools
- Review the terms of service of each tool used -- do they grant full ownership of generated code?
- Flag any tool whose terms retain rights to the code, use it for training, or restrict commercial use
- If you can't determine ownership clearly, flag it as a risk

3. COPYLEFT DEPENDENCIES
Scan package.json (and any lock files) for dependencies with copyleft licenses:
- GPL, AGPL, LGPL, MPL, or similar licenses
- These licenses can require you to release your entire source code under the same license
- For a commercial product you plan to sell, this means you'd have to give away your code
- Check both direct dependencies and significant transitive dependencies

For each finding, report:
- Number (1, 2, 3...)
- Severity: CRITICAL, HIGH, or OK
- File and line number (if applicable)
- What's wrong (one sentence)
- What could happen if you don't fix it (one sentence)
- How to fix it and what could break (one sentence each)

Sort by severity, then by how fast it could hurt you.

IMPORTANT: This is an audit only. Do NOT modify any code. Report what you find and suggest fixes, but do not apply any changes until I explicitly ask you to.
