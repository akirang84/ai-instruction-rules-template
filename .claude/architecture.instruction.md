# Architecture and project discovery

## Discover before designing

- Map the existing app boundaries, entry points, package manager, scripts, CI, tests, environment configuration, and deploy topology before proposing changes.
- For a new project, clarify: product purpose, user types, primary workflows, required platforms, data ownership/sensitivity, integrations, expected traffic/scale, offline needs, accessibility, constraints, and MVP scope.
- Recommend an architecture proportional to the product. Prefer a modular monolith initially unless deployment, scaling, ownership, or reliability requirements justify services. Explain the operational cost of distributed systems.
- Confirm unresolved architecture decisions with the user before installing dependencies or generating substantial scaffolding. Record confirmed decisions and meaningful trade-offs in `docs/architecture/decisions.md` (create it if suitable) or the project’s existing decision log.

## Boundaries

- Organize by business capability/domain, not only by technical layer. Each module owns its domain logic and public interface.
- Modules must be reusable with minimal changes. Depend on a module's exported public API, never its private implementation.
- Keep dependency direction explicit. Avoid circular dependencies and cross-module reach-through. In NestJS, wire module dependencies through `*.module.ts`; extract a shared abstraction only when there is a real shared responsibility.
- Keep controllers/adapters thin. Put domain rules in domain/application services; isolate persistence and external integrations behind clear interfaces where useful.
- One class or one core module per file. Avoid generic “utils” dumping grounds and premature abstractions.
- Use domain-specific errors extending native `Error`; translate them to transport/API errors at the boundary.

## Change safety

- Before a broad reorganization, deleting a module, changing a shared contract, schema, or breaking API, describe affected consumers, migration/rollout path, and rollback implications. Wait for explicit confirmation before proceeding.
- Prefer additive, backward-compatible changes. Update API contracts and relevant docs when behavior changes.
- Avoid adding a dependency or a new architectural layer unless it solves a current requirement. State the reason and alternatives in the proposal.
