# Expenses Context

This document describes the ExpensesContext for expense tracking.

## Purpose

Manages expense records with:
- CRUD operations
- Monthly filtering
- Total calculations

## Interface

```typescript
interface ExpensesContextType {
  expenses: Expense[];
  addExpense: (expense: Omit<Expense, 'id'>) => void;
  deleteExpense: (id: string) => void;
  getCurrentMonthExpenses: () => Expense[];
  getTotalForMonth: (month: number, year: number) => number;
}

interface Expense {
  id: string;
  amount: number;
  description: string;
  category: string;
  categoryId: string;
  date: string;
  icon: string;
  color: string;
  paymentMethod: 'Cash' | 'Credit Card' | 'Gcash';
}
```

## Usage

```typescript
const { expenses, addExpense, deleteExpense, getCurrentMonthExpenses, getTotalForMonth } = useExpenses();
```

## Operations

### Add Expense
```typescript
addExpense({
  amount: 50.00,
  description: 'Grocery shopping',
  category: 'Food & Dining',
  categoryId: 'cat123',
  date: '2024-01-15',
  icon: 'ri-restaurant-line',
  color: '#FF6B6B',
  paymentMethod: 'Credit Card'
});
```

### Delete Expense
```typescript
deleteExpense('exp456');
```

### Get Current Month
```typescript
const currentExpenses = getCurrentMonthExpenses();
```

### Get Monthly Total
```typescript
const total = getTotalForMonth(0, 2024); // January 2024
```

## Persistence

Expenses persisted to `expense-tracker-expenses` in localStorage.

## Filtering

Current month filter uses date comparison:
```typescript
const getCurrentMonthExpenses = () => {
  const now = new Date();
  return expenses.filter(expense => {
    const date = new Date(expense.date);
    return date.getMonth() === now.getMonth() && 
           date.getFullYear() === now.getFullYear();
  });
};
```
