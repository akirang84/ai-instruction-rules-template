# Mobile: Performance and Offline

## Performance

- Set budgets: cold start time, time to interactive, JS bundle size, app binary size, frame rate (60 fps; no sustained dropped frames), and memory. Measure on low-end physical devices and in release builds, never only in development mode on a simulator.
- Use the Hermes engine and keep the startup path minimal: lazy-load screens and heavy modules, defer non-critical initialization, and keep the splash screen until the first useful render.
- Use virtualized lists with stable keys and memoized items for long lists. Avoid heavy work on the JS thread during interactions; move animations to the native driver or Reanimated worklets.
- Optimize images: right-sized assets, caching, and modern formats. Avoid decoding large images on the UI path.
- Control memory: release listeners, subscriptions, and timers; avoid retaining large objects across screens.
- Respect battery and data: batch network calls, avoid polling, limit background work and location precision/frequency to what the feature needs.
- Profile before optimizing, and treat measured regressions as defects.

## Offline and Sync

- Decide per feature whether it is online-only, read-offline, or fully offline-capable, and state it in the requirements. Do not retrofit offline.
- Detect connectivity changes and degrade gracefully: queue writes, show state clearly, and never lose user input.
- Local persistence is a cache or a source of truth by explicit decision. Version the local schema and migrate it between app versions.
- Sync must be idempotent and resumable, with conflict rules defined (last-write-wins, merge, or user choice) and tested. Use client-generated IDs and server timestamps in UTC.
- Retry with exponential backoff and jitter. Bound the queue size and expire stale operations.
- Clear local data on logout and account deletion.
