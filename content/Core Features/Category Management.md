# Category Management

This document describes the category management functionality.

## Category Structure

Each category includes:
- **id**: Unique identifier
- **name**: Display name
- **icon**: Remix Icon class name
- **color**: Hex color code
- **budget**: Monthly budget amount

## Default Categories

The application includes 8 default categories:
1. Food & Dining (Red)
2. Health & Fitness (Teal)
3. Transportation (Mint)
4. Housing (Coral)
5. Entertainment (Purple)
6. Utilities (Pink)
7. Shopping (Yellow)
8. Healthcare (Green)

## CRUD Operations

### Create
- Modal form for adding categories
- Icon selector (14 options)
- Color picker (15 options)
- Budget field (optional)

### Read
- List view with category cards
- Icon and color display
- Budget information

### Update
- Edit modal with pre-filled data
- Update any field
- Preserve expense associations

### Delete
- Remove category from list
- Expenses retain category reference

## UI Components

- Category cards with visual indicators
- Modal forms for add/edit
- Grid selectors for icons and colors
- Budget input with currency formatting
