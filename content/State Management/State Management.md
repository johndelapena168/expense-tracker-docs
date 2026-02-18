# State Management

This document provides an overview of the state management architecture.

## Overview

The application uses React Context API for state management with a hierarchical provider pattern.

## Context Hierarchy

```
AppProvider (Global Settings)
└── CategoriesProvider (Categories)
    └── ExpensesProvider (Expenses)
        └── Routes (Pages)
```

## Key Principles

1. **Separation of Concerns**: Each context manages one domain
2. **Persistence**: All state persisted to localStorage
3. **Type Safety**: TypeScript interfaces for all state
4. **Lazy Loading**: Routes loaded on demand

## Contexts

### AppContext
Global application settings including currency and theme.

### CategoriesContext
Category management with CRUD operations.

### ExpensesContext
Expense tracking with filtering and totals.

See detailed documentation:
- [App Context](App%20Context.md)
- [Categories Context](Categories%20Context.md)
- [Expenses Context](Expenses%20Context.md)
- [Provider Hierarchy and Composition](Provider%20Hierarchy%20and%20Composition.md)
