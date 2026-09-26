# Environments and deployment

- Suggested targets: production backend on Railway, staging backend on Render, frontend on Vercel. Confirm these fit the project’s runtime, region, networking, and budget before setup.
- Keep production, staging, and local configuration separate. Never reuse production secrets or sensitive production data in staging.
- Validate configuration at startup and provide an `.env.example` with safe placeholders. Secrets belong in the platform’s secret manager/environment settings.
- Use explicit, repeatable build and start commands. Do not depend on a developer’s local state or undocumented manual steps.
- Run migrations as a deliberate release step using the project’s migration tooling. Do not enable schema auto-sync in deployed environments.
- Design health/readiness checks and graceful shutdown for the service. Avoid exposing detailed internals through health endpoints.
- For frontend builds, distinguish public build-time variables from secrets. Anything bundled into a client build must be treated as public.
- Before changing production deployment topology, data region, domains, or release/migration behavior, explain the impact and wait for confirmation if it is a material change.
- Document how staging and production are promoted, and ensure branch/PR targets align with `.claude/git-flow.instruction.md`.
