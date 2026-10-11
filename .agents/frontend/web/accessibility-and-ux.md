# Web: Accessibility and UX

## Accessibility

- Target WCAG 2.2 AA. Treat accessibility defects as functional defects.
- Use semantic HTML first (landmarks, headings, buttons, links, form controls). Add ARIA only when native semantics are insufficient.
- Everything usable by keyboard with a visible focus indicator and a logical focus order. Manage focus on route changes, dialogs, and error summaries; no keyboard traps.
- Every control has an accessible name. Form fields have associated labels, error messages linked to their fields, and clear required-state cues.
- Meet color contrast, do not rely on color alone, respect `prefers-reduced-motion`, and support zoom to 200% and text resize without loss of content.
- Provide alt text for meaningful images, captions or transcripts for media, and announce dynamic updates with live regions.
- Verify with automated checks in CI plus manual keyboard and screen reader passes on critical journeys.

## Responsive and Browser Support

- Design mobile-first and test at representative breakpoints, orientations, and zoom levels. No horizontal page scroll at phone width.
- State the supported browser and OS matrix and test the critical journeys on it. Use progressive enhancement for features outside the matrix.
- Use touch-friendly targets and avoid hover-only interactions.

## UX States

- Every async view defines loading (skeleton or progress), empty (with next action), error (with recovery), partial, and success states.
- Forms: validate inline without blocking typing, keep user input on error, prevent double submit, and confirm destructive actions with undo where possible.
- Use clear, consistent copy through i18n; support right-to-left and longer translated text when locales require it.
- Persist the user's work across refresh where loss would hurt (drafts, long forms).
