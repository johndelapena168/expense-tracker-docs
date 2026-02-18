# Provider Hierarchy and Composition

This document describes the provider hierarchy and composition patterns.

## Hierarchy

```
BrowserRouter
└── AppProvider
    └── CategoriesProvider
        └── ExpensesProvider
            └── AppRoutes
```

## Provider Order

The order matters because:
1. AppProvider has no dependencies
2. CategoriesProvider may use AppContext
3. ExpensesProvider may use CategoriesContext
4. Routes consume all contexts

## Implementation

```tsx
// main.tsx
ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <BrowserRouter>
      <AppProvider>
        <CategoriesProvider>
          <ExpensesProvider>
            <AppRoutes />
          </ExpensesProvider>
        </CategoriesProvider>
      </AppProvider>
    </BrowserRouter>
  </React.StrictMode>
);
```

## Context Consumption

Pages can consume multiple contexts:

```tsx
// Dashboard page
const Dashboard = () => {
  const { formatAmount } = useApp();
  const { categories } = useCategories();
  const { expenses, getCurrentMonthExpenses } = useExpenses();
  
  // Use all three contexts
};
```

## Benefits

1. **Clear Dependencies**: Parent/child relationship explicit
2. **Predictable Initialization**: Order guarantees availability
3. **Scoped State**: Each context manages one domain
4. **Easy Testing**: Mock providers individually

## Extending

To add a new context:
1. Create context file
2. Add provider to hierarchy
3. Export hook for consumption
4. Update main.tsx

## Best Practices

- Keep providers focused on one domain
- Avoid deep nesting (max 3-4 levels)
- Use custom hooks for consumption
- Document dependencies between contexts
