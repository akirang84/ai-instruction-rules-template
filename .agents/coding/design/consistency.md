# Consistency

- Follow existing conventions for naming, structure, error handling, API shape, and UI patterns. Do not introduce a second way to do the same thing.
- Use one canonical representation per concept (types, units, timezones, enums, IDs, formats) across UI, API, domain, and database.
- Keep one source of truth for each business rule and each piece of data; derive everything else from it.
- Use the same terminology in requirements, code, UI copy, API fields, and docs.
- Keep error, loading, empty, and success behavior uniform across similar features.
- If an existing convention is wrong, change it deliberately in its own task and migrate all usages; do not diverge locally.
