# Category Entity

This document describes the Category entity.

## Interface

```typescript
interface Category {
  id: string;
  name: string;
  icon: string;
  color: string;
  budget: number;
}
```

## Fields

### id
- Type: `string`
- Format: `'cat' + timestamp`
- Unique identifier

### name
- Type: `string`
- Required
- Display name for the category

### icon
- Type: `string`
- Remix Icon class name
- Examples: `ri-restaurant-line`, `ri-car-line`

### color
- Type: `string`
- Hex color code
- Examples: `#FF6B6B`, `#4ECDC4`

### budget
- Type: `number`
- Monthly budget amount
- 0 if not set

## Default Categories

| Name | Icon | Color | Budget |
|------|------|-------|--------|
| Food & Dining | ri-restaurant-line | #FF6B6B | 500 |
| Health & Fitness | ri-heart-pulse-line | #4ECDC4 | 200 |
| Transportation | ri-car-line | #95E1D3 | 300 |
| Housing | ri-home-line | #F38181 | 1500 |
| Entertainment | ri-movie-line | #AA96DA | 150 |
| Utilities | ri-lightbulb-line | #FCBAD3 | 200 |
| Shopping | ri-shopping-bag-line | #FFFFD2 | 400 |
| Healthcare | ri-medicine-bottle-line | #A8E6CF | 250 |

## Context Interface

```typescript
interface CategoriesContextType {
  categories: Category[];
  addCategory: (category: Omit<Category, 'id'>) => void;
  updateCategory: (id: string, updates: Partial<Category>) => void;
  deleteCategory: (id: string) => void;
}
```
