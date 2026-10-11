# Maintainability and Extensibility

Complements `../architecture.md` and `../code-quality.md`; follow those for module boundaries and contracts.

- Optimize for the next reader: clear names, small cohesive units, explicit data flow, and comments that explain intent.
- Put expected variation behind deliberate extension points (registries, strategies, configuration, data-driven rules). Justify each with a concrete, foreseeable need.
- Adding a new variant should not require editing unrelated flows. If it does, the boundary is wrong.
- Keep changes local: a change in one module should not ripple into unrelated modules.
- Make behavior testable in isolation by injecting dependencies and keeping side effects at the edges.
- Remove dead code and obsolete paths as part of the change that replaces them.
- Do not add speculative frameworks or options. Simple stable core plus deliberate extension points.
