# Architecture Overview

This document describes the architecture of the Expense Tracker application, focusing on the React-based frontend built with Vite, React Context API for state management, routing with lazy-loaded pages, and cross-platform strategy using Capacitor.

## Key Architectural Components

### Provider Chain
- **AppProvider**: Global settings (currency, dark mode, formatting)
- **CategoriesProvider**: Category management with CRUD operations
- **ExpensesProvider**: Expense tracking with persistence

### Routing Architecture
- React Router v7 with lazy-loaded components
- Code splitting for improved performance
- Centralized route configuration

### Cross-Platform Strategy
- Capacitor for Android deployment
- Single codebase for web and mobile
- WebView-based native app

## Documentation Sections

For detailed information, see the specific architecture documents:
- [Component Hierarchy and Routing](Component%20Hierarchy%20and%20Routing.md)
- [Cross-Platform Development Strategy](Cross-Platform%20Development%20Strategy.md)
- [Data Flow and Communication Patterns](Data%20Flow%20and%20Communication%20Patterns.md)
- [State Management Architecture](State%20Management%20Architecture.md)
