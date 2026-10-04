# Testing Requirements

Defines **what** must be tested for a requirement. How tests are executed and reported is defined in `.agents/coding/testing.md`.

## Purpose

Testing verifies that a requirement is correct from the user's perspective and that its business logic stays consistent across actors, states, and related features.

Testing is not limited to the happy path. For user-facing requirements, the primary strategy is End-to-End (E2E) testing through the Front End.

## Depth

Scale the depth of testing to the risk and size of the change.

- Trivial change (copy, styling, config with no behavior impact): verify the affected screen or output; sections 2–10 do not need a full pass.
- Non-trivial feature or any change to business rules, permissions, money, data, or state: apply every section below that is relevant.
- If a section does not apply, skip it. Do not invent scenarios for actors, states, or rules that do not exist.

## 1. Mindset

Act as a Tester Lead. The goal is not to prove the feature works; it is to try to break the business rules and show that invalid behavior cannot occur.

Do not assume the implementation follows the requirement. Test against the requirement, not against the code.

## 2. Analyze Before Testing

Before writing scenarios, identify:

- Actors, roles, and permissions
- User journeys
- Entities and their relationships
- Business rules
- Preconditions and postconditions
- Entity states, valid transitions, invalid transitions
- Business invariants
- Side effects and external dependencies
- Related features that share the same data or logic

If important behavior is ambiguous, state the ambiguity and ask or record it. Do not silently pick an assumption.

## 3. Actors

Identify every actor that can initiate, view, modify, delete, approve, reject, be affected by, or trigger a related state change for the data involved.

Actors may include end users, other users, admins, the system, background workers, and external services.

Do not test only the actor named in the requirement.

## 4. Cross-Actor Scenarios

When multiple actors can touch the same entity, test their interaction.

```text
User A creates Resource X
→ User B attempts to access Resource X
→ User B attempts to modify Resource X
→ Admin modifies Resource X
→ User A refreshes and verifies the final state
```

Verify authorization, ownership, visibility, consistency, and cross-user side effects.

## 5. Business Rules and Invariants

For each business rule, define at least one scenario that satisfies it and one that violates it.

Define invariants that must always hold, and verify them after every scenario that changes state. Examples:

- A total equals the sum of its parts
- A resource has exactly one owner
- A completed item cannot return to an earlier state
- A counter never goes negative

## 6. State Transitions

For every entity with a lifecycle:

- Test each valid transition.
- Test the invalid transitions that must be rejected (for example Cancelled → Updated, Deleted → Updated, Completed → Cancelled).
- Verify that a rejected transition leaves state and related data unchanged.

## 7. Input Validation and Boundaries

For each input or rule with limits, cover:

- Missing or empty value
- Minimum and maximum valid values
- Just below minimum and just above maximum
- Zero and negative values where meaningful
- Minimum and maximum length
- Maximum number of items
- Wrong format or type
- Special characters, whitespace-only, and very long text
- Date and time boundaries: before, exactly at, and after
- Time zone and daylight-saving effects when time is involved

## 8. Duplicate, Retry, and Concurrency

Test repeated and overlapping actions when they can affect correctness:

- Double submit and repeated clicks
- Refresh or navigate away during an operation
- Retry after failure
- Two actors changing the same data at the same time
- Stale data (acting on an item that was changed or deleted elsewhere)

Verify no duplicate records, payments, rewards, notifications, or events, and no lost updates, unless duplication is explicitly required.

## 9. Failure and Recovery

When an operation can fail (validation, network, dependency, timeout, partial failure):

- Verify the user sees a clear, correct error.
- Verify no partial, corrupted, or duplicated state is left behind.
- Verify the user can retry or recover and reach the correct final state.

## 10. Security and Access

- Unauthenticated access to protected pages and actions
- Access to another user's data (by direct URL or identifier)
- Actions beyond the actor's role
- Expired or revoked sessions
- Sensitive data not exposed in the UI, URLs, logs, or error messages

## 11. Cross-Feature Impact

When a feature changes shared data, identify every dependent feature (lists, totals, reports, dashboards, notifications, exports, search, integrations) and verify each one reflects the change. Verify existing data and existing users are unaffected.

## 12. Non-Functional Checks

Include only when relevant to the requirement:

- Loading, empty, and error states
- Large data volumes and pagination
- Responsive layouts and supported browsers
- Accessibility basics (keyboard use, labels, focus)
- Performance of critical paths
- Data migration and backward compatibility

## 13. Scenario Output

Before testing, produce a short scenario list covering the relevant sections above. For each scenario record:

- Actor(s) and preconditions
- Steps
- Expected UI result
- Expected business and persisted result
- Related state that must remain correct

Mark each scenario by priority: critical (core flow, money, permissions, data integrity), important, or optional. Critical scenarios must pass before a requirement is reported as verified.
