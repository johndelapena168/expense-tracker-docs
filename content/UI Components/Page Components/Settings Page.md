# Settings Page

This document describes the Settings page.

## Purpose

Configure application preferences.

## Settings

### Currency
- Modal selector
- 8 currencies supported
- Symbol preview

### Notifications
- Toggle switch
- Local state only
- Future: push notifications

### Dark Mode
- Toggle switch
- Immediate effect
- Persisted to storage

### About
- App version
- Privacy policy link
- Terms of service

### Account
- Logout button
- Future: account deletion

## UI Layout

- Fixed header with back
- Settings list
- Tappable rows
- Modal for currency
- Bottom navigation

## State Management

Uses AppContext for:
- Currency selection
- Dark mode toggle
- Persistence
