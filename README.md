# AION MOBILE

Private fork workspace for the AionUi mobile companion. The iOS workflow builds the upstream mobile app source from `iOfficeAI/AionUi` and applies AION MOBILE-specific app identifiers at build time.

## iOS build setup

The workflow is in **Actions → AION MOBILE iOS IPA → Run workflow**.

Before the first build, configure:

1. **Settings → Secrets and variables → Actions → Secrets**
   - `EXPO_TOKEN`: an Expo access token for the Expo account that owns this app's EAS project.
2. **Settings → Secrets and variables → Actions → Variables**
   - `EXPO_PROJECT_ID`: the EAS project ID created under your Expo account for this app.

The first successful internal iOS build also needs valid Apple Developer signing credentials configured for that EAS project. EAS may require registering the target iPhone's UDID for an ad hoc/internal install. No Apple credentials, certificates, passwords, or private keys belong in this public repository.

The workflow uses the upstream app's mobile directory and packages the shared `src/common` utilities into the mobile build workspace. It uses bundle identifier `com.moha700m.aionmobile`, builds an internal-distribution IPA, and does **not** submit to TestFlight or the App Store.

## Important

- This repository is currently public. Do not commit API keys, Expo tokens, Apple credentials, provisioning profiles, or private signing keys.
- The mobile client is a companion app: it connects to an AionUi server. It does not run the desktop Electron backend on iPhone.
- Upstream source: https://github.com/iOfficeAI/AionUi
