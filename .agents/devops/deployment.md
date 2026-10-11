# Environments and Deployment

- Suggested targets: production backend on Railway, staging backend on Render, frontend on Vercel. Confirm these fit the runtime, region, networking, and budget before setup.
- Keep local, staging, and production configuration separate. Never reuse production secrets or sensitive data in staging.
- Validate configuration at startup. Provide `.env.example` with safe placeholders. Secrets live in the platform secret manager.
- Use explicit, repeatable build and start commands. Never depend on a developer's local state or undocumented manual steps.
- Run migrations as a deliberate release step with the project's migration tooling. No schema auto-sync in deployed environments.
- Provide health and readiness checks and graceful shutdown. Do not expose internals through health endpoints.
- Distinguish public build-time variables from secrets for client builds. Anything bundled into a client build is public.
- Before changing production topology, data region, domains, or release and migration behavior, explain the impact and wait for confirmation on material changes.
- Document how staging and production are promoted. Branch and PR targets follow `git/workflow.md`.
