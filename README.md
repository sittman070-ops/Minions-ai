# Minion AI — Android wrapper

This Android project packages the currently deployed Minion AI web app in a native Android WebView shell.

## Build an APK using GitHub Actions (no local Android SDK required)

1. Create a new **private** repository on GitHub.
2. Upload the contents of this ZIP into the repository (the `.github` folder must be included).
3. Open the repository's **Actions** tab.
4. Select **Build Minion APK** and choose **Run workflow** (or push to `main`).
5. Wait for the workflow to finish successfully.
6. Open the completed workflow run, scroll to **Artifacts**, and download **Minion-debug-apk**.
7. Extract the ZIP artifact; it contains `app-debug.apk`. Transfer it to your Android phone and open it to install. You may need to allow installs from that file manager.

## Important limitations

- This is a **debug APK for personal testing**, not a Play Store-ready signed release.
- The app loads the hosted Minion website, so it needs an internet connection and the website/backend must remain available.
- This does not add always-on wake-word listening, system-wide Circle to Search, unrestricted device control, or video generation. Those require separate native implementations and permissions.
- Android and browser permissions still apply. The wrapper does not silently control the phone.
- Before Play Store release, create a signed Android App Bundle (`.aab`), configure privacy disclosures and data safety, test on real devices, and review Play policies.
- Change the application ID in `app/build.gradle` and package path if you later want a permanent production identity.

## Local build

Install JDK 17, Android SDK platform 35, and Gradle 8.9, then run:

```bash
gradle assembleDebug
```

The APK will be at `app/build/outputs/apk/debug/app-debug.apk`.
