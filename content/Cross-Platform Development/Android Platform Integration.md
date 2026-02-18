# Android Platform Integration

This document describes the Android platform integration using Capacitor.

## Project Structure

```
android/
├── app/
│   ├── src/main/
│   │   ├── java/com/example/expensetracker/
│   │   │   └── MainActivity.java
│   │   ├── res/
│   │   │   ├── values/
│   │   │   │   ├── strings.xml
│   │   │   │   └── styles.xml
│   │   │   └── xml/file_paths.xml
│   │   └── AndroidManifest.xml
│   └── build.gradle
├── build.gradle
└── gradle.properties
```

## MainActivity

The MainActivity extends Capacitor's BridgeActivity:

```java
public class MainActivity extends BridgeActivity {}
```

This minimal setup provides:
- WebView initialization
- Plugin bridge
- Lifecycle management

## AndroidManifest.xml

Key configurations:
- MainActivity with LAUNCHER intent
- FileProvider for secure file sharing
- Internet permission

## Build Configuration

### app/build.gradle
- Capacitor dependencies
- Cordova plugins
- Min SDK: 22
- Target SDK: 34

### gradle.properties
- AndroidX enabled
- JVM settings

## Building the App

### Debug Build
```bash
cd android
./gradlew assembleDebug
```

### Release Build
```bash
cd android
./gradlew assembleRelease
```

### App Bundle
```bash
cd android
./gradlew bundleRelease
```

## Testing

- Android Emulator
- Physical device via USB
- Chrome DevTools for WebView debugging
