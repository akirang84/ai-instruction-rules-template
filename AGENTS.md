# Agent Instructions

## Core Principles

- Follow the repository Git workflow defined in `.agents/git/workflow.md`.
- Follow the requirements engineering rules defined in `.agents/requirements/`.
- Follow the coding and architecture rules defined in `.agents/coding/`.

## Requirements

Before implementing any non-trivial feature:

1. Read `.agents/requirements/requirements.md`.
2. Read `.agents/requirements/perspectives.md`.
3. Read `.agents/requirements/architecture.md`.
4. Read `.agents/requirements/acceptance-criteria.md`.

Requirements must be complete across business, UX, frontend, backend, database, testing, and production concerns.

## Git

Follow `.agents/git/workflow.md`.

Never bypass the repository branch and Pull Request workflow.

## Testing

When implementing or verifying a requirement:

1. Read `.agents/requirements/testing.md` to determine what must be tested.
2. Read `.agents/coding/testing.md` to determine how the tests must be executed.
3. For user-facing functionality, prioritize E2E testing through the Front End.
4. Do not consider a feature verified based only on unit tests or API responses.
5. Do not declare success until the relevant business rules, actors, states, and invariants have been verified.

## Context Management

After a feature is completed (PR created and results reported), end the final message by reminding the user to run `/clear` before starting the next task, to save tokens.

Do not carry context from a completed feature into the next one.

## Priority

When instructions conflict:

1. User's explicit request
2. Repository-specific requirements
3. Architecture rules
4. Coding conventions
5. General best practices