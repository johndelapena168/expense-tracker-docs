# Data Flow and Communication Patterns

This document explains how data flows through the application's React components and contexts.

## Unidirectional Data Flow

1. Data enters via context providers at the root
2. Consumers subscribe via custom hooks
3. Page components compute derived analytics
4. Events trigger actions that update context state

## Context Providers

### AppContext
- Currency selection and formatting
- Dark mode toggle
- User preferences persistence

### CategoriesContext
- Category CRUD operations
- Budget management
- Icon and color customization

### ExpensesContext
- Expense CRUD operations
- Monthly filtering
- Total calculations

## Event Handling

- Form submissions trigger context updates
- Navigation uses React Router hooks
- State changes persist to localStorage
