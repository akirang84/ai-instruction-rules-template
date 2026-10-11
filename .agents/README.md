# Agent Rules Index

Entry point for all agent rules. Read the relevant files before starting a task.

## Git

- [`git/workflow.md`](git/workflow.md) — branch + Pull Request workflow. Never bypass.

## Requirements

Read before implementing any non-trivial feature.

- [`requirements/requirements.md`](requirements/requirements.md) — requirements engineering rules.
- [`requirements/perspectives.md`](requirements/perspectives.md) — perspectives to evaluate a feature from.
- [`requirements/architecture.md`](requirements/architecture.md) — core engine and extensibility.
- [`requirements/acceptance-criteria.md`](requirements/acceptance-criteria.md) — completeness checklist.
- [`requirements/testing.md`](requirements/testing.md) — **what** must be tested.

## Coding

- [`coding/architecture.md`](coding/architecture.md) — architecture and design rules.
- [`coding/code-quality.md`](coding/code-quality.md) — code quality rules.
- [`coding/testing.md`](coding/testing.md) — **how** tests are executed and reported.

### Common design rules

Mandatory for every platform and app. Platform-specific specs (web, mobile) must follow them strictly. See [`coding/design/README.md`](coding/design/README.md).

- [`coding/design/reusability.md`](coding/design/reusability.md)
- [`coding/design/consistency.md`](coding/design/consistency.md)
- [`coding/design/scalability.md`](coding/design/scalability.md)
- [`coding/design/ecosystem-connectivity.md`](coding/design/ecosystem-connectivity.md) — comprehensiveness and connectivity.
- [`coding/design/maintainability-extensibility.md`](coding/design/maintainability-extensibility.md)

## Stack and Platform Rules

Common rules (`coding/`, `coding/design/`, `security/`, `requirements/`) apply everywhere. Stack and platform rules extend them and never weaken them.

### Backend, Data, Security, DevOps

- [`backend/nestjs.md`](backend/nestjs.md) — NestJS and TypeScript backend.
- [`database/database.md`](database/database.md) — database, ORM, migrations, time.
- [`security/security.md`](security/security.md) — authentication and security.
- [`devops/deployment.md`](devops/deployment.md) — environments and deployment.
- [`devops/ci-cd-and-release.md`](devops/ci-cd-and-release.md) — pipeline, release, infrastructure.
- [`devops/observability-and-operations.md`](devops/observability-and-operations.md) — logs, metrics, alerts, runbooks.

### Frontend

- [`frontend/shared.md`](frontend/shared.md) — shared baseline for web and mobile (Expo, React Native, Tamagui).
- [`web/README.md`](web/README.md) — web specification (rendering, performance and SEO, accessibility, security, delivery).
- [`mobile/README.md`](mobile/README.md) — mobile specification (platform, performance and offline, UX, security, release).
