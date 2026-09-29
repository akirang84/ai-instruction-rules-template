# Architecture & Design

## Boundaries and Dependencies

- Keep modules cohesive and give each module a clear responsibility and owner for its data.
- Put business rules in the domain or application layer that owns them; keep transport, persistence, and framework details at the edges.
- Make dependencies point toward stable, higher-level policy. Avoid circular dependencies and cross-module access to internal implementation details.
- Keep side effects such as database access, network calls, filesystem access, and process execution behind clear boundaries.
- Reuse existing architectural patterns and abstractions. Introduce a new abstraction only when it supports a concrete requirement, meaningful variation, or a useful test boundary.

## Contracts and Evolution

- Treat APIs, events, and persisted data formats as contracts. Consider existing callers and stored data before changing them.
- Prefer explicit, backward-compatible contract changes. When a breaking change is necessary, identify affected consumers and provide a migration path.
- Make database and data migrations safe for existing data, repeatable where practical, and consistent with deployment order.
- Keep environment-specific values in configuration. Never couple application behavior to a developer machine or deployment environment implicitly.
- Model domain concepts and invariants explicitly; do not spread the same business decision across multiple layers.

## Design Tradeoffs

- Prefer the simplest design that satisfies the complete current requirement while preserving known extension points.
- Do not build speculative frameworks, generic layers, or extension mechanisms without a concrete use case.
- Before adding a dependency, verify that its scope and maintenance cost are justified and that an existing project utility does not already solve the need.
- Record important architectural decisions where the repository keeps design documentation, especially when the choice constrains future changes.
