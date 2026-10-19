# Stack: Node.js + TypeScript (Backend)

Active when `project.md` lists `node-typescript`. Base for every Node backend; framework files such as `nestjs.md` extend it. Extends `coding/` and `coding/design/`; never weakens them.

## Runtime and Tooling

- Use the Node LTS version and package manager confirmed in `project.md`. Pin them (`.nvmrc` or `engines`, and `packageManager`) and keep local, CI, and deployed runtimes identical.
- Commit the lockfile. Install in CI with the frozen-lockfile command.
- Use one module system per package (ESM or CommonJS) as confirmed in `project.md`.
- TypeScript `strict: true`. Lint with ESLint (typescript-eslint) and format with Prettier or the project's confirmed formatter.

## Types

- Never use `any`. Use `unknown` for dynamic data and narrow it with guards or schema validation. Avoid unsafe casts and non-null assertions; justify unavoidable ones locally.
- Declare return types on exported functions and public methods. Keep types precise at API, domain, and persistence boundaries.
- Validate external input (HTTP, queues, files, environment) at runtime with a schema library; static types are not validation.

## Configuration and Errors

- Load configuration once, validate required environment variables at startup, and fail fast. Never hardcode secrets.
- Use domain-specific error classes extending `Error` with stable semantics. Map them to transport errors at the boundary; never leak stack traces or internals.
- Handle every promise. Register `unhandledRejection` and `uncaughtException` handlers that log and exit so the platform restarts the process.
- Implement graceful shutdown on `SIGTERM`: stop accepting work, finish in-flight requests and jobs, close connections.

## Performance

- Never block the event loop with CPU-heavy or synchronous I/O work on the request path; move it to workers or jobs.
- Set timeouts on every outbound call. Reuse HTTP and database connections through pools.

## Logging

- Structured JSON logs with a fast logger (for example pino) and request/correlation IDs. Never log tokens, passwords, secrets, or sensitive personal data.

## Testing

- Unit and integration tests with the runner confirmed in `project.md` (for example Vitest or Jest). Integration tests run against a real PostgreSQL (for example Testcontainers or a CI service), not mocks of the database.
