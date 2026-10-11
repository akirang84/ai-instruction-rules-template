# Mobile: UX and Accessibility

## Platform Conventions

- Follow iOS Human Interface Guidelines and Android Material guidance for navigation, gestures, system back, and controls. Share logic, adapt interaction where conventions differ.
- Support dark mode, dynamic text sizes, and the system language and region. Keep touch targets at least 44x44 pt (iOS) / 48x48 dp (Android) with enough spacing.
- Give immediate feedback to every tap (pressed state, haptics where fitting). Keep actions reachable by thumb on large phones.
- Respect safe areas, keyboard avoidance, and interrupted states (calls, notifications, split screen).

## Accessibility

- Support VoiceOver and TalkBack: every interactive element has an accessible label, role, and state; reading order is logical; focus moves sensibly after navigation and modals.
- Support dynamic type scaling without clipped or overlapping content, sufficient contrast, reduced motion, and bold-text and inversion settings.
- Do not rely on color or gestures alone; offer an alternative to complex gestures.
- Test critical journeys with a screen reader on real devices of both platforms.

## Permissions and Onboarding

- Ask for a permission only when the feature needs it, with a short in-context explanation before the system prompt. The app must remain usable when permission is denied, and must guide the user to settings when needed.
- Keep first-run short. Defer account creation until value is shown when the product allows.

## States

- Every async screen defines loading, empty, error with retry, offline, and success states. Show clear, human error messages and keep user input on failure.
- Avoid blocking spinners for the whole screen when partial content can render. Confirm destructive actions and offer undo where possible.
