# Validate Code

Run the project's code quality checks:

Lint results:
!npm run lint 2>&1 || true

Unused code check (knip):
!npm run knip 2>&1 || true

Build check:
!npm run build 2>&1 || true

Review the output above and report what passed and what needs fixing.
