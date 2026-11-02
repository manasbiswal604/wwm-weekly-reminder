BUILD THE APK (on a PC with Node.js and Android Studio installed)

1. Open a terminal in this folder and run:
     npm install
     npx cap add android
     npx cap sync android
     npx cap open android
2. In Android Studio wait for Gradle to finish, then:
     Build > Build Bundle(s) / APK(s) > Build APK(s)
3. The APK is at android/app/build/outputs/apk/debug/app-debug.apk
   Copy it to your phone and install it (allow "install unknown apps").

Reminders: tap "Turn on reminders" in the app, allow notifications.
It schedules Monday, Thursday and Saturday at 09:00 even when the app is closed.

To change the page later, edit www/index.html and run: npx cap sync android

AUTOMATIC RELEASES (GitHub)
- Create a release with a new tag such as v1.6.0 (Releases > Draft a new release), or run the workflow manually.
  The workflow builds the APK and attaches WeeklyShops.apk to that release.
- You can also run "Build APK and Release" manually from the Actions tab.

SIGNING (so updates install over the old app)
1. In Termux: pkg install openjdk-17
   keytool -genkeypair -v -keystore release.jks -alias weeklyshops -keyalg RSA -keysize 2048 -validity 10000 -storetype PKCS12
   base64 -w0 release.jks
2. In the repo: Settings > Secrets and variables > Actions > New repository secret:
   KEYSTORE_BASE64   = the base64 output
   KEYSTORE_PASSWORD = the password you chose
   KEY_ALIAS         = weeklyshops
3. Keep a private backup of release.jks. If you lose it you cannot update the app.
Without these secrets the workflow still works and builds a debug APK.

NOTE: GitHub always lists "Source code (zip)" and "Source code (tar.gz)" on a release. Those are not the app.
The installable file is WeeklyShops-<tag>.apk, listed under Assets.

BEFORE YOU BUILD: open www/index.html, find the line starting with  var DEV=  and put your name and GitHub link there.
