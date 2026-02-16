## Build, Lint, and Test Check

Run all verification steps and report a clean pass/fail summary.

### Steps
1. Run these three commands and capture their output:
   - `npm run build` (TypeScript compilation + Vite build)
   - `npm run lint` (ESLint for frontend and backend)
   - `npm test` (Vitest for frontend and backend)
2. For each step, report one of:
   - **Pass** — no errors
   - **Fail** — with only the relevant error lines (not the full output)
3. If there are TypeScript errors, list each error with file path and line number
4. If there are lint errors, list each error with file path, line, and rule name
5. If tests fail, list which test files/cases failed and the assertion error
6. End with a single summary line, e.g.:
   - "All checks passed"
   - "Build failed (2 type errors), lint passed, tests passed"
   - "Build passed, lint passed, 1 test failed"
