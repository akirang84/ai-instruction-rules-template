# Database, ORM, Migrations, and Time

## Choices

- PostgreSQL is the default. At project start recommend PostgreSQL or a specific alternative based on data shape, transaction needs, deployment constraints, and scale; confirm before committing.
- Choose either TypeORM or Prisma with the user at project start. Do not combine them casually or switch later without explicit approval and a migration plan.

## Migrations

- Every schema change is a versioned migration script. No manual production or staging edits and no ORM auto-sync in deployed environments.
- Review each migration for data loss, locking, runtime, backfill, and compatibility with the currently deployed application version.
- Use expand/contract for breaking changes: add new structure, deploy code that supports both, backfill, then remove the old structure in a later release.
- For destructive or breaking changes, explain the rollout and rollback path and wait for explicit confirmation.
- Migrations are repeatable in a clean environment and tested against realistic data where risk is high.
- Document seed data and make sure it can never run against production.

## Modeling

- Define foreign keys, uniqueness, nullability, indexes, and delete behavior intentionally, in migrations and in the application model.
- Index for known query patterns. Verify hot paths with the query plan; avoid N+1 access.
- Use transactions for multi-step operations that must succeed or fail together. Make retryable jobs and external side effects idempotent.
- Store money and quantities with exact numeric types, never floating point.
- Plan retention, archival, and deletion for personal and high-volume data.
- Back up production data and verify restore. State the recovery point and recovery time the product needs.

## Time

- Store timestamps in UTC with `timestamptz`. Do not store local wall-clock time unless the domain requires it.
- Convert to the user's timezone only for presentation or user-local periods. Use `users.timezone` (IANA identifier) as the anchor: compute local period boundaries, then query with the matching UTC instants.
