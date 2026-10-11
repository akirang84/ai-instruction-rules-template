# Observability and Operations

- Emit structured logs with correlation IDs. Record enough context to diagnose, never sensitive data.
- Track the golden signals per service: latency, traffic, errors, saturation. Add business metrics for critical flows (signup, payment, order).
- Add error tracking for backend and clients, tagged with release and environment, with source maps or symbol files uploaded.
- Alert on symptoms users feel (error rate, latency, failed jobs), each with an owner and an action. Remove alerts nobody acts on.
- State SLOs for critical paths once the product has real users, and use them to balance feature work against reliability work.
- Set timeouts, retries with backoff and jitter, and circuit breaking for outbound calls. Retry only idempotent operations.
- Background jobs are idempotent and observable, with dead-letter handling and a way to replay.
- Keep a short runbook per service: how to deploy, roll back, check health, rotate secrets, and restore data.
- Run a blameless post-incident review for production incidents and turn findings into tracked tasks and rule updates.
