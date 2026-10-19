# Frontend Shared Baseline

Applies to every client (web and mobile), whatever the framework. `web/`, `mobile/`, and the frontend files in `stacks/frontend/` extend this file; all of it extends `coding/design/`.

## Structure

- Screens and pages compose and navigate. Reusable behavior lives in services, hooks or stores, and domain modules. Avoid giant components and imports into another feature's private internals.
- Build a design system once (tokens, primitives, patterns) and reuse it. Use theme tokens and reusable accessible components, not one-off visual values or per-screen restyling.

## State and Data

- Recommend server-state and client-state approaches at project start, based on requirements and existing dependencies. Server/cache state and local UI state have different lifecycles; do not mirror server data into a client store without a reason.
- Do not add a global state library for state that can stay local or be derived.
- Keep API access in a typed client layer generated from or checked against the API contract. Handle loading, empty, error, and retry states intentionally, including optimistic updates with rollback where used.
- Validate input on the client for usability; backend validation is authoritative.

## Language and Accessibility

- English is the default locale. Route every user-visible string through the i18n library confirmed in `project.md`. Preserve interpolation and pluralization; never concatenate translated fragments. Format dates, numbers, and currency by locale and user timezone.
- Support keyboard and screen reader use, labels and roles, touch targets, focus order, reduced motion, dynamic type, color contrast, responsive layouts, and safe areas.

## Security

- No secrets or privileged authorization logic in the client. Anything bundled is public.
- Never store long-lived credentials in unprotected storage. Follow `security/security.md` and the platform specs for token handling.
