# Testing Rules

Defines **how** tests are designed, executed, and reported. What to test is defined in `.agents/requirements/testing.md`; read it first.

## Levels

Use the narrowest level that gives meaningful confidence, and combine levels.

- Unit: isolated business rules and pure logic.
- Integration/API: component boundaries, persistence, authorization.
- E2E: user journeys through the real Front End.

For user-facing requirements, E2E through the Front End is the primary verification. Unit and API tests complement it and never replace it.

Non-user-facing code (libraries, CLIs, jobs, backend services) is verified at the unit and integration levels, plus a run of the real entry point where practical.

Scale effort to the change: a trivial change needs a focused check, not the full E2E suite.

## Test Design

- Test observable behavior and contracts, not private implementation details.
- Cover the normal path, boundaries, invalid input, empty or missing data, and failure behavior.
- Assert outcomes, state changes, and externally meaningful side effects. Do not couple tests to call order or internal structure.
- Keep assertions specific enough to explain a failure without being brittle to unrelated output.
- Add a regression test for every fixed defect; confirm it fails against the old behavior.
- Update tests when behavior or a public contract changes. Never weaken or delete an assertion only to make a failing implementation pass.

## Reliability and Data

- Tests must be deterministic and independent of execution order, wall-clock time, uncontrolled randomness, and external services.
- Each test creates the state it needs, runs, and cleans up. Do not rely on another test's side effects, arbitrary existing records, or hardcoded IDs.
- Use the repository's fixtures and helpers. Avoid shared mutable state.
- Use fakes or mocks only at true system boundaries. Prefer real collaborating code when it is fast and reliable.
- Do not put credentials or real personal data in tests. Stub external effects unless the test validates that integration.

## E2E Execution

### Environment

Before running, verify the Front End, Backend, Database, external dependencies (or their mocks), test accounts, and configuration are available.

If the environment prevents testing, report it as an environment failure (BLOCKED), not a product failure. Do not fall back to API-only checks and report PASS.

If no browser automation is available, say so, run what can be run, and report the E2E scenarios as BLOCKED with the exact steps for a human to execute.

### Interaction

- Drive the real Front End like a user: click controls, fill forms, navigate, refresh, log in and out.
- Do not bypass the Front End in the primary journey by calling APIs or manipulating state with JavaScript.
- Direct API, database, or script access is allowed for test setup, cleanup, inspecting internal state, diagnosing failures, and scenarios that cannot reasonably be created through the UI.
- For multi-actor scenarios, use separate sessions or accounts and establish each actor's state explicitly.

### What to verify after each important action

- UI result: correct page, displayed data, validation or error message, enabled/disabled controls, loading and empty states.
- Business result: entity created, updated, or deleted; correct status and calculated values; related data updated; permissions applied; expected side effects present and no unintended ones.
- Persistence: navigate away, return, and refresh, and confirm the result remains.
- Related features: check the dependent features identified in the requirements, not only the screen where the action happened.

A success toast, an HTTP 200, a successful build, or passing unit tests is not proof that a requirement works.

## Failures

When a test fails:

1. Capture the scenario, failing step, expected and actual result, and evidence (screenshot, console and network errors, logs, relevant state).
2. Classify the cause: application defect, test defect, test-data defect, or environment defect.
3. For an application defect, fix the root cause, re-run the failing test, then the related tests, then the regression set. Keep the failing scenario as a regression test.

Distinguish regressions from pre-existing or unrelated failures, and report unresolved failures clearly.

Never remove an assertion, weaken an expectation, skip a scenario without justification, or change a test to match incorrect behavior.

## Validation Order

1. Run focused tests for the changed behavior.
2. Run related and regression tests for shared logic, permissions, calculations, state transitions, and dependent UI.
3. Run broader checks when available: full test suite, type check, lint, build.

## Completion Criteria

A user-facing requirement is verified only when:

- Critical scenarios pass: E2E journeys, negative, boundary, actor interaction, and state transition scenarios relevant to the change.
- Business invariants hold and persistence is confirmed where applicable.
- Related features are correct and no critical regression is detected.

Any relevant scenario that was not tested must be reported as a limitation. Do not report PASS while a critical scenario is untested or blocked.

## Final Report

Keep it concise.

```text
Requirement:
Test Status: PASS / FAIL / BLOCKED / PARTIAL
Scenarios executed:
Passed / Failed / Blocked:
Defects found:
Regression: PASS / FAIL
Unverified risks and limitations:
```
