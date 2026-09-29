# Testing

## Test Design

- Test observable behavior and contracts rather than private implementation details.
- Choose the narrowest test level that gives meaningful confidence: unit tests for isolated rules, integration tests for component boundaries, and end-to-end tests for critical user workflows.
- Cover the normal path plus relevant boundary values, invalid input, empty or missing data, and failure behavior.
- Add a regression test for a fixed defect when practical; ensure the test would fail against the prior behavior.
- Assert outcomes, state changes, and externally meaningful side effects. Avoid coupling tests to incidental call order or internal structure.

## Reliability

- Keep tests deterministic and independent of execution order, wall-clock timing, uncontrolled randomness, and external services.
- Use the repository's fixtures and test helpers. Isolate test data, clean up resources, and avoid shared mutable state between tests.
- Use fakes or mocks at true system boundaries; prefer exercising real collaborating code when it remains fast and reliable.
- Do not put credentials or real personal data in tests. Stub network and other external effects unless the test specifically validates that integration.
- Keep assertions specific enough to explain what failed without making tests brittle to unrelated output changes.

## Validation

- Run focused tests for the changed behavior first, then relevant broader checks such as the full test suite, type checking, linting, or builds when available.
- When a check fails, distinguish a regression from an existing or unrelated failure; report unresolved failures clearly.
- Update tests when a behavior or public contract changes. Do not weaken or remove an assertion solely to make a failing implementation pass.
