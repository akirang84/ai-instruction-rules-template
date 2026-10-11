# Reusability

- Identify the reusable capability (domain concept, service, component, contract) before building the feature that consumes it.
- Search for an existing utility, component, or service first; extend it before creating a parallel one.
- Extract shared logic only after a real second use or a clear domain concept. Do not abstract for hypothetical reuse.
- Keep reusable units free of feature-specific assumptions: pass behavior and data in through parameters, configuration, or injected dependencies.
- Give reusable units a single responsibility, a documented contract, and their own tests.
- Share across layers and apps through explicit packages or modules, not copy-paste or reaching into internals.
