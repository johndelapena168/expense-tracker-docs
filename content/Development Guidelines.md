# Development Guidelines

<cite>
**Referenced Files in This Document**
- [AppContext.tsx](file://src/contexts/AppContext.tsx)
- [CategoriesContext.tsx](file://src/contexts/CategoriesContext.tsx)
- [ExpensesContext.tsx](file://src/contexts/ExpensesContext.tsx)
- [BottomNav.tsx](file://src/components/BottomNav.tsx)
- [page.tsx](file://src/pages/dashboard/page.tsx)
- [page.tsx](file://src/pages/categories/page.tsx)
- [page.tsx](file://src/pages/expenses/page.tsx)
- [page.tsx](file://src/pages/add-expense/page.tsx)
- [page.tsx](file://src/pages/reports/page.tsx)
- [page.tsx](file://src/pages/settings/page.tsx)
- [page.tsx](file://src/pages/profile/page.tsx)
- [config.tsx](file://src/router/config.tsx)
- [main.tsx](file://src/main.tsx)
- [expenses.ts](file://src/mocks/expenses.ts)
- [capacitor.config.ts](file://capacitor.config.ts)
</cite>

## Table of Contents
1. [Introduction](#introduction)
2. [Project Structure](#project-structure)
3. [Core Components](#core-components)
4. [Architecture Overview](#architecture-overview)
5. [Detailed Component Analysis](#detailed-component-analysis)
6. [Dependency Analysis](#dependency-analysis)
7. [Performance Considerations](#performance-considerations)
8. [Testing Strategy](#testing-strategy)
9. [Troubleshooting Guide](#troubleshooting-guide)
10. [Conclusion](#conclusion)

## Introduction
This document provides comprehensive development guidelines for the Expense Tracker application. It covers the project structure, core components, architecture patterns, state management strategies, and best practices for extending and maintaining the codebase. The guidelines ensure consistency, maintainability, and scalability across the application.

## Project Structure
The Expense Tracker follows a well-organized directory structure that separates concerns and promotes modularity:

```
src/
├── components/        # Reusable UI components
├── contexts/         # React Context providers for state management
├── hooks/            # Custom React hooks
├── mocks/            # Mock data for development
├── pages/            # Page components organized by feature
├── router/           # Routing configuration
├── assets/           # Static assets
└── main.tsx          # Application entry point
```

**Key architectural decisions:**
- Context-based state management (no Redux)
- LocalStorage for data persistence
- Lazy-loaded routes for performance
- Mobile-first responsive design

## Core Components

### Context Providers
The application uses three main context providers:

1. **AppContext**: Global application settings (currency, dark mode, formatting)
2. **CategoriesContext**: Category management (CRUD operations, budgets)
3. **ExpensesContext**: Expense tracking (add, delete, filtering, totals)

### Navigation
- **BottomNav**: Fixed bottom navigation for mobile experience
- **React Router**: Client-side routing with lazy loading

### Page Components
- Dashboard: Financial overview and analytics
- Expenses: Expense list management
- Add Expense: Form for creating new expenses
- Categories: Category management interface
- Reports: Spending analysis and visualizations
- Settings: Application preferences
- Profile: User account information

## Architecture Overview

### State Management Pattern
The application uses React Context API with a hierarchical provider structure:

```
AppProvider
└── CategoriesProvider
    └── ExpensesProvider
        └── AppRoutes
```

This pattern ensures:
- Predictable data flow
- Proper initialization order
- Efficient state sharing
- Clear dependency hierarchy

### Data Flow
1. Context providers initialize from localStorage
2. Pages consume context data via custom hooks
3. User actions trigger context methods
4. Context updates state and persists to localStorage
5. UI re-renders with updated data

## Detailed Component Analysis

### Context Implementation
Each context follows a consistent pattern:
- TypeScript interfaces for type safety
- Provider component with state management
- Custom hook for consuming the context
- localStorage integration for persistence

### Page Component Structure
Pages follow a consistent layout:
- Fixed header with navigation
- Scrollable content area
- Bottom navigation bar
- Responsive container with max-width

### Form Handling
Forms implement:
- Controlled inputs with React state
- Client-side validation
- Error handling and user feedback
- Navigation after successful submission

## Dependency Analysis

### External Dependencies
- **React 19.2.0**: Core UI library
- **React Router 7.13.0**: Client-side routing
- **Tailwind CSS 4.1.18**: Utility-first styling
- **Capacitor 7.0.0**: Cross-platform mobile deployment
- **Remix Icons**: Icon library

### Internal Dependencies
Contexts have minimal coupling:
- AppContext: No dependencies
- CategoriesContext: Depends on AppContext
- ExpensesContext: Depends on CategoriesContext and AppContext

## Performance Considerations

### Optimization Strategies
1. **Lazy Loading**: Route components loaded on demand
2. **Selective Context Updates**: Only re-render when necessary
3. **Efficient Filtering**: Linear-time algorithms for data processing
4. **Local Storage Batching**: Minimize write operations

### Memory Management
- Automatic cleanup on component unmount
- Stable references for unchanged data
- Efficient serialization for storage

## Testing Strategy

### Unit Testing
- Test individual context methods
- Validate data transformations
- Mock localStorage operations

### Component Testing
- Render pages with mock contexts
- Test user interactions
- Verify navigation flows

### Integration Testing
- Test context provider hierarchy
- Validate data persistence
- Check cross-platform compatibility

## Troubleshooting Guide

### Common Issues

**State Not Persisting**
- Verify localStorage availability
- Check context provider wrapping
- Validate JSON serialization

**Navigation Not Working**
- Confirm route configuration
- Check BottomNav active state logic
- Verify React Router setup

**Styling Issues**
- Ensure Tailwind CSS is configured
- Check dark mode class application
- Verify responsive breakpoints

## Conclusion
Following these guidelines ensures:
- Consistent code quality
- Maintainable architecture
- Scalable feature development
- Optimal performance
- Cross-platform compatibility

For questions or contributions, refer to the specific component documentation in the respective folders.
