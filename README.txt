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
