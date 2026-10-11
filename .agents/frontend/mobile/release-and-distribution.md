# Mobile: Release and Distribution

Extends `devops/ci-cd-and-release.md`.

- Build with EAS (or the project's chosen build service) using named profiles: development, preview/staging, production. Builds are reproducible from the repository and lockfile in CI, never from a developer machine.
- Manage signing credentials (certificates, provisioning profiles, keystores) in the build service or a secret store with documented ownership and backup. Losing the Android upload/app signing key or iOS certificates must never block a release.
- Auto-increment build numbers, follow semantic versioning for the app version, and tag each release in Git.
- Distribute through internal channels first (TestFlight, Play internal/closed tracks), then staged rollout (phased release on iOS, percentage rollout on Android). Halt a rollout on regression.
- A store release cannot be recalled instantly. Use feature flags and remote config to disable risky features, and keep the API backward compatible with all supported app versions.
- Use OTA updates (EAS Update) only for JavaScript and asset changes that are compatible with the installed native runtime. Tie updates to a runtime version, use channels per environment, test them on a preview channel, and know how to roll back. Native changes require a store build. OTA must not violate store policy.
- Plan for store review time: prepare metadata, screenshots, privacy declarations, review notes, and test accounts before submission, and do not make a release plan that assumes same-day approval.
- Monitor after release: crash-free sessions and users, ANRs, startup time, and key funnels, by app version. Upload symbols and source maps for every build so crashes are readable.
- Maintain a device and OS test matrix, and run E2E on real devices or a device farm for critical journeys before release.
- Keep a documented process for expired certificates, rejected submissions, and emergency hotfixes.
