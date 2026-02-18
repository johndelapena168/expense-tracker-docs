# Platform Compatibility

This document describes platform compatibility considerations.

## Browser Support

### Supported Browsers
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

### Required Features
- ES2020+ JavaScript
- CSS Grid and Flexbox
- LocalStorage API
- Web Animations API

## Android Support

### Minimum Requirements
- Android 5.0 (API 21)
- WebView with Chrome 90+
- 100MB free storage

### Recommended
- Android 10+ (API 29+)
- 2GB RAM
- Chrome WebView

## Feature Detection

### LocalStorage
```typescript
const isStorageAvailable = () => {
  try {
    const test = '__storage_test__';
    localStorage.setItem(test, test);
    localStorage.removeItem(test);
    return true;
  } catch (e) {
    return false;
  }
};
```

### Dark Mode
```typescript
const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
```

## Platform-Specific Code

### Conditional Rendering
```typescript
const isAndroid = Capacitor.getPlatform() === 'android';
const isWeb = Capacitor.getPlatform() === 'web';
```

### Native Features
Use Capacitor plugins for:
- Camera access
- File system
- Geolocation
- Push notifications
- Storage

## Responsive Breakpoints

| Breakpoint | Width | Target |
|------------|-------|--------|
| sm | 640px | Large phones |
| md | 768px | Tablets |
| lg | 1024px | Small laptops |
| xl | 1280px | Desktops |
