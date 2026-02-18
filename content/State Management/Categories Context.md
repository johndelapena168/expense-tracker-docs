# Categories Context

This document describes the CategoriesContext for category management.

## Purpose

Manages expense categories with:
- CRUD operations
- Budget allocation
- Icon and color customization

## Interface

```typescript
interface CategoriesContextType {
  categories: Category[];
  addCategory: (category: Omit<Category, 'id'>) => void;
  updateCategory: (id: string, updates: Partial<Category>) => void;
  deleteCategory: (id: string) => void;
}

interface Category {
  id: string;
  name: string;
  icon: string;
  color: string;
  budget: number;
}
```

## Usage

```typescript
const { categories, addCategory, updateCategory, deleteCategory } = useCategories();
```

## Operations

### Add Category
```typescript
addCategory({
  name: 'Groceries',
  icon: 'ri-shopping-cart-line',
  color: '#4CAF50',
  budget: 300
});
```

### Update Category
```typescript
updateCategory('cat123', { budget: 400 });
```

### Delete Category
```typescript
deleteCategory('cat123');
```

## Persistence

Categories persisted to `expense-tracker-categories` in localStorage.

## Initialization

1. Try loading from localStorage
2. Fall back to mock data if empty
3. Set default categories

## Default Categories

8 predefined categories with icons and colors.
