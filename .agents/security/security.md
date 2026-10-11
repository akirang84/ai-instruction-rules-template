# Authentication and Security

Applies to every platform and tier. Web and mobile specs add platform detail on top of this file.

## Authentication

- Use JWT access and refresh tokens through `@nestjs/passport`, unless the project has an approved identity provider or a confirmed alternative.
- Confirm token lifetime, refresh rotation and revocation, per-client storage and delivery, logout behavior, and account recovery during project setup.
- Validate issuer, audience, expiry, and signature. Keep signing keys in the deployment secret store, never in source control.
- Authentication does not establish permission. Enforce authorization on the server for every protected operation and check resource ownership.
- Store passwords only with a current dedicated password hashing function. Never store or log plaintext passwords.

## Secure Defaults

- Treat all client input and third-party responses as untrusted. Validate at boundaries and use parameterized queries.
- Apply least privilege to database users, service credentials, and roles. Separate staging and production secrets and data.
- Configure CORS, cookie flags, transport security, rate limits for sensitive endpoints, and safe error responses for the deployment topology.
- Defend against account enumeration, brute force, replay, and token reuse where relevant.
- Never commit `.env` files or real credentials. `.env.example` has names and safe placeholders only. Rotate any exposed secret.
- Never log tokens, passwords, reset codes, secrets, or sensitive personal data. Redact them from errors and telemetry.
- Minimize collected personal data and define retention and deletion behavior.

## Supply Chain and Operations

- Pin dependencies through a lockfile, review new dependencies for maintenance and license, and run vulnerability audits in CI.
- Run secret scanning in CI and pre-commit where available.
- Keep an audit trail for security-sensitive actions (login, permission change, data export, deletion).
- For security-sensitive changes, state the threat addressed and include focused verification (negative and authorization tests) in the plan.
