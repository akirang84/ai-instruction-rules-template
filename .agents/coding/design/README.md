# Common Design Rules

These files are the **common specification** for every platform and app in the repository.

- Every rule here is mandatory. Follow it strictly, not as a suggestion.
- Platform-specific specs (for example web, mobile) extend these rules with platform detail. They must not weaken, contradict, or bypass them.
- If a platform spec conflicts with a common rule, the common rule wins. Stop and ask the user instead of deviating.
- A platform spec should reference the relevant common file instead of restating it.

| Quality | File |
|---|---|
| Reusability | [`reusability.md`](reusability.md) |
| Consistency | [`consistency.md`](consistency.md) |
| Scalability | [`scalability.md`](scalability.md) |
| Comprehensiveness and Connectivity (Ecosystem) | [`ecosystem-connectivity.md`](ecosystem-connectivity.md) |
| Maintainability and Extensibility | [`maintainability-extensibility.md`](maintainability-extensibility.md) |
