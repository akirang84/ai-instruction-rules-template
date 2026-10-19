# Stack: PostgreSQL

Active when `project.md` lists `postgresql`. Extends `database/database.md`; never weakens it.

## Version and Access

- Use the PostgreSQL major version confirmed in `project.md`, identical across local, CI, and deployed environments.
- Application, migration, and read-only roles are separate database users with least privilege. The application user cannot alter schema.
- Use a connection pool sized for the instance count and the database's `max_connections`; use a pooler (for example PgBouncer) when instances scale out.

## ORM (Node.js / TypeScript)

- Use the ORM confirmed in `project.md`: Prisma or TypeORM (or a query builder such as Kysely or Drizzle if confirmed). Do not combine them casually or switch later without explicit approval and a migration plan.
- Migrations are generated or written with that tool, reviewed as SQL, and committed. `synchronize` / `db push` are allowed only in local throwaway databases.
- Do not expose ORM entities or models outside the persistence layer.

## Types and Modeling

- Timestamps: `timestamptz`, stored in UTC. Business dates without time: `date`.
- Money and exact quantities: `numeric(p, s)`, never `real` or `double precision`.
- IDs: the type confirmed in `project.md` (for example `uuid` or `bigint` identity). Use one type consistently.
- Enumerations: a lookup table or `text` with a `CHECK` constraint when values will change; native `enum` only for stable sets.
- Use `jsonb` only for genuinely schemaless data, never to avoid modeling.

## Migrations and Locking

- Create indexes on existing large tables with `CREATE INDEX CONCURRENTLY` (outside a transaction).
- Add `NOT NULL` or foreign keys to large tables in steps: add as `NOT VALID`, backfill, then `VALIDATE CONSTRAINT`.
- Set `lock_timeout` and `statement_timeout` for migrations so they fail rather than block traffic.
- Backfill in batches, not one long transaction.

## Queries

- Check hot-path queries with `EXPLAIN (ANALYZE, BUFFERS)` before release.
- Use keyset pagination for large or frequently paged tables.
- Enable `pg_stat_statements` in deployed environments to find slow queries.
