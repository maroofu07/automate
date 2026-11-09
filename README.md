# LocationReply - Android SMS Location Auto-Responder

An automated Android application that continuously monitors for incoming SMS triggers (e.g. `#LOCATE` or `locate`) and automatically replies with current high-precision GPS coordinates, a direct Google Maps link, and device battery statistics. Works 100% offline using hardware GPS satellites even if mobile data is turned off.

---

## ⚠️ Important Installation Guide (Play Protect & Android 13/14)

### 1. Why Google Play Protect warns during installation:
Google Play Protect scans all apps installed from outside the Play Store. Because this application requests `RECEIVE_SMS` and `SEND_SMS` permissions (strictly required to read incoming triggers and reply with location), Play Protect flags it as an "Unrecognized developer" app.
- **To install:** Tap **"More details"** -> Tap **"Install anyway"**.
- This is your own private, open-source build for personal anti-theft protection.

### 2. Android 13 & 14 "Restricted Settings" (Fixing greyed-out permissions):
On Android 13+, sideloaded APKs are restricted by default until approved:
1. Open phone **Settings > Apps > LocationReply**.
2. Tap the **3 DOTS (⋮)** in the top right corner.
3. Tap **"Allow restricted settings"** and verify with your fingerprint/PIN.
4. Now open **LocationReply** and tap **"Grant SMS"** & **"Grant GPS"**.

### 3. Background Autostart (Xiaomi / Redmi / Poco / Vivo / Oppo / Realme / Samsung):
In India, OEM power managers can sleep background apps. To guarantee 24/7 readiness:
1. In App Info, enable **"Autostart"** or **"Background startup"**.
2. Go to **Battery** and select **"Unrestricted"** (or "No restrictions").

---

## 🚀 How to Build the APK File

### Method 1: Automated Free Cloud Build (GitHub Actions)
1. Download the project **ZIP** from the exporter.
2. Push or upload the folder to your GitHub repository.
3. The included `.github/workflows/build-apk.yml` will compile the APK in ~2 minutes.
4. Go to the **Actions** tab on GitHub -> Click the latest build -> Download **location-reply-debug-apk**!

### Method 2: Android Studio (Mac / Windows / Linux)
1. Open **Android Studio** -> Select **File > Open** -> Select this extracted folder.
2. Go to top menu: **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
3. In the notification, click **locate** to find `app-debug.apk`.

### Method 3: Command Line (Linux / macOS)
```bash
chmod +x ./gradlew
./gradlew assembleDebug
```

### Method 4: Command Line (Windows PowerShell / CMD)
```cmd
gradlew.bat assembleDebug
```
The APK will be at:
`app/build/outputs/apk/debug/app-debug.apk`

---

## 🛠️ Gradle Wrapper & Compatibility Matrix
- **Gradle Version**: 8.9 (distribution: `gradle-8.9-bin.zip`)
- **Android Gradle Plugin (AGP)**: 8.7.2
- **Kotlin**: 2.0.21 (Compose Compiler 2.0.21)
- **JDK Compatibility**: Java 17 (Temurin recommended)
- **Wrapper Files Included**: `gradlew`, `gradlew.bat`, `gradle/wrapper/gradle-wrapper.jar` (genuine binary, SHA-256: `498495120a03b9a6ab5d155f5de3c8f0d986a449153702fb80fc80e134484f17`), and `gradle-wrapper.properties`. No separate Gradle installation or manual wrapper generation required!

---

## 🔒 Configuration Summary
- **Trigger Keyword**: `#LOCATE` (matches with or without '#' prefix)
- **Whitelist Security**: Disabled (responds to any sender with the secret keyword)
- **Template**: `My current location: {maps_url}`
