# Agent Rules Index

Entry point for all agent rules. Read the relevant files before starting a task.

## Core Rules

### Requirements

Before implementing any non-trivial feature, read `requirements/requirements.md`, `perspectives.md`, `architecture.md`, and `acceptance-criteria.md`.

Requirements must be complete across business, UX, frontend, backend, database, testing, and production concerns.

### Git

Follow `git/workflow.md`. Never bypass the repository branch and Pull Request workflow.

### Testing

When implementing or verifying a requirement:

1. Read `requirements/testing.md` to determine what must be tested.
2. Read `coding/testing.md` to determine how the tests must be executed.
3. For user-facing functionality, prioritize E2E testing through the Front End.
4. Do not consider a feature verified based only on unit tests or API responses.
5. Do not declare success until the relevant business rules, actors, states, and invariants have been verified.

### Context Management

After a feature is completed (PR created and results reported), end the final message by reminding the user to run `/clear` before starting the next task, to save tokens.

Do not carry context from a completed feature into the next one.

### Priority

When instructions conflict:

1. User's explicit request
2. Repository-specific requirements
3. Architecture rules
4. Coding conventions
5. General best practices

## File Index

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
