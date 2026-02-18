# Type Definitions and Validation

This document describes type definitions and validation patterns.

## Currency Type

```typescript
interface Currency {
  code: string;
  symbol: string;
  name: string;
}

const currencies: Currency[] = [
  { code: 'USD', symbol: '$', name: 'US Dollar' },
  { code: 'PHP', symbol: '₱', name: 'Philippine Peso' },
  { code: 'EUR', symbol: '€', name: 'Euro' },
  { code: 'GBP', symbol: '£', name: 'British Pound' },
  { code: 'JPY', symbol: '¥', name: 'Japanese Yen' },
  { code: 'SGD', symbol: 'S$', name: 'Singapore Dollar' },
  { code: 'AUD', symbol: 'A$', name: 'Australian Dollar' },
  { code: 'CAD', symbol: 'C$', name: 'Canadian Dollar' },
];
```

## Type Guards

### isValidExpense
```typescript
const isValidExpense = (obj: any): obj is Expense => {
  return (
    typeof obj.id === 'string' &&
    typeof obj.amount === 'number' &&
    typeof obj.description === 'string' &&
    typeof obj.category === 'string' &&
    typeof obj.date === 'string'
  );
};
```

### isValidCategory
```typescript
const isValidCategory = (obj: any): obj is Category => {
  return (
    typeof obj.id === 'string' &&
    typeof obj.name === 'string' &&
    typeof obj.icon === 'string' &&
    typeof obj.color === 'string' &&
    typeof obj.budget === 'number'
  );
};
```

## Validation Functions

### validateExpense
```typescript
const validateExpense = (expense: Partial<Expense>): string[] => {
  const errors: string[] = [];
  
  if (!expense.amount || expense.amount <= 0) {
    errors.push('Amount must be greater than 0');
  }
  
  if (!expense.description?.trim()) {
    errors.push('Description is required');
  }
  
  if (!expense.categoryId) {
    errors.push('Category is required');
  }
  
  return errors;
};
```

### validateCategory
```typescript
const validateCategory = (category: Partial<Category>): string[] => {
  const errors: string[] = [];
  
  if (!category.name?.trim()) {
    errors.push('Name is required');
  }
  
  if (!category.icon) {
    errors.push('Icon is required');
  }
  
  if (!category.color) {
    errors.push('Color is required');
  }
  
  return errors;
};
```

## Utility Types

### Omit for Creation
```typescript
type CreateExpenseInput = Omit<Expense, 'id'>;
type CreateCategoryInput = Omit<Category, 'id'>;
```

### Partial for Updates
```typescript
type UpdateExpenseInput = Partial<Omit<Expense, 'id'>>;
type UpdateCategoryInput = Partial<Omit<Category, 'id'>>;
```
