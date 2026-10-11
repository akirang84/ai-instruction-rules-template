# Scalability

- State the expected volume (data size, concurrency, request rate, growth) before designing; design for that plus a reasonable margin, not for unlimited scale.
- Bound every list, query, payload, and queue: use pagination, limits, streaming, or batching.
- Keep request handling stateless where possible; place state in explicit stores so instances can be added.
- Make operations idempotent and safe to retry; define timeouts, backpressure, and failure behavior for slow or unavailable dependencies.
- Choose data access patterns deliberately: indexes for known queries, no N+1 access, no unbounded scans on hot paths.
- Move slow or heavy work off the request path (jobs, queues) when it can exceed user-facing latency budgets.
- Add observability (logs, metrics, tracing) for the paths that must scale. Do not optimize without measurement.
