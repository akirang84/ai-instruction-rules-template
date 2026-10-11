# Frontend Shared Baseline: Expo, React Native, Tamagui

Applies to the web and mobile clients that share one codebase. `web/` and `mobile/` extend this file; all of it extends `coding/design/`.

## Stack

- React Native + Expo, Expo Router for navigation, React Native Web for browser builds. Confirm any departure from this baseline.
- Tamagui for shared UI primitives and styling. Use theme tokens and reusable accessible components, not one-off visual values.

## Structure

- Screens compose and navigate. Reusable behavior lives in hooks, services, and domain modules. Avoid giant components and imports into another feature's private internals.
- Keep platform-specific behavior explicit through platform files (`.web.tsx`, `.native.tsx`) or small adapters. Verify shared code on iOS, Android, and web.
- Build a design system once (tokens, primitives, patterns) and reuse it. Do not restyle per screen.

## State and Data

- Recommend server-state and client-state approaches at project start, based on requirements and existing dependencies. Server/cache state and local UI state have different lifecycles; do not mirror server data into a client store without a reason.
- Do not add a global state library for state that can stay local or be derived.
- Keep API access in a typed client layer generated from or checked against the API contract. Handle loading, empty, error, and retry states intentionally, including optimistic updates with rollback where used.
- Validate input on the client for usability; backend validation is authoritative.

## Language and Accessibility

- English is the default locale. Route every user-visible string through the i18n library (confirm the library at project start). Preserve interpolation and pluralization; never concatenate translated fragments. Format dates, numbers, and currency by locale and user timezone.
- Support keyboard and screen reader use, labels and roles, touch targets, focus order, reduced motion, dynamic type, color contrast, responsive layouts, and safe areas.

## Security

- No secrets or privileged authorization logic in the client. Anything bundled is public.
- Never store long-lived credentials in unprotected storage. Follow `security/security.md` and the platform specs for token handling.
