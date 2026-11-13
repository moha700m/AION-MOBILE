# AION MOBILE

Bootstrap repository for the AionUi iOS companion build. The GitHub Actions workflow checks out the upstream mobile source at build time and applies AION MOBILE-specific identifiers before building.

## One-time setup required for a signed iPhone IPA

The workflow is ready, but a signed iOS IPA cannot be produced until the app has its own Expo/EAS project and Apple signing credentials.

1. Create an Expo account/project for this app at https://expo.dev/ (do not use the upstream maintainer's project).
2. Create an Expo access token at https://expo.dev/accounts/[your-account]/settings/access-tokens.
3. In this repository, open **Settings → Secrets and variables → Actions**:
   - Add secret `EXPO_TOKEN` with the Expo access token.
   - Add variable `EXPO_PROJECT_ID` with this app's EAS project UUID.
4. Configure iOS signing credentials for that EAS project. For direct installation on your iPhone, an Apple Developer membership and an ad hoc provisioning profile containing your iPhone's registered UDID are normally required.

Then run **Actions → AION MOBILE iOS IPA → Run workflow**. The build is internal-distribution only; it does not submit to TestFlight or the App Store.

## What the workflow does

- Checks out `iOfficeAI/AionUi` at build time.
- Packages the shared `src/common` utilities used by the mobile app.
- Uses bundle identifier `com.moha700m.aionmobile` and your EAS project ID.
- Builds the iOS IPA using EAS Build and waits for the result.

## Important

- This repository is public. Never commit API keys, Expo tokens, Apple credentials, provisioning profiles, or private signing keys.
- The mobile app is a companion client that connects to an AionUi server. It does not run the desktop Electron backend on iPhone.
- This repository currently contains the build workflow and setup documentation, not a full mirrored copy of upstream source. The workflow fetches upstream source when it runs.
- Upstream source: https://github.com/iOfficeAI/AionUi
