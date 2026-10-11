# Mobile: Security and Privacy

Extends `security/security.md`.

## On-Device

- The device and the app binary are untrusted. Never ship secrets, API keys with write power, or private keys in the bundle. Treat anything inside the app as extractable.
- Store tokens and secrets only in the platform secure store (Keychain on iOS, Keystore-backed storage on Android) via `expo-secure-store` or equivalent. Never use plain AsyncStorage or the file system for credentials.
- Keep sensitive data out of screenshots, the app-switcher snapshot, clipboard, logs, and backups when the data is sensitive. Exclude sensitive files from device backup.
- Offer biometric or device-credential unlock for sensitive apps, as a local convenience that gates access to a stored token, not as a replacement for server authentication.
- Use short-lived access tokens with refresh rotation and server-side revocation. Handle token expiry and forced logout cleanly.

## Network

- Use HTTPS only (App Transport Security / cleartext disabled). Consider certificate pinning for high-risk apps, with a rotation and backup-pin plan so a pin change cannot brick the app.
- Validate deep link and push payload inputs as untrusted. Use verified app/universal links, and never act on a link without checking state and authorization.
- Server-side authorization is the only real control; client checks (root/jailbreak detection, obfuscation) are only defense in depth.
- Attest the app and device (Play Integrity, App Attest) for high-risk operations when abuse is a concern.

## Privacy and Stores

- Declare data collection accurately in App Store privacy labels and Google Play data safety, and keep them in sync with the SDKs in use. Review each SDK for data collection before adding it.
- Request the minimum permissions and provide the required usage descriptions. Use App Tracking Transparency and consent flows where required.
- Provide in-app account deletion and data export where the stores and regulations require it.
- Keep personal data out of analytics events, crash reports, and logs.
