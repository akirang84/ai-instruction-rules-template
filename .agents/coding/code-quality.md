# Code Quality

## Implementation

- Make the smallest complete change that solves the requested behavior. Avoid unrelated refactoring and formatting churn.
- Follow the language, framework, and neighboring-code conventions already established in the repository.
- Prefer clear names and small, cohesive functions. Keep control flow and state changes easy to follow; avoid hidden side effects.
- Reuse existing utilities and dependencies when they fit. Avoid duplicate logic, but do not introduce an abstraction solely to remove a small amount of repetition.
- Use types and domain-specific values to make invalid states harder to represent where the language supports it. Avoid unsafe casts and loosely typed escape hatches without a documented reason.
- Keep constants and policy decisions visible and named when they affect behavior; avoid unexplained literal values.

## Correctness and Safety

- Validate and normalize untrusted input at system boundaries. Enforce authorization and business invariants in the layer that owns the operation, not only in the UI.
- Use safe, structured APIs for queries, serialization, paths, and process execution; do not construct executable commands or queries from untrusted strings.
- Handle expected failures explicitly. Do not silently swallow errors; preserve useful context when translating or propagating them.
- Release resources reliably, including on failure paths. Make retries, concurrency, and repeated requests safe where those behaviors are possible.
- Do not expose secrets, credentials, personal data, or sensitive payloads in logs, error messages, or test fixtures.
- Keep secrets out of source control and load environment-specific configuration through the project's established mechanism.

## Maintainability

- Comments should explain intent, constraints, or non-obvious tradeoffs rather than restate the code.
- Update user-facing or developer documentation when behavior, configuration, or public contracts change.
- Remove obsolete code only when it is part of the requested change; do not leave dead code as an alternate implementation.
- Use the repository's formatter, linter, and static analysis tools when available. Do not suppress diagnostics broadly to make a check pass.
