# Stack: Angular

Active when `project.md` lists `angular`. Extends `frontend/shared.md` and `frontend/web/`. Never weakens them.

## Project Setup

- Use the Angular version confirmed in `project.md` and the Angular CLI defaults for build and test. Upgrade with `ng update` as scheduled work, one major version at a time.
- Enable `strict` TypeScript and `strictTemplates`. Lint with `angular-eslint`.

## Structure

- Standalone components, organized by feature (`features/<name>/`), with shared UI in a `shared/` or design-system library. No shared mutable state between features except through services.
- Components present; services hold behavior and data access. Keep templates free of business logic.
- Use `OnPush` change detection. Prefer signals for local and derived state; use RxJS for streams and async coordination, and convert at the boundary (`toSignal`, `toObservable`).
- Lazy-load feature routes. Use functional guards and resolvers; guards are UX only, the server enforces access.
- Use typed reactive forms for non-trivial forms.

## Data and HTTP

- `HttpClient` with functional interceptors for auth headers, correlation IDs, and error mapping. API types are generated from or checked against the OpenAPI contract.
- Unsubscribe automatically (`takeUntilDestroyed`, `async` pipe, signals). No manual subscriptions without cleanup.
- Use the server-state approach confirmed in `project.md` (plain services with signals, or a store library). Do not add NgRx or another store without a stated need.

## Rendering

- Choose CSR, SSR, or prerendering per route as `frontend/web/architecture-and-rendering.md` requires. With SSR, use hydration and keep browser-only APIs behind injected adapters (`isPlatformBrowser`, `DOCUMENT`).
- Use `@defer` for heavy below-the-fold features and `NgOptimizedImage` for images.

## Security

- Rely on Angular's template sanitization. Never call `bypassSecurityTrust*` on untrusted input; any use needs a one-line justification next to it.
- Use Angular's XSRF support for cookie-based auth.

## Accessibility and i18n

- Use Angular CDK a11y utilities (focus trap, live announcer) and the component library confirmed in `project.md`.
- Use the i18n library confirmed in `project.md` (Angular built-in i18n or a runtime library); follow `frontend/shared.md` for strings and formatting.

## Testing

- Unit and component tests with the CLI's configured runner and Angular Testing Library or `TestBed`. E2E with Playwright.
