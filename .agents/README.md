# Agent Rules Index

Entry point for all agent rules. Template version: 1.0.0.

## How This Template Works

Rules come in three layers. Copy the whole structure (`AGENTS.md`, `CLAUDE.md`, `.agents/`) into a new project unchanged.

| Layer | Files | Changes per project? |
|---|---|---|
| **Locked** | `git/workflow.md` | Never. Not even through overrides. |
| **Core** | `requirements/`, `coding/`, `security/`, `database/`, `devops/`, `frontend/` | No. Stack-agnostic rules for every project. Improve them in the template repository. |
| **Stacks** | `stacks/backend/`, `stacks/database/`, `stacks/frontend/` | No edits; a project activates the ones it uses in `project.md`. Each extends core and never weakens it. |
| **Project** | `project.md` | Yes. Product, chosen stacks, commands, environments, decisions, and overrides. |

Setup: when `project.md` says `Status: NOT CONFIGURED`, run [`bootstrap.md`](bootstrap.md). It asks the user what must be confirmed and fills `project.md`.

To add a stack (for example `stacks/frontend/react-web.md`), create it in the template repository with a header naming the core files it extends, and add it to `project.md` section 2 and to the table below.

## What to Read per Task

Always read `project.md` and the active stack files it lists. Then:

| Task | Read |
|---|---|
| Any code change | `git/workflow.md`, `coding/code-quality.md` |
| New feature or business-rule change | `requirements/` (all), `coding/architecture.md`, `coding/design/`, `requirements/testing.md`, `coding/testing.md` |
| Bug fix | `coding/testing.md` (regression test), `requirements/testing.md` sections relevant to the bug |
| API or contract change | `coding/architecture.md` (Contracts), `coding/design/ecosystem-connectivity.md` |
| Schema or data change | `database/database.md`, `devops/ci-cd-and-release.md` (Release) |
| Auth, permissions, personal data | `security/security.md`, platform security files |
| Web UI | `frontend/shared.md`, `frontend/web/` |
| Mobile UI | `frontend/shared.md`, `frontend/mobile/` |
| CI, deploy, infrastructure | `devops/` |

A change is **trivial** when it has no behavior impact (copy, styling, config with no behavior change); everything else is non-trivial. See `requirements/testing.md` (Depth).

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

### Context Management (Claude Code)

After a feature is completed (PR created and results reported), end the final message by reminding the user to run `/clear` before starting the next task, to save tokens.

Do not carry context from a completed feature into the next one.

### Priority

The Non-Negotiables in `AGENTS.md` and `git/workflow.md` always apply. Otherwise, when instructions conflict:

1. User's explicit request
2. `project.md` (including its overrides)
3. Core rules (`requirements/`, `coding/`, `security/`, `database/`, `devops/`, `frontend/`)
4. Active stack rules (`stacks/`)
5. General best practices

A stack rule never weakens a core rule. If they conflict, the core rule wins; stop and ask the user.

## File Index

### Project

- [`project.md`](project.md) — per-project configuration: product, active stacks, commands, environments, overrides.
- [`bootstrap.md`](bootstrap.md) — new-project setup questions.

### Git (locked)

- [`git/workflow.md`](git/workflow.md) — branch + Pull Request workflow. Never bypass.

### Requirements

- [`requirements/requirements.md`](requirements/requirements.md) — requirements engineering rules.
- [`requirements/perspectives.md`](requirements/perspectives.md) — perspectives to evaluate a feature from.
- [`requirements/architecture.md`](requirements/architecture.md) — core engine and extensibility.
- [`requirements/acceptance-criteria.md`](requirements/acceptance-criteria.md) — completeness checklist.
- [`requirements/testing.md`](requirements/testing.md) — **what** must be tested.

### Coding

- [`coding/architecture.md`](coding/architecture.md) — architecture and design rules.
- [`coding/code-quality.md`](coding/code-quality.md) — code quality rules.
- [`coding/testing.md`](coding/testing.md) — **how** tests are executed and reported.

Common design rules, mandatory for every platform and app ([`coding/design/README.md`](coding/design/README.md)):

- [`coding/design/reusability.md`](coding/design/reusability.md)
- [`coding/design/consistency.md`](coding/design/consistency.md)
- [`coding/design/scalability.md`](coding/design/scalability.md)
- [`coding/design/ecosystem-connectivity.md`](coding/design/ecosystem-connectivity.md) — comprehensiveness and connectivity.
- [`coding/design/maintainability-extensibility.md`](coding/design/maintainability-extensibility.md)

### Data, Security, DevOps

- [`database/database.md`](database/database.md) — database, migrations, modeling, time.
- [`security/security.md`](security/security.md) — authentication and security.
- [`devops/deployment.md`](devops/deployment.md) — environments and deployment.
- [`devops/ci-cd-and-release.md`](devops/ci-cd-and-release.md) — pipeline, release, infrastructure.
- [`devops/observability-and-operations.md`](devops/observability-and-operations.md) — logs, metrics, alerts, runbooks.

### Frontend Platforms

- [`frontend/shared.md`](frontend/shared.md) — baseline for every client, any framework.
- [`frontend/web/README.md`](frontend/web/README.md) — web: rendering, performance and SEO, accessibility, security, delivery.
- [`frontend/mobile/README.md`](frontend/mobile/README.md) — mobile: platform, performance and offline, UX, security, release.

### Stacks (active only when listed in `project.md`)

- [`stacks/backend/node-typescript.md`](stacks/backend/node-typescript.md) — Node.js + TypeScript backend base.
- [`stacks/backend/nestjs.md`](stacks/backend/nestjs.md) — NestJS (extends node-typescript).
- [`stacks/database/postgresql.md`](stacks/database/postgresql.md) — PostgreSQL and Node ORMs.
- [`stacks/frontend/angular.md`](stacks/frontend/angular.md) — Angular web.
- [`stacks/frontend/react-native-expo.md`](stacks/frontend/react-native-expo.md) — React Native + Expo (mobile and web).
