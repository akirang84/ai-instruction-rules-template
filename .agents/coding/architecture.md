# Architecture & Design

## Discovery Before Design

- Map the existing app boundaries, entry points, package manager, scripts, CI, tests, environment configuration, and deploy topology before proposing changes.
- For a new project, clarify: product purpose, user types, primary workflows, required platforms, data ownership and sensitivity, integrations, expected traffic and scale, offline needs, accessibility, constraints, and MVP scope.
- Recommend an architecture proportional to the product. Prefer a modular monolith initially unless deployment, scaling, ownership, or reliability requirements justify services. State the operational cost of distributed systems.
- Confirm unresolved architecture decisions with the user before installing dependencies or generating substantial scaffolding.

## Boundaries and Dependencies

- Keep modules cohesive and give each module a clear responsibility and owner for its data.
- Put business rules in the domain or application layer that owns them; keep transport, persistence, and framework details at the edges.
- Make dependencies point toward stable, higher-level policy. Avoid circular dependencies and cross-module access to internal implementation details.
- Keep side effects such as database access, network calls, filesystem access, and process execution behind clear boundaries.
- Reuse existing architectural patterns and abstractions. Introduce a new abstraction only when it supports a concrete requirement, meaningful variation, or a useful test boundary.
- Design around stable domain contracts and narrow ports; isolate vendor and framework details in adapters.
- Add, update, or remove variants (providers, strategies, policies, and similar) through registries or composition, not edits across unrelated flows.
- Prefer small cohesive modules and explicit capability/version metadata over giant configurable classes.

## Contracts and Evolution

- Treat APIs, events, and persisted data formats as contracts. Consider existing callers and stored data before changing them.
- Prefer explicit, backward-compatible contract changes. When a breaking change is necessary, identify affected consumers and provide a migration path.
- Version breaking contract changes and provide migration notes.
- Make database and data migrations safe for existing data, repeatable where practical, and consistent with deployment order.
- Keep environment-specific values in configuration. Never couple application behavior to a developer machine or deployment environment implicitly.
- Model domain concepts and invariants explicitly; do not spread the same business decision across multiple layers.

## Change Safety

- Before a broad reorganization, deleting a module, or changing a shared contract, schema, or public API, describe affected consumers, the migration and rollout path, and rollback implications. Wait for explicit confirmation before proceeding.
- Organize by business capability or domain, not only by technical layer. Each module owns its domain logic and exposes a public interface; depend on that interface, never on private implementation.
- One class or core module per file. Avoid generic "utils" dumping grounds.
- Use domain-specific errors and translate them to transport or API errors at the boundary.

## Design Tradeoffs

- Prefer the simplest design that satisfies the complete current requirement while preserving known extension points.
- Do not build speculative frameworks, generic layers, or extension mechanisms without a concrete use case.
- Before adding a dependency, verify that its scope and maintenance cost are justified and that an existing project utility does not already solve the need.
- Explain the extension point and its tests in the change summary.
- Record confirmed decisions and trade-offs in `docs/architecture/decisions.md` (or the project's existing decision log).
- Record important architectural decisions where the repository keeps design documentation, especially when the choice constrains future changes.
