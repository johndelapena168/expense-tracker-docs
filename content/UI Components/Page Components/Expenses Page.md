# Expenses Page

This document describes the Expenses page.

## Purpose

Display and manage all expense records.

## Features

### Expense List
- Chronological order (newest first)
- Infinite scroll (future)
- Pull to refresh (future)

### Expense Cards
- Category icon
- Description
- Date
- Formatted amount
- Delete button

### Empty State
- Message when no expenses
- Call to action

### Floating Add Button
- Quick access to add form
- Positioned above bottom nav

## UI Layout

- Fixed header
- Scrollable list
- Card items
- Bottom navigation

## State Management

Uses ExpensesContext for:
- Loading expenses
- Delete operations
- Real-time updates
