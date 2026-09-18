# Klotski — Android project

Your `klotski.html` game wrapped in a native Android WebView app. The game runs fully
offline from `app/src/main/assets/`. Launcher icons were generated from `klotski.jpg`.

- Package: `com.klotski.game`
- App name: Klotski
- minSdk 21 (Android 5.0) / targetSdk 34
- Portrait, no action bar, localStorage enabled so saves and best times persist

## Option A — Build in the cloud (no installs)

1. Create a new **GitHub** repository and upload this whole folder to it.
2. Go to the **Actions** tab → *Build Klotski APK* → **Run workflow**
   (it also runs automatically on every push to `main`).
3. When it finishes, download the **klotski-debug-apk** artifact. Inside is `app-debug.apk`.
4. Copy it to your phone, open it, and allow "Install unknown apps" when prompted.

## Option B — Build locally with Android Studio

1. Install [Android Studio](https://developer.android.com/studio).
2. **File → Open** → select this `KlotskiApp` folder. Let it sync (it downloads Gradle
   and the SDK automatically the first time).
3. **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
4. The APK lands in `app/build/outputs/apk/debug/app-debug.apk`.

## Option C — Command line

Requires JDK 17 and the Android SDK (`ANDROID_HOME` set):

```bash
gradle assembleDebug        # or ./gradlew assembleDebug once a wrapper is generated
```

## Making a release APK for the Play Store

1. In Android Studio: **Build → Generate Signed Bundle / APK**, create a keystore, keep it safe.
2. Play Store submissions require an **AAB**, not an APK — choose *Android App Bundle*.
3. Bump `versionCode` / `versionName` in `app/build.gradle` for each update.

## Updating the game later

Replace `app/src/main/assets/index.html` with your newer HTML and rebuild. No Java changes needed.
