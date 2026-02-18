# Expense Entity

This document describes the Expense entity.

## Interface

```typescript
interface Expense {
  id: string;
  amount: number;
  description: string;
  category: string;
  categoryId: string;
  date: string;
  icon: string;
  color: string;
  paymentMethod: PaymentMethod;
}
```

## Fields

### id
- Type: `string`
- Format: `'exp' + timestamp`
- Unique identifier

### amount
- Type: `number`
- Positive value
- Stored as plain number (not cents)

### description
- Type: `string`
- Required
- User-provided description

### category
- Type: `string`
- Category name (denormalized)

### categoryId
- Type: `string`
- Reference to category ID

### date
- Type: `string`
- Format: `YYYY-MM-DD`
- ISO date string

### icon
- Type: `string`
- Category icon (denormalized)

### color
- Type: `string`
- Category color (denormalized)

### paymentMethod
- Type: `PaymentMethod`
- Enum: `'Cash' | 'Credit Card' | 'Gcash'`

## PaymentMethod Enum

```typescript
type PaymentMethod = 'Cash' | 'Credit Card' | 'Gcash';
```

## Context Interface

```typescript
interface ExpensesContextType {
  expenses: Expense[];
  addExpense: (expense: Omit<Expense, 'id'>) => void;
  deleteExpense: (id: string) => void;
  getCurrentMonthExpenses: () => Expense[];
  getTotalForMonth: (month: number, year: number) => number;
}
```

## Denormalization Strategy

Expense records denormalize category data:
- Faster reads (no joins needed)
- Category changes don't update existing expenses
- Simpler component code
