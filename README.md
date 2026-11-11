# ADANCRAFT for Android

A friendly 3D building adventure. This folder is a complete Android app project
(Capacitor wraps the game in a full-screen WebView). The game itself is `www/index.html`.
It works offline: three.js is bundled, and worlds are saved on the phone.

## Option A: get the APK with no installs (GitHub, about 5 minutes)
1. Create a free account at github.com and make a **new repository** (private is fine).
2. Upload everything in this folder to it (drag the files into the repo page, or use git).
   Make sure the hidden `.github` folder is included.
3. Open the repo's **Actions** tab, choose **Build Android APK**, and press **Run workflow**
   (it also runs on every push).
4. When it finishes (a few minutes), open the run and download the **ADANCRAFT-apk** artifact.
   Unzip it to get `app-debug.apk`.
5. Copy the APK to your phone and open it. Android will ask you to allow installs from
   this source ("Install unknown apps"). Accept, then install.

## Option B: build on your computer
Needs Node 18+, JDK 17 and Android Studio (or the Android SDK).
```
npm install
npx cap sync android
cd android
./gradlew assembleDebug        # Windows: gradlew.bat assembleDebug
```
The APK is at `android/app/build/outputs/apk/debug/app-debug.apk`.
Or run `npx cap open android` and press Run in Android Studio with your phone plugged in.

## Option C: install as a web app (no APK)
Host the `www` folder on any HTTPS site (for example GitHub Pages). Open it in Chrome on
the phone and choose **Install app** / **Add to Home screen**. It runs full-screen and offline.

## Notes
- The debug APK is signed with a debug key. It installs fine on your own devices.
  For Google Play you need a release build signed with your own key (Android Studio:
  Build > Generate Signed Bundle / APK).
- App id: `com.adancraft.game` (change it in `capacitor.config.json` and
  `android/app/build.gradle` before publishing).
- The game runs in landscape. Works best on phones from about 2019 onward.
  In Settings (O) lower Graphics quality if it feels slow.
- Updating the game: replace `www/index.html`, then run `npx cap sync android` and rebuild.
