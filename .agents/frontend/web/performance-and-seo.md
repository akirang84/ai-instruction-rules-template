# Web: Performance and SEO

## Performance

- Set budgets and enforce them in CI: Core Web Vitals targets (LCP, INP, CLS), JavaScript bundle size per route, and image weight. Measure on a mid-range device with a throttled network, not only on a developer machine.
- Ship less JavaScript: analyze bundles, remove unused dependencies, avoid heavy libraries for small tasks, and tree-shake.
- Optimize the critical rendering path: inline only critical CSS, defer non-critical scripts, preload the LCP resource, and avoid render-blocking requests.
- Images: responsive sizes, modern formats, explicit width and height (no layout shift), lazy loading below the fold, and a CDN.
- Fonts: subset, preload the critical weight, and use `font-display` to avoid invisible text.
- Prevent layout shift: reserve space for async content, ads, and embeds.
- Keep the main thread free: move heavy work to workers or defer it, virtualize long lists, and debounce expensive handlers.
- Measure real users (field data) as well as lab tests, and treat regressions as defects.

## SEO

- Public pages need unique `<title>`, meta description, canonical URL, semantic headings, and Open Graph and social metadata.
- Render SEO-critical content on the server or at build time so crawlers see it without running JavaScript.
- Provide `robots.txt`, a sitemap, correct status codes (404, 301/308 for moves), and structured data where it applies.
- Private and authenticated pages are `noindex`.
- Use meaningful, stable URLs. Redirect old URLs when routes change.
