# Testing and verification

- Follow the existing test framework and conventions. If starting from an empty project, propose a proportionate test setup and confirm any material tooling choice.
- Add or update focused tests for changed behavior: unit tests for domain rules, integration tests for persistence/boundaries, and end-to-end tests for critical user/API flows.
- Test validation failures, authorization boundaries, error paths, and relevant timezone/UTC edge cases where those behaviors change.
- Keep tests deterministic. Avoid dependence on live external services; use test doubles or isolated test resources.
- Before reporting completion, inspect `git status` and the diff; run the relevant formatter/linter, type check, and tests available in the repository. Report commands run and failures accurately. Do not claim checks passed if they were not run.
- If checks cannot run because tooling/dependencies/services are unavailable, say exactly what was blocked and what remains unverified.
- Do not weaken, delete, skip, or rewrite a failing test merely to make a change pass. Explain the failure and fix the underlying issue or ask when the expected behavior is ambiguous.
