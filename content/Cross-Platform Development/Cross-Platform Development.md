# Cross-Platform Development

This document provides an overview of the cross-platform development approach using Capacitor.

## Overview

The Expense Tracker is built as a web application that can be deployed to multiple platforms:
- Web (via browser)
- Android (via Capacitor)
- iOS (potential future support)

## Technology Stack

- **Capacitor 7.0**: Cross-platform runtime
- **Android Studio**: Android development environment
- **Gradle**: Android build system
- **WebView**: Native app container

## Development Workflow

1. **Web Development**
   - Develop with Vite dev server
   - Use React components and hooks
   - Test in browser

2. **Android Integration**
   - Run `npx cap sync android`
   - Open Android Studio
   - Build and test on device/emulator

3. **Deployment**
   - Build web assets
   - Sync to Android
   - Generate APK or App Bundle

## Platform-Specific Considerations

### Web
- LocalStorage for persistence
- Browser APIs available
- Responsive design

### Android
- WebView rendering
- Native file system access
- Hardware back button support
- Status bar theming

See the detailed documentation for specific topics:
- [Android Platform Integration](Android%20Platform%20Integration.md)
- [Capacitor Configuration](Capacitor%20Configuration.md)
- [Platform Compatibility](Platform%20Compatibility.md)
- [Web Deployment](Web%20Deployment.md)
