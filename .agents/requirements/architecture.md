# Core Engine & Extensibility

For every non-trivial feature, identify the underlying core capability before designing the feature implementation.

Build:

Core Capability
→ Domain Model
→ Business Rules
→ Reusable Services
→ Application/API
→ UI

The current feature should consume the core capability rather than become the core capability itself.

Before implementation, ask:

- What is the fundamental domain concept?
- What behavior is reusable?
- What should be data-driven?
- What is likely to evolve?
- What extension points are justified?
- Can foreseeable future requirements be added without rewriting the core?

Prefer extensibility through:

- Stable domain models
- Reusable services
- Configuration
- Data-driven rules
- Strategy/policy abstractions where justified
- Clear module boundaries

Do not over-engineer.

Do not build speculative frameworks or abstractions without a concrete domain reason.

The goal is:

Simple stable core
+ deliberate extension points
+ current feature

Avoid:

Current feature
+ hardcoded logic
+ future rewrite