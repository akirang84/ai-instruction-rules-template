# Frontend: Expo, React Native, web and Tamagui

- Use React Native + Expo, Expo Router for navigation, and React Native Web for browser builds. Confirm any departure from this baseline.
- Use Tamagui for shared UI primitives and styling. Prefer accessible, reusable components and theme tokens over one-off visual values.
- Keep screens focused on composition and navigation; move reusable behavior into hooks/services and domain-specific modules. Avoid giant components and cross-feature imports into private internals.
- Keep platform-specific behavior explicit with supported platform files or small platform adapters. Verify that shared code works on iOS, Android, and web where applicable.
- English is the default locale. Put user-visible text through the selected i18n approach, preserve interpolation/pluralization, and avoid concatenating translated fragments. Confirm the i18n library at project start if none exists.
- At project start, recommend server-state and client-state approaches based on requirements and existing dependencies. Server/cache state and local UI state have different lifecycles; do not mirror server data into a client store without a reason. Avoid adding a global state library for state that can remain local or be derived.
- Keep API access in a typed client/service layer. Handle loading, empty, error, and retry states intentionally. Do not put secrets or privileged authorization logic in the client.
- Validate user input for usability on the client, but treat backend validation as authoritative.
- Consider keyboard behavior, screen readers, touch targets, reduced motion, responsive web layouts, and safe areas.
- Never store long-lived credentials in unprotected local storage. Follow `.claude/security.instruction.md` for token handling.
