# Backend: NestJS and TypeScript

Stack-specific rules. They extend `coding/` and `coding/design/`; they never weaken them.

## Structure

- Use NestJS class-based conventions: `*.controller.ts`, `*.service.ts`, `*.module.ts`, DTO classes, and focused providers.
- Controllers own transport concerns only. Application and domain behavior lives in services or use cases.
- Inject dependencies through constructors. Never instantiate concrete services inside methods or bypass the DI container.
- Keep modules independent. Import other modules only through their exported providers. Wire dependencies in `*.module.ts`; no circular module imports to shortcut a boundary.
- Do not expose ORM entities as API responses. Map persistence models to domain and DTO types at a deliberate boundary.

## Types

- Never use `any`. Use `unknown` for dynamic data and narrow it with guards or schema validation. Avoid unsafe casts and non-null assertions; justify unavoidable ones locally.
- Declare access modifiers explicitly. Mark stable fields and injected dependencies `readonly`.
- Declare return types on all public methods. Keep types precise at API, domain, and persistence boundaries.

## Input, Errors, Config

- Validate and transform every endpoint input with DTOs plus `class-validator` / `class-transformer`. Configure global validation to reject unknown fields where compatible with the contract.
- Never trust client-supplied identifiers, ownership, roles, prices, or derived values.
- Use domain-specific error classes extending `Error` with stable semantics. Map them to HTTP responses in a filter; never leak stack traces or internals.
- Centralize configuration, validate required environment variables at startup, and fail fast. Never hardcode secrets.

## API Behavior

- Paginate collection endpoints with bounded limits.
- Enforce authorization server-side, close to the resource or use case.
- Make mutating endpoints idempotent where retries are possible (idempotency keys or natural keys).
- Version breaking API changes and keep the API contract (OpenAPI) in sync with behavior.
- Use structured logs with request/correlation IDs. Never log tokens, passwords, secrets, or sensitive personal data.
