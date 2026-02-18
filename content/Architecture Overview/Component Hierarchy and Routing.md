# Component Hierarchy and Routing

This document explains the component hierarchy and routing architecture of the expense tracker application.

## Provider Chain

The application uses a hierarchical provider pattern:

```
AppProvider
└── CategoriesProvider
    └── ExpensesProvider
        └── AppRoutes
```

## Routing Configuration

Routes are configured using React Router with lazy-loaded components:

- `/` - Dashboard
- `/expenses` - Expense list
- `/add-expense` - Add new expense
- `/categories` - Category management
- `/reports` - Analytics and reports
- `/settings` - App settings
- `/profile` - User profile

## Navigation

The BottomNav component provides mobile-first navigation with:
- Five primary destinations
- Active state highlighting
- Floating action button for quick add
