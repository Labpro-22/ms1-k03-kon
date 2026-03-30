# Nimons360
## Prerequisites

Before writing code, ensure your local environment is set up for CLI Android development:

1. **Android SDK:** You must have API Level 35 installed.
2. **Java JDK:** JDK 17 or higher is required.
3. **VSCode Extensions:**
    - `Kotlin` (fwcd) - For language server support.
    - `XML` (Red Hat) - For layout formatting.
4. **Android Device/Emulator:** Must have USB Debugging enabled or Android Studio emulator

## Project Structure

All code lives inside the `com.kon.nimons360` package.

app/
├── build.gradle.kts           # Module-level build config
├── src/main/
│   ├── AndroidManifest.xml    # App entry points and permissions
│   ├── java/com/kon/nimons360/
│   │   ├── MainActivity.kt    # Kotlin UI Controllers
│   │   └── ui/                # Jetpack Compose functions
│   └── res/
│       ├── layout/            # XML View layouts
│       └── values/            # Themes, strings, and colors
gradle/
└── libs.versions.toml         # SINGLE SOURCE OF TRUTH for dependency versions

## Terminal Cheatsheet

### Compile & Build

```bash
# Clean the project (run this if dependencies change or things act weird)
./gradlew clean

# Build the Debug APK
./gradlew assembleDebug

# Build the APK
./gradlew build
```

### Clean

```bash
# 1. Kill any hidden Gradle background processes
./gradlew --stop

# 2. Clean the project and force Gradle to redownload/re-verify dependencies
./gradlew clean assembleDebug --refresh-dependencies
```

### Deploy & Run with ADB

```bash
# 1. Install the newly compiled APK
adb install -r app/build/outputs/apk/debug/app-debug.apk

# 2. Launch the app instantly
adb shell am start -n "com.kon.nimons360/.MainActivity"

# 3. View the live crash logs/console output
adb logcat | grep "com.kon.nimons360"
```


