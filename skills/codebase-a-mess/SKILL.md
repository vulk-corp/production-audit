---
name: codebase-a-mess
description: Audit codebase for quality issues that break AI tools -- file sizes, god components, duplicated logic, naming consistency, separation of concerns.
---

Audit this project for code quality issues that will break AI tool assistance. Check the following in order of severity.

1. FILE SIZE
List every file over 300 lines. What is it doing? Could it be split? Files over 500 lines exceed most AI tool context windows.

2. GOD COMPONENTS
Find components that handle UI rendering AND data fetching AND business logic in the same file. Could the data fetching be separated from the display?

3. DUPLICATED LOGIC
Search for logic that appears in multiple places: similar API calls, repeated validation rules, copy-pasted utility functions.

4. NAMING AND STRUCTURE
Check project organization: are names consistent (casing, structure)? Can you tell what a file does from its name and location? Are related files grouped together?

5. SEPARATION OF CONCERNS
Check if the codebase separates UI components, data access (API calls, database queries), and business logic (rules, validation, transformations).

For each finding, report:
- Number (1, 2, 3...)
- Severity: CRITICAL, HIGH, or OK
- File and line number
- What's wrong (one sentence)
- What could happen if you don't fix it (one sentence)
- How to fix it and what could break (one sentence each)

Sort by severity, then by how fast it could hurt you.

IMPORTANT: This is an audit only. Do NOT modify any code. Report what you find and suggest fixes, but do not apply any changes until I explicitly ask you to.
