## Code Review Uncommitted Changes

Review all uncommitted changes (staged and unstaged) for issues and summarize what changed.

### Steps
1. Run `git diff` (unstaged) and `git diff --cached` (staged) to collect all uncommitted changes
2. Run `git status` to see the full picture of modified, added, and deleted files
3. Summarize what changed: group changes by area (backend model, backend route, frontend type, frontend component, migration, config, etc.) with a one-line description per file
4. Review the diff for these common issues:

   **Date format inconsistencies (critical for this project)**
   - Mixing ISO timestamps (`2024-01-01T00:00:00Z`) with date-only strings (`2024-01-01`) — always use YYYY-MM-DD strings
   - Using `new Date()` for keys or comparisons where a string format should be used
   - Missing `TO_CHAR(date_column, 'YYYY-MM-DD')` in SQL queries that return dates
   - Timezone-unsafe date conversions

   **Type safety**
   - `any` types that should be specific
   - Missing null checks on `.find()`, `.rows[0]`, or optional chaining
   - Frontend types not matching backend response shape
   - Mismatched field names between API response and TypeScript interface

   **SQL & backend**
   - Missing `user_id` filter in queries (data isolation)
   - Missing parameterized queries (SQL injection risk)
   - Missing input validation (Zod schemas) on new endpoints
   - Missing `ON DELETE CASCADE` or appropriate FK behavior on new tables

   **Frontend**
   - Missing error handling on API calls
   - Missing query invalidation after mutations
   - Stale query keys that won't refetch when they should

   **General**
   - `console.log` left in production code
   - Hardcoded values that should be constants
   - Dead code or unused imports

5. Report findings as:
   - **Issues** — things that should be fixed before committing
   - **Warnings** — things worth considering but not blockers
   - If no issues found, say so explicitly
6. End with a one-line verdict: "Ready to commit", "X issues to fix first", or "Clean diff — no changes found"
