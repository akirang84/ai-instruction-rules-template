# Stack: React Native + Expo

Active when `project.md` lists `react-native-expo`. Extends `frontend/shared.md`, `frontend/mobile/`, and `frontend/web/` (when the app also ships to browsers). Never weakens them.

## Stack

- React Native + Expo, Expo Router for navigation, React Native Web for browser builds. Confirm any departure from this baseline.
- UI library from `project.md` (default suggestion: Tamagui) for shared primitives and styling.
- Use the Hermes engine.

## Structure

- Reusable behavior lives in hooks, services, and domain modules; screens compose and navigate.
- Keep platform-specific behavior explicit through platform files (`.web.tsx`, `.native.tsx`, `.ios.tsx`, `.android.tsx`) or small adapters. Verify shared code on iOS, Android, and web.
- Use Expo Router typed routes.

## Native and Build

- Prefer the Expo managed workflow with config plugins. Use a development build (not Expo Go) once native modules are involved. Adding a native module or ejecting is an architecture decision: state the reason and the maintenance cost, and confirm.
- Build with EAS using named profiles: development, preview/staging, production. Keep per-environment config (bundle identifier, API URL, feature flags) in build profiles and `app.config.ts`, never edited by hand before a build.
- OTA updates use EAS Update, tied to a runtime version, with one channel per environment. Follow the OTA limits in `frontend/mobile/release-and-distribution.md`.
- Plan Expo SDK and React Native upgrades as scheduled work, not emergency work.

## Storage

- Credentials and tokens only in `expo-secure-store`. Never in AsyncStorage or plain files.

## Testing

- Unit and component tests with Jest and React Native Testing Library. Mobile E2E with the tool confirmed in `project.md` (for example Maestro or Detox); web E2E with Playwright.
