# Add Expense Page

This document describes the Add Expense page.

## Purpose

Form interface for creating new expense records.

## Form Fields

1. **Amount** (required)
   - Number input
   - Currency symbol prefix
   - Decimal support

2. **Date** (required)
   - Date picker
   - Defaults to today

3. **Description** (required)
   - Text input
   - Placeholder: "What did you spend on?"

4. **Category** (required)
   - Grid of category buttons
   - Icon and color display
   - Single selection

5. **Payment Method** (required)
   - Cash, Credit Card, GCash
   - Icon buttons
   - Defaults to Cash

## Validation

- Amount must be > 0
- Description cannot be empty
- Category must be selected

## Submission Flow

1. Validate inputs
2. Find selected category
3. Create expense object
4. Call addExpense()
5. Navigate to dashboard

## UI Layout

- Fixed header with back button
- Form in scrollable area
- Sectioned cards for groups
- Bottom navigation
