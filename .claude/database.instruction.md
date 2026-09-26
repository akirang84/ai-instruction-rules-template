# Database, ORM, migrations and time

- PostgreSQL is the default. At project start, recommend PostgreSQL or a specific alternative based on data shape, transaction needs, deployment constraints, and scale; confirm before committing to it.
- Select either TypeORM or Prisma with the user at project start. Do not combine them casually or switch later without explicit approval and a migration plan.
- All schema changes must be represented by versioned migration scripts. Never make manual production/staging schema edits or rely on ORM auto-sync in deployed environments.
- Review migrations for data loss, locking, runtime, backfill needs, and compatibility with currently deployed application versions. For destructive or breaking schema changes, explain the rollout and wait for explicit confirmation.
- Store timestamps in UTC using PostgreSQL `timestamptz`. Treat application instants as UTC; do not store local wall-clock timestamps without a deliberate domain requirement.
- Convert to the user’s timezone only when presenting or computing user-local periods. Use `users.timezone` (IANA timezone identifier) as the anchor for calculations such as “this month”; calculate local period boundaries, then query using the corresponding UTC instants.
- Define foreign keys, uniqueness, nullability, indexes, and delete behavior intentionally. Keep constraints in migrations and model them in the application.
- Use transactions for multi-step operations that must succeed or fail together. Make retryable jobs and external side effects idempotent where practical.
- Avoid exposing ORM models/entities directly as API contracts. Map between persistence models and domain/DTO types at a deliberate boundary.
- Document seed data and ensure it cannot accidentally run against production.
