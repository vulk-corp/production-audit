---
name: codebase-a-mess
description: Audit your codebase for quality issues that break AI tools. Checks file sizes, god components, duplicated logic, naming consistency, and separation of concerns.
---

# Is your codebase a mess?

The more features you add, the harder it gets. Your AI tool starts hallucinating, changes break other things, and files grow until nothing works reliably. Code quality is what keeps your app buildable.

## What this prompt checks

- Files too large for AI tools to process reliably
- Components doing too many things at once
- Duplicated logic across multiple files
- Inconsistent naming and project structure
- Missing separation between UI, data, and business logic

## Prompt

Audit this project for code quality issues that will slow me down or break my AI tool's ability to help. Check the following, in order of severity. For each one, tell me if it's a problem, why it matters, and what to do about it.

1. FILE SIZE
List every file over 300 lines. For each one:
- What is it doing? Is it doing too many things?
- Could it be split into smaller, focused files?
- Files over 500 lines are a problem for AI tools -- they can't hold enough context to make safe changes

2. GOD COMPONENTS
Find components that handle UI rendering AND data fetching AND business logic in the same file:
- Does the component manage its own API calls, state, validation, and rendering?
- Could the data fetching be separated from the display?
- Components doing 3+ jobs are the #1 source of bugs when AI tools make changes

3. DUPLICATED LOGIC
Search for logic that appears in multiple places:
- Similar API calls in different components
- Repeated validation rules
- Copy-pasted utility functions
- Duplicated logic means every fix needs to happen in multiple places (and your AI tool will miss some)

4. NAMING AND STRUCTURE
Check the project organization:
- Are file and folder names consistent? (camelCase vs kebab-case vs PascalCase)
- Is there a clear structure (pages/components/hooks/utils/types)?
- Can you tell what a file does from its name and location?
- Are related files grouped together or scattered?

5. SEPARATION OF CONCERNS
Check if the codebase separates:
- UI components (what users see)
- Data access (API calls, database queries)
- Business logic (rules, validation, transformations)
- If everything is mixed together, changes in one area break others

For each finding, report:
- Number (1, 2, 3...)
- Severity: CRITICAL, HIGH, or OK
- File and line number
- What's wrong (one sentence)
- What could happen if you don't fix it (one sentence)
- How to fix it and what could break (one sentence each)

Sort by severity, then by how fast it could hurt you.

IMPORTANT: This is an audit only. Do NOT modify any code. Report what you find and suggest fixes, but do not apply any changes until I explicitly ask you to.
