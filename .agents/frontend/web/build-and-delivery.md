# Web: Build and Delivery

Extends `devops/`.

- Builds are deterministic from the lockfile with pinned runtime versions. Public build-time variables are separated from secrets; anything in the bundle is public.
- Emit content-hashed asset filenames. Serve assets from a CDN with compression (Brotli/gzip) and HTTP/2 or HTTP/3.
- Every PR gets a preview deployment for review and E2E checks. Production deploys promote a tested build, not a rebuild.
- Version the web client against the API. Support the previous API version during rollout, or deploy backward-compatible APIs first. Handle a stale client by detecting version mismatch and prompting reload.
- Use feature flags for risky changes and staged rollouts. Keep a one-step rollback to the previous deployment.
- Upload source maps to the error tracker, not to the public CDN, unless intended.
- Monitor in production: real-user Core Web Vitals, JavaScript errors, failed API calls, and key business funnels. Alert on regressions after each release.
- Run smoke tests after deploy on the real domain, covering load, login, and one critical journey.
- Control domains, DNS, TLS certificates, and redirects as managed configuration with documented ownership and renewal.
