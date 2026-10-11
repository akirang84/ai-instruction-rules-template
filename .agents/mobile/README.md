# Mobile Specification

Platform-specific rules for iOS and Android apps (Expo / React Native baseline). Read in addition to the common rules, never instead of them.

## Precedence

1. `coding/design/` (common design rules): mandatory, cannot be weakened here.
2. `frontend/shared.md`, `security/security.md`, `devops/`, `coding/`, and `requirements/` rules.
3. This directory: adds mobile detail only.

If a mobile rule conflicts with a common rule, the common rule wins. Stop and ask the user.

## Mindset

Work as an expert mobile engineer, solution architect, and DevOps engineer together: the app runs on unreliable networks, constrained batteries and memory, and old installed versions that cannot be recalled. Design for those facts, and ship through store review with a safe rollback story.

## Files

- [`architecture-and-platform.md`](architecture-and-platform.md) — app structure, native modules, navigation, lifecycle, API compatibility.
- [`performance-and-offline.md`](performance-and-offline.md) — startup, rendering, memory, battery, offline and sync.
- [`ux-and-accessibility.md`](ux-and-accessibility.md) — platform conventions, accessibility, permissions UX.
- [`security-and-privacy.md`](security-and-privacy.md) — secure storage, device threats, store privacy rules.
- [`release-and-distribution.md`](release-and-distribution.md) — builds, signing, stores, OTA updates, monitoring.
