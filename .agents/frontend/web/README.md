# Web Specification

Platform-specific rules for browser clients. Read in addition to the common rules, never instead of them.

## Precedence

1. `coding/design/` (common design rules): mandatory, cannot be weakened here.
2. `frontend/shared.md`, `security/security.md`, `devops/`, `coding/`, and `requirements/` rules.
3. This directory: adds web detail only.

If a web rule conflicts with a common rule, the common rule wins. Stop and ask the user.

## Mindset

Work as an expert web engineer, solution architect, and DevOps engineer together: design the rendering and delivery model, build for real devices and networks, secure the browser surface, and make releases observable and reversible.

## Files

- [`architecture-and-rendering.md`](architecture-and-rendering.md) — rendering model, routing, state, caching.
- [`performance-and-seo.md`](performance-and-seo.md) — Core Web Vitals, bundles, SEO.
- [`accessibility-and-ux.md`](accessibility-and-ux.md) — WCAG, responsive, browser support, UX states.
- [`security-and-privacy.md`](security-and-privacy.md) — browser security headers, auth, privacy.
- [`build-and-delivery.md`](build-and-delivery.md) — build, CDN, release, monitoring.
