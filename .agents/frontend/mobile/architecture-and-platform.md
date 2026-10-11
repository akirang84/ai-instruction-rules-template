# Mobile: Architecture and Platform

- Prefer Expo managed workflow with config plugins. Use a development build (not Expo Go) once native modules are involved. Adding a native module or ejecting is an architecture decision: state the reason and the maintenance cost, and confirm.
- Isolate native and platform APIs (camera, notifications, biometrics, file system, location) behind small adapters so screens and domain code stay platform-free and testable.
- Treat every installed app version as a client that lives for months. The API must stay backward compatible with all supported app versions. Define a minimum supported version, and provide a forced-upgrade path for dropped versions.
- Handle the full app lifecycle: cold start, background, foreground, process death and restore, low memory, and interrupted flows. Persist critical in-progress state.
- Deep links and universal/app links are contracts: define, validate, and test them, including handling when the app is not installed or the user is logged out.
- Push notifications: define the payload contract, handle permission denial, token rotation, and tapping a notification in each app state. Never put sensitive data in a payload.
- Navigation: use Expo Router with typed routes, handle back behavior on Android, and guard routes for UX while the server enforces access.
- Design for different screen sizes, tablets and foldables, orientation, and safe areas (notch, home indicator, system bars).
- Keep configuration per environment (bundle identifier, API URL, feature flags) through build profiles, never edited by hand before a build.
- Track the minimum OS versions and SDK versions deliberately. Plan Expo SDK and React Native upgrades as scheduled work, not emergency work.
