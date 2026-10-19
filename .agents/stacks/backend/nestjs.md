# Stack: NestJS

Active when `project.md` lists `nestjs`. Extends `stacks/backend/node-typescript.md`, `coding/`, and `coding/design/`; never weakens them.

## Structure

- Use NestJS class-based conventions: `*.controller.ts`, `*.service.ts`, `*.module.ts`, DTO classes, and focused providers.
- Controllers own transport concerns only. Application and domain behavior lives in services or use cases.
- Inject dependencies through constructors. Never instantiate concrete services inside methods or bypass the DI container.
- Keep modules independent. Import other modules only through their exported providers. Wire dependencies in `*.module.ts`; no circular module imports to shortcut a boundary.
- Do not expose ORM entities as API responses. Map persistence models to domain and DTO types at a deliberate boundary.

## Types

- Declare access modifiers explicitly. Mark stable fields and injected dependencies `readonly`.

## Input, Errors, Config

- Validate and transform every endpoint input with DTOs plus `class-validator` / `class-transformer`. Configure global validation to reject unknown fields where compatible with the contract.
- Never trust client-supplied identifiers, ownership, roles, prices, or derived values.
- Map domain errors to HTTP responses in an exception filter.
- Use `@nestjs/config` with a validation schema for configuration.

## Authentication

- Default: JWT access and refresh tokens through `@nestjs/passport`, unless `project.md` confirms an identity provider or another approach. Follow `security/security.md`.

## API Behavior

- Paginate collection endpoints with bounded limits.
- Enforce authorization server-side with guards and policies close to the resource or use case.
- Make mutating endpoints idempotent where retries are possible (idempotency keys or natural keys).
- Version breaking API changes and keep the OpenAPI contract (`@nestjs/swagger`) in sync with behavior.
- Use structured logs with request/correlation IDs.

## Testing

- Unit-test services with Nest's `Test.createTestingModule` and real collaborators where fast. Test HTTP behavior with `supertest` against the app module.
