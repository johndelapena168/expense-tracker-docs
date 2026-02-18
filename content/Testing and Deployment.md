# Testing and Deployment

<cite>
**Referenced Files in This Document**
- [package.json](file://package.json)
- [capacitor.config.ts](file://capacitor.config.ts)
- [android/app/build.gradle](file://android/app/build.gradle)
- [vite.config.ts](file://vite.config.ts)
</cite>

## Table of Contents
1. [Introduction](#introduction)
2. [Testing Strategy](#testing-strategy)
3. [Unit Testing](#unit-testing)
4. [Component Testing](#component-testing)
5. [Integration Testing](#integration-testing)
6. [Web Deployment](#web-deployment)
7. [Android Deployment](#android-deployment)
8. [CI/CD Pipeline](#cicd-pipeline)

## Introduction
This document outlines the testing and deployment procedures for the Expense Tracker application. It covers testing strategies for both web and mobile platforms, as well as deployment processes for production releases.

## Testing Strategy

### Testing Pyramid
1. **Unit Tests**: Test individual functions and utilities
2. **Component Tests**: Test React components in isolation
3. **Integration Tests**: Test component interactions
4. **E2E Tests**: Test complete user flows

### Test File Organization
```
src/
├── __tests__/
│   ├── unit/
│   ├── components/
│   └── integration/
├── components/
│   └── BottomNav.test.tsx
└── contexts/
    └── AppContext.test.tsx
```

## Unit Testing

### Testing Utilities
```bash
npm install --save-dev vitest @testing-library/react @testing-library/jest-dom
```

### Example Unit Test
```typescript
// utils/formatCurrency.test.ts
import { describe, it, expect } from 'vitest';
import { formatCurrency } from './formatCurrency';

describe('formatCurrency', () => {
  it('formats USD correctly', () => {
    expect(formatCurrency(100, 'USD')).toBe('$100.00');
  });
  
  it('formats PHP correctly', () => {
    expect(formatCurrency(100, 'PHP')).toBe('₱100.00');
  });
});
```

### Running Unit Tests
```bash
npm run test:unit
```

## Component Testing

### Testing React Components
```typescript
// BottomNav.test.tsx
import { render, screen } from '@testing-library/react';
import { BrowserRouter } from 'react-router-dom';
import { BottomNav } from './BottomNav';

describe('BottomNav', () => {
  it('renders navigation items', () => {
    render(
      <BrowserRouter>
        <BottomNav />
      </BrowserRouter>
    );
    
    expect(screen.getByText('Dashboard')).toBeInTheDocument();
    expect(screen.getByText('Expenses')).toBeInTheDocument();
  });
});
```

### Testing with Context
```typescript
// Test with AppProvider wrapper
const renderWithProviders = (component: React.ReactNode) => {
  return render(
    <AppProvider>
      <BrowserRouter>
        {component}
      </BrowserRouter>
    </AppProvider>
  );
};
```

## Integration Testing

### Testing Context Interactions
```typescript
// contexts/integration.test.tsx
describe('Context Integration', () => {
  it('persists data across contexts', () => {
    // Test that expenses and categories work together
  });
  
  it('maintains state through navigation', () => {
    // Test state persistence across page changes
  });
});
```

## Web Deployment

### Building for Production
```bash
# Create optimized build
npm run build

# Preview locally
npm run preview
```

### Static Hosting Options

#### Vercel
```bash
npm i -g vercel
vercel --prod
```

#### Netlify
```bash
npm i -g netlify-cli
netlify deploy --prod --dir=dist
```

#### GitHub Pages
1. Enable GitHub Pages in repository settings
2. Set source to GitHub Actions
3. Use workflow:

```yaml
# .github/workflows/deploy.yml
name: Deploy to GitHub Pages
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
      - run: npm ci
      - run: npm run build
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

## Android Deployment

### Preparing for Release

1. **Update Version**
   ```json
   // package.json
   {
     "version": "1.0.0"
   }
   ```

2. **Build Web Assets**
   ```bash
   npm run build
   npx cap sync android
   ```

3. **Configure Signing**
   ```gradle
   // android/app/build.gradle
   android {
     signingConfigs {
       release {
         storeFile file("my-release-key.jks")
         storePassword "password"
         keyAlias "my-alias"
         keyPassword "password"
       }
     }
   }
   ```

### Building APK
```bash
cd android
./gradlew assembleRelease
```

Output: `android/app/build/outputs/apk/release/app-release.apk`

### Building App Bundle (AAB)
```bash
cd android
./gradlew bundleRelease
```

Output: `android/app/build/outputs/bundle/release/app-release.aab`

### Google Play Store Deployment

1. Create Google Play Developer account
2. Create new app in Play Console
3. Upload AAB file
4. Complete store listing
5. Submit for review

## CI/CD Pipeline

### GitHub Actions Workflow
```yaml
name: Build and Deploy
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
      - run: npm ci
      - run: npm run lint
      - run: npm run type-check
      - run: npm run test:unit

  build-web:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
      - run: npm ci
      - run: npm run build
      - uses: actions/upload-artifact@v3
        with:
          name: web-build
          path: dist

  build-android:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
      - run: npm ci
      - run: npm run build
      - run: npx cap sync android
      - uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'temurin'
      - run: cd android && ./gradlew assembleDebug
```

## Environment Variables

### Production Environment
```env
# .env.production
VITE_APP_NAME=Expense Tracker
VITE_APP_VERSION=1.0.0
VITE_API_URL=https://api.example.com
VITE_ENABLE_ANALYTICS=true
```

### Environment-Specific Config
```typescript
// config.ts
export const config = {
  apiUrl: import.meta.env.VITE_API_URL,
  appVersion: import.meta.env.VITE_APP_VERSION,
  enableAnalytics: import.meta.env.VITE_ENABLE_ANALYTICS === 'true',
};
```

## Monitoring and Analytics

### Error Tracking
```bash
npm install @sentry/react
```

```typescript
// main.tsx
import * as Sentry from '@sentry/react';

Sentry.init({
  dsn: import.meta.env.VITE_SENTRY_DSN,
  environment: import.meta.env.MODE,
});
```

### Performance Monitoring
- Use Lighthouse CI for performance budgets
- Monitor Core Web Vitals
- Track Android app performance metrics

## Rollback Strategy

### Web Rollback
- Keep previous deployments tagged
- Use blue-green deployment
- Instant rollback via hosting platform

### Android Rollback
- Maintain previous AAB versions in Play Console
- Use staged rollouts
- Monitor crash reports before full release

## Troubleshooting

### Build Failures
- Check Node.js version compatibility
- Verify all dependencies installed
- Review TypeScript errors

### Android Issues
- Ensure Android SDK is up to date
- Check signing configuration
- Verify Capacitor sync completed

### Deployment Issues
- Verify environment variables set
- Check build output paths
- Review hosting platform logs
