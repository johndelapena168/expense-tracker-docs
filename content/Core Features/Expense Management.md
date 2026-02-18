# Expense Management

This document describes the expense management functionality.

## Expense Structure

Each expense includes:
- **id**: Unique identifier
- **amount**: Numeric value
- **description**: Text description
- **category**: Category name
- **categoryId**: Category reference
- **date**: ISO date string
- **icon**: Category icon
- **color**: Category color
- **paymentMethod**: Cash, Credit Card, or GCash

## Adding Expenses

### Form Fields
1. Amount (required)
2. Date (defaults to today)
3. Description (required)
4. Category selection (required)
5. Payment method (defaults to Cash)

### Validation
- Amount must be positive number
- Description cannot be empty
- Category must be selected

### Process
1. User fills form
2. Validation occurs
3. Expense is created with unique ID
4. Added to expenses list
5. Persisted to localStorage
6. User redirected to dashboard

## Viewing Expenses

### Expenses List Page
- Chronological list (newest first)
- Category icon and color
- Formatted amount
- Date display
- Description preview

### Dashboard Recent Transactions
- Last 5 expenses
- Quick view of recent activity

## Deleting Expenses

- Swipe or button to delete
- Confirmation not required
- Immediate removal from list
- localStorage updated

## Filtering

### Current Month Filter
- Default view on dashboard
- Filters by current month/year
- Used for monthly totals

### Monthly Totals
- Calculate total for any month
- Used in trend charts
- Year-over-year comparison
