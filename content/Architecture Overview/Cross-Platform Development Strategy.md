# Cross-Platform Development Strategy

This document explains the cross-platform development strategy using Capacitor.

## Overview

The application uses Capacitor to deploy a unified React + TypeScript codebase to both web and Android platforms.

## Key Components

### Capacitor Configuration
- Defines application identifiers
- Specifies web build output directory
- Configures platform-specific settings

### Android Integration
- MainActivity extends Capacitor BridgeActivity
- AndroidManifest declares permissions and FileProvider
- Gradle build scripts manage dependencies

### Development Workflow
1. Develop with Vite dev server
2. Build web assets
3. Sync to Android with `npx cap sync`
4. Build Android app with Android Studio

## Best Practices
- Keep webDir in sync with Vite output
- Use lazy loading for routes
- Minimize plugin dependencies
