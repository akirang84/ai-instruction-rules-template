# Web: Security and Privacy

Extends `security/security.md`.

## Browser Surface

- Set a strict Content-Security-Policy and tighten it over time (no `unsafe-inline` or `unsafe-eval` unless justified). Also set HSTS, `X-Content-Type-Options`, a Referrer-Policy, a Permissions-Policy, and frame protection (`frame-ancestors`).
- Prevent XSS: rely on framework escaping, never inject untrusted HTML; sanitize with a vetted library when rich text is required; avoid `dangerouslySetInnerHTML` and `eval`.
- Prevent CSRF for cookie-based auth with SameSite cookies plus CSRF tokens or origin checks on state-changing requests.
- Configure CORS with explicit origins. Never reflect arbitrary origins or combine wildcard origins with credentials.
- Use Subresource Integrity or self-host for third-party scripts. Review each third-party script for data exposure.
- Validate redirect targets and URLs from input (open redirect, `javascript:` URLs). Use `rel="noopener noreferrer"` for external links.

## Authentication in the Browser

- Prefer short-lived access tokens in memory and refresh tokens in `HttpOnly`, `Secure`, `SameSite` cookies. Do not keep tokens in `localStorage` or `sessionStorage`.
- Make logout clear client state and revoke server-side sessions. Handle expired sessions with a clean re-authentication flow that preserves intended navigation.
- Protect sensitive screens from caching and from back-button exposure after logout.

## Privacy

- Collect only needed data. Obtain consent before non-essential cookies, analytics, and tracking, and honor regional rules (GDPR, CCPA) that apply to the audience.
- Keep personal data out of URLs, logs, analytics events, and error reports.
- Provide ways to export and delete user data when the product requires it.
