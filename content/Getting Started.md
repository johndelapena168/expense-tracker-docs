# Getting Started

<cite>
**Referenced Files in This Document**
- [package.json](file://package.json)
- [main.tsx](file://src/main.tsx)
- [AppContext.tsx](file://src/contexts/AppContext.tsx)
- [CategoriesContext.tsx](file://src/contexts/CategoriesContext.tsx)
- [ExpensesContext.tsx](file://src/contexts/ExpensesContext.tsx)
- [capacitor.config.ts](file://capacitor.config.ts)
- [vite.config.ts](file://vite.config.ts)
- [tailwind.config.ts](file://tailwind.config.ts)
- [tsconfig.json](file://tsconfig.json)
</cite>

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Development Server](#development-server)
5. [Building for Production](#building-for-production)
6. [Android Deployment](#android-deployment)
7. [Project Structure](#project-structure)
8. [Environment Configuration](#environment-configuration)
9. [Troubleshooting](#troubleshooting)

## Introduction
This guide will help you set up and run the Expense Tracker application on your local machine. The application is built with React, TypeScript, and Vite, supporting both web and Android platforms through Capacitor.

## Prerequisites
Before you begin, ensure you have the following installed:

- **Node.js** (version 18 or higher)
- **npm** or **yarn** package manager
- **Git** for version control
- **Android Studio** (for Android deployment)
- **Java Development Kit (JDK)** 17 or higher

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd expense-tracker
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   Edit `.env` with your configuration if needed.

## Development Server

Start the development server:
```bash
npm run dev
```

The application will be available at `http://localhost:5173`

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint
- `npm run type-check` - Run TypeScript compiler

## Building for Production

1. **Build the web application**
   ```bash
   npm run build
   ```

2. **Preview the production build**
   ```bash
   npm run preview
   ```

## Android Deployment

### Initial Setup

1. **Add Android platform** (first time only)
   ```bash
   npx cap add android
   ```

2. **Sync web assets to Android**
   ```bash
   npx cap sync android
   ```

### Building and Running

1. **Open in Android Studio**
   ```bash
   npx cap open android
   ```

2. **Build APK/Bundle**
   - In Android Studio: Build → Build Bundle(s) / APK(s)
   - Or use Gradle commands

### Live Reload for Android

For development with live reload on Android:
```bash
npm run dev:android
```

## Project Structure

```
expense-tracker/
├── android/              # Android platform files
├── public/               # Static assets
├── src/
│   ├── assets/          # Images and static files
│   ├── components/      # Reusable UI components
│   ├── contexts/        # React Context providers
│   ├── hooks/           # Custom React hooks
│   ├── mocks/           # Mock data
│   ├── pages/           # Page components
│   ├── router/          # Routing configuration
│   ├── index.css        # Global styles
│   └── main.tsx         # Application entry
├── .env.example         # Environment template
├── capacitor.config.ts  # Capacitor configuration
├── package.json         # Dependencies
├── tailwind.config.ts   # Tailwind CSS config
├── tsconfig.json        # TypeScript configuration
└── vite.config.ts       # Vite configuration
```

## Environment Configuration

### Environment Variables

Create a `.env` file with the following variables:

```env
# Application
VITE_APP_NAME=Expense Tracker
VITE_APP_VERSION=1.0.0

# API (if applicable)
VITE_API_URL=http://localhost:3000

# Features
VITE_ENABLE_ANALYTICS=false
```

### Capacitor Configuration

The `capacitor.config.ts` file contains platform-specific settings:

```typescript
const config: CapacitorConfig = {
  appId: 'com.example.expensetracker',
  appName: 'Expense Tracker',
  webDir: 'dist',
  server: {
    androidScheme: 'https'
  }
};
```

## Troubleshooting

### Common Issues

**Port already in use**
```bash
# Kill process on port 5173
npx kill-port 5173
```

**Android build fails**
- Ensure Android Studio is properly configured
- Check that JDK is installed and JAVA_HOME is set
- Run `npx cap sync android` after web changes

**Dependencies not resolving**
```bash
rm -rf node_modules package-lock.json
npm install
```

**TypeScript errors**
```bash
npm run type-check
```

### Getting Help

If you encounter issues:
1. Check the [Troubleshooting Guide](Troubleshooting%20Guide.md)
2. Review component-specific documentation
3. Check the project issues on GitHub

## Next Steps

After setup, explore:
- [Project Overview](Project%20Overview.md) for architecture details
- [Development Guidelines](Development%20Guidelines.md) for coding standards
- Individual component documentation in respective folders
