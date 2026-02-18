# Capacitor Configuration

This document describes the Capacitor configuration.

## Configuration File

`capacitor.config.ts`:

```typescript
import type { CapacitorConfig } from '@capacitor/cli';

const config: CapacitorConfig = {
  appId: 'com.example.expensetracker',
  appName: 'Expense Tracker',
  webDir: 'dist',
  server: {
    androidScheme: 'https'
  }
};

export default config;
```

## Configuration Options

### appId
- Unique application identifier
- Reverse domain notation
- Used for Android package name

### appName
- Display name for the app
- Shown on device home screen

### webDir
- Directory containing web assets
- Must match Vite build output
- Default: 'dist'

### server.androidScheme
- URL scheme for Android
- 'https' recommended for security

## CLI Commands

### Add Platform
```bash
npx cap add android
```

### Sync Web Assets
```bash
npx cap sync android
```

### Open in IDE
```bash
npx cap open android
```

### Copy Web Assets (without sync)
```bash
npx cap copy android
```

## Live Reload

For development with live reload:
```bash
npm run dev
# In another terminal
npx cap run android --livereload --external
```
