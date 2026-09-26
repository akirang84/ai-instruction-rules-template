# Authentication and security

## Authentication baseline

- Use JWT access and refresh tokens through `@nestjs/passport`, unless the project has an existing approved identity provider or a confirmed alternative.
- Confirm token lifetime, refresh rotation/revocation strategy, delivery/storage mechanism per client platform, logout behavior, and account recovery requirements during project setup.
- Validate issuer, audience, expiry, and signature. Keep signing keys and secrets in deployment secret stores/environment configuration, never source control.
- Apply authorization on the server for every protected operation. Authentication alone does not establish resource ownership or permission.
- Do not log tokens, passwords, reset codes, secrets, or sensitive personal data. Redact credentials from errors and telemetry.

## Secure defaults

- Treat all client input and third-party responses as untrusted. Validate at boundaries and use parameterized ORM/query APIs.
- Apply least privilege to database users, service credentials, and role permissions. Separate staging and production secrets and data.
- Configure CORS, cookie flags (when cookies are used), transport security, rate limits for sensitive endpoints, and safe error responses according to deployment topology.
- Protect account enumeration, brute-force, replay, and token reuse risks where relevant. Store passwords using a current, dedicated password hashing function; never encrypt or store plaintext passwords.
- Do not commit `.env` files or real credentials. Keep `.env.example` limited to variable names and safe placeholders. Rotate secrets if they are exposed.
- Minimize collected personal data and define retention/deletion behavior appropriate to product requirements.
- For security-sensitive changes, state the threat addressed and include focused verification in the implementation plan.
