# Web Deployment

This document describes web deployment options.

## Build Process

### Production Build
```bash
npm run build
```

Output: `dist/` directory with optimized assets.

### Preview Build
```bash
npm run preview
```

## Deployment Options

### Static Hosting

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
Use GitHub Actions workflow for automatic deployment.

### CDN Deployment
- Upload `dist/` contents to CDN
- Configure cache headers
- Set up SSL certificate

## Environment Variables

### Production
```env
VITE_APP_NAME=Expense Tracker
VITE_APP_VERSION=1.0.0
VITE_API_URL=https://api.example.com
```

### Build-time Variables
All `VITE_` prefixed variables are available in the app.

## Performance Optimization

### Build Output
- Minified JavaScript
- Optimized CSS
- Compressed assets
- Code splitting

### Caching Strategy
- Hash in filename for cache busting
- Service worker for offline support
- LocalStorage for data persistence

## Security Considerations

- HTTPS only
- Content Security Policy
- Secure localStorage usage
- Input validation
