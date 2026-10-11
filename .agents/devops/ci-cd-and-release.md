# CI/CD and Release

## Pipeline

- Every PR runs these as required automated checks: install from lockfile, format/lint, type check, unit and integration tests, build, and dependency and secret scans.
- Run E2E tests for critical journeys against a staging-like environment before release. Keep the pipeline fast by parallelizing and caching, never by skipping checks.
- Build once and promote the same artifact through environments. Do not rebuild per environment.
- Pipeline configuration lives in the repository and is reviewed like code. Pipeline secrets are scoped to the least privilege needed.

## Release

- Make releases small, frequent, and reversible. Prefer feature flags to separate deploy from release for risky changes.
- Know the rollback path before deploying. Database changes follow expand/contract so the previous application version keeps working.
- Order for breaking changes: backward-compatible schema, then code, then cleanup in a later release.
- Use semantic versioning and a changelog for versioned artifacts (libraries, APIs, mobile builds).
- After deploy, run smoke checks and watch error rate and latency before declaring success.

## Infrastructure

- Define infrastructure and environment configuration as code where the platform supports it. No untracked manual console changes.
- Pin runtime versions (Node, OS image, tooling) and keep them identical across local, CI, and deployed environments.
- Record budget, region, and data-residency choices as explicit architecture decisions.
