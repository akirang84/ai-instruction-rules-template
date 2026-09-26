# Project instructions for Claude Code

This file is the entry point. Read the applicable instructions in `.claude/` before planning or changing code. Keep this file short; detailed, scoped rules live in the linked files.

## Start of every new project / first session

1. Inspect the repository, README, package manifests, existing code, tests, CI, and deployment configuration before proposing a stack. Preserve established conventions unless they conflict with a rule here.
2. If this is a new/empty project, first learn the product goal, users, core workflows, platforms, expected scale, data sensitivity, integrations, budget/hosting constraints, and delivery priorities. Ask a concise, grouped set of questions for unknowns that materially affect architecture. Do not ask again for facts already present in the repo or conversation.
3. Present a short proposed project profile and ask the user to confirm unresolved choices before installing dependencies, scaffolding, or making architectural commitments. In particular confirm ORM (TypeORM or Prisma), database (PostgreSQL by default or explain an alternative), server-state and client-state libraries, deployment targets, and any material architecture decision. Recommend one option with reasons; do not silently choose unresolved items.
4. Once confirmed, record the decisions in the project README (or `docs/architecture/decisions.md` if the repo uses that convention), then implement in small, reviewable steps. If the user has already explicitly decided, treat that as confirmation.

## Default stack

- Backend: NestJS + TypeScript, class-based Nest conventions.
- ORM: TypeORM or Prisma; choose with the user at project start. Never mix ORMs in one service without explicit approval.
- Database: PostgreSQL by default; suggest an alternative only when requirements make it a better fit and obtain confirmation.
- Auth: JWT access + refresh tokens using `@nestjs/passport`.
- Input validation: DTO classes using `class-validator` and `class-transformer`.
- Frontend: React Native + Expo + Expo Router; web through React Native Web.
- UI: Tamagui.
- i18n: English is the default locale. Keep user-facing strings ready for localization.
- Server state and client state: recommend and confirm libraries at project start; avoid adding a state library without a demonstrated need.
- Deploy targets: production backend on Railway, staging backend on Render, frontend on Vercel, subject to confirmation against the project’s actual needs.

## Non-negotiable safeguards

- Before deleting data/files or making a large structural change, schema change, or breaking API change, explain the impact and wait for explicit confirmation. Do not execute the change while awaiting it.
- Store timestamps in UTC using PostgreSQL `timestamptz`. Convert to a user's timezone only at the application/display boundary. Use `users.timezone` for user-relative calculations such as “this month”.
- Keep modules independently reusable with explicit boundaries and dependencies.
- Never use `any`; validate untrusted input; never expose secrets. Use migrations for database changes.
- Follow `.claude/git-flow.instruction.md` for every change, including small changes. Never commit directly to `main` or `staging`.

## Instruction map

- Project discovery, decisions, boundaries: `.claude/architecture.instruction.md`
- NestJS and TypeScript: `.claude/backend.instruction.md`
- Expo, React Native Web, Tamagui and i18n: `.claude/frontend.instruction.md`
- Database, ORM, migrations and time: `.claude/database.instruction.md`
- Authentication and security: `.claude/security.instruction.md`
- Testing and verification: `.claude/testing.instruction.md`
- Environments and deployment: `.claude/deployment.instruction.md`
- Branch, commit, PR and merge flow: `.claude/git-flow.instruction.md`

Before editing, identify which files apply and read them. If an instruction conflicts with an existing project constraint, stop and surface the conflict instead of silently overriding either one.
