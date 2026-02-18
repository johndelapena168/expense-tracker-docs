# Categories Page

This document describes the Categories page.

## Purpose

Manage expense categories with full CRUD operations.

## Features

### Category List
- Card-based layout
- Icon and color circle
- Name and budget
- Edit/delete actions

### Add Category
Modal form with:
- Name input
- Budget field
- Icon selector (14 options)
- Color picker (15 options)

### Edit Category
- Pre-filled modal
- Update any field
- Save changes

### Delete Category
- Remove from list
- No confirmation (future enhancement)

## UI Components

- Category cards
- Modal overlay
- Grid selectors
- Form inputs
- Action buttons

## State Management

Uses CategoriesContext for:
- Loading categories
- CRUD operations
- Persistence
