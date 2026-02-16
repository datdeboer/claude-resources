## Suggest Git Commit Message

Analyze all changed files and suggest a commit message. Do NOT create the commit — only suggest the message.

### Steps
1. Run `git status` to see all modified, added, and deleted files (never use -uall flag)
2. Run `git diff` (unstaged) and `git diff --cached` (staged) to see the actual changes
3. Run `git log --oneline -10` to understand the repository's existing commit message style
4. Analyze the changes:
   - Identify what changed from a user/product perspective — what can the user now do that they couldn't before, or what works differently?
   - Group related changes into a single functional description (e.g. backend model + route + frontend UI = "users can now add daily notes to habits")
   - Ignore implementation details like file names, table names, model names, endpoints, types, etc.
5. Draft a commit message following the repo's style:
   - First line: concise summary (under 72 chars) describing the functional change, not the technical one
   - If helpful, add a blank line followed by a brief explanation of why the change was made or how it affects the user experience
   - Do NOT list technical artifacts (tables, models, routes, types, components) — describe behavior and capabilities instead
6. Present the suggested message in a code block the user can copy
7. If there are no changes to commit, say so
