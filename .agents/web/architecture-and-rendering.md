# Web: Architecture and Rendering

- Choose the rendering model per route and record the reason: static (SSG) for content that rarely changes, server rendering (SSR) for personalized or SEO-critical pages, client rendering for authenticated app screens. Do not default one model to the whole app.
- Keep the URL as the source of truth for navigable state (filters, tabs, pagination, selected item). Pages must work with deep links, refresh, and the back button.
- Separate server state (fetched, cached, revalidated) from UI state. Define cache keys, staleness, invalidation after mutations, and retry policy deliberately.
- Define the HTTP caching strategy: immutable hashed assets with long cache lifetimes, short or revalidated HTML, and explicit `Cache-Control` for API responses that may be cached.
- Make routes code-split by default. Load heavy features (editors, charts, maps) lazily.
- Handle the full network lifecycle: slow, offline, failed, partial, and retried requests; cancel in-flight requests on navigation; avoid duplicate requests.
- Provide error boundaries per route and a not-found route. A failed widget must not blank the page.
- Guard routes by authentication state on the client for UX only; the server enforces access.
- Isolate browser-only APIs (`window`, `localStorage`, `navigator`) behind adapters so server rendering and tests do not break.
- Treat third-party scripts as dependencies with cost: justify each, load asynchronously, and isolate failures.
