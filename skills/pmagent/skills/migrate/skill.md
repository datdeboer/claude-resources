## Run Database Migration

Run the database migration and report results.

### Steps
1. Run `cd backend && npm run migrate` and capture the full output
2. Parse the output and report:
   - Which migrations were **newly applied** (lines with "completed successfully")
   - Which migrations were **already executed** (lines with "already executed")
   - Any **errors** that occurred
3. If the migration failed, analyze the error and suggest a fix based on common issues:
   - `ECONNREFUSED` → PostgreSQL not running
   - `3D000` → Database doesn't exist
   - `28P01` → Bad credentials
   - `role does not exist` → Wrong username in DATABASE_URL
   - Syntax errors → Problem in the migration SQL
4. Summarize with a short status line, e.g. "2 new migrations applied, 15 already executed" or "Migration failed: [reason]"
