# Comprehensiveness and Connectivity (Ecosystem)

Design and code must be complete across the whole system, not only the layer being edited.

- Trace every change end to end: UI, API, domain, persistence, jobs, integrations, configuration, docs, and tests. Update every affected layer in the same change.
- Identify all producers and consumers of each contract, event, and data format; verify the change against each of them.
- Define how the feature connects to existing modules, shared services, and external systems through explicit contracts (ports/adapters, events, APIs), not shortcuts.
- Cover cross-cutting concerns: authentication and authorization, validation, error handling, logging, auditing, observability, i18n, and accessibility where they apply.
- Define behavior across actors, states, and lifecycle (create, update, delete, retry, recovery), including failure and partial-failure paths.
- Keep design artifacts and code in sync: when behavior or contracts change, update diagrams, docs, schemas, and examples.
- Verify integration points with tests across the connected parts; a layer working alone is not evidence the ecosystem works.
