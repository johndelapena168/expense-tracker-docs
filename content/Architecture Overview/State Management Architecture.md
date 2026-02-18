# State Management Architecture

This document explains the React Context API-based state management architecture.

## Hierarchical Provider Pattern

```
AppProvider (Global Settings)
└── CategoriesProvider (Category Management)
    └── ExpensesProvider (Expense Tracking)
```

## Context Factory Pattern

Each context follows a consistent pattern:
1. Define TypeScript interface
2. Create Provider component
3. Export custom hook
4. Implement localStorage persistence

## State Persistence

All contexts persist state to localStorage:
- AppContext: currency, darkMode
- CategoriesContext: categories array
- ExpensesContext: expenses array

## Performance Optimizations

- Provider isolation prevents unnecessary re-renders
- Lazy initialization from localStorage
- Efficient filtering algorithms
- Memoized derived computations
