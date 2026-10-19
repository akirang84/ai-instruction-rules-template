# Project Configuration

Status: NOT CONFIGURED
Template version: 1.0.0

> The only rules file filled in per project. Agents: while Status is `NOT CONFIGURED`, run [`bootstrap.md`](bootstrap.md) before any other task.
> Values marked `TBD` are open decisions: ask before relying on them.

## 1. Product

- Name: TBD
- Purpose (one paragraph): TBD
- MVP scope: TBD
- Out of scope: TBD
- Actors and roles: TBD
- Domain expert perspectives (`requirements/perspectives.md`): TBD
- Glossary (term: meaning): TBD

## 2. Platforms and Active Stacks

Agents read only the stack files listed here. Delete lines that do not apply.

| Area | Choice | Rules file |
|---|---|---|
| Backend runtime | Node.js + TypeScript | `stacks/backend/node-typescript.md` |
| Backend framework | TBD (NestJS / other) | `stacks/backend/nestjs.md` |
| Database | PostgreSQL TBD (major version) | `stacks/database/postgresql.md` |
| Data access | TBD (Prisma / TypeORM / other) | `stacks/database/postgresql.md` |
| Web frontend | TBD (Angular / React Native Web / none) | `stacks/frontend/angular.md` or `stacks/frontend/react-native-expo.md` |
| Mobile app | TBD (React Native + Expo / none) | `stacks/frontend/react-native-expo.md` |

Platform specs: web `frontend/web/` TBD (yes/no), mobile `frontend/mobile/` TBD (yes/no).

## 3. Technical Decisions

- Repository layout (single app / monorepo + tool): TBD
- Node LTS version, package manager, module system (ESM/CJS): TBD
- Test runner (backend / frontend), E2E tool (web / mobile): TBD
- Authentication approach (`security/security.md`): TBD
- ID type (uuid / bigint): TBD
- UI component library: TBD
- Client state / server-state approach: TBD
- i18n library and locales: TBD (default locale: English)
- Supported browsers / OS versions / devices: TBD
- Mobile build service and OTA: TBD

## 4. Environments and Hosting

| Environment | Backend | Frontend | Database | URL |
|---|---|---|---|---|
| Local | TBD | TBD | TBD | TBD |
| Staging | TBD | TBD | TBD | TBD |
| Production | TBD | TBD | TBD | TBD |

- Region / data residency: TBD
- Secret store: TBD
- Error tracking, logs, metrics: TBD

## 5. Commands

Agents run these exact commands. Never guess.

| Purpose | Command |
|---|---|
| Install | TBD |
| Run locally | TBD |
| Lint / format | TBD |
| Type check | TBD |
| Unit + integration tests | TBD |
| E2E tests | TBD |
| Build | TBD |
| Create / run migration | TBD |
| Seed local data | TBD |

Test accounts (names and roles only, never passwords): TBD

## 6. Non-Functional Requirements

- Expected users, request rate, data volume, growth: TBD
- Availability / SLO for critical paths: TBD
- RPO / RTO: TBD
- Compliance (GDPR, PCI, HIPAA, none): TBD
- Personal or sensitive data handled: TBD
- Budget constraints: TBD

## 7. Process

- Ticket system and key prefix (for branch names and PRs): TBD
- Requirements docs location: TBD (default `docs/requirements/`)
- Decision log location: TBD (default `docs/architecture/decisions.md`)
- Reviewers / code owners: TBD

## 8. Project Overrides

Deviations from core or stack rules. Each needs the rule, the change, the reason, and who approved it. `git/workflow.md` cannot be overridden here.

| Rule (file + line) | Override | Reason | Approved by / date |
|---|---|---|---|
| — | — | — | — |
