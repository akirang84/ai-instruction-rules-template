# Backend: NestJS and TypeScript

- Use NestJS class-based conventions and OOP: `*.controller.ts`, `*.service.ts`, `*.module.ts`, DTO classes, and focused providers.
- Every endpoint must validate and transform untrusted input using DTO classes and `class-validator` / `class-transformer`. Configure global validation to reject unknown fields where compatible with the API contract. Never trust client-supplied identifiers, ownership, roles, prices, or derived values.
- Declare access modifiers explicitly (`public`, `protected`, `private`). Mark stable fields and injected dependencies `readonly`. Use `readonly` for values that should not change after construction.
- Never use `any`. Use `unknown` for truly dynamic data and narrow it with runtime guards or schema validation. Avoid unsafe casts and non-null assertions; justify unavoidable ones locally.
- Explicitly declare return types for all public class methods. Keep types precise at API, domain, and persistence boundaries.
- Inject dependencies through constructors. Do not instantiate concrete services inside methods or bypass Nest’s DI container.
- Keep controllers responsible for transport concerns; put application/domain behavior in services/use cases. Avoid leaking ORM entities directly as public API response types.
- Keep modules independent. Import other modules only through their exported providers and module declarations. Do not create circular module imports to shortcut a boundary.
- Use domain-specific error classes extending native `Error`, with stable error semantics. Map errors to HTTP responses in a boundary/filter; do not leak stack traces or internal details.
- Centralize configuration, validate required environment variables at startup, and fail fast on invalid configuration. Never hardcode credentials or secrets.
- Use structured logs with request/correlation identifiers. Do not log tokens, passwords, secrets, or sensitive personal data.
- Add pagination and bounded limits for collection endpoints. Make authorization checks server-side and close to the resource/use case.
