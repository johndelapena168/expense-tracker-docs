# Settings and Profile

This document describes the settings and profile features.

## Settings Page

### Currency Selection
Supported currencies:
- USD ($) - US Dollar
- PHP (₱) - Philippine Peso
- EUR (€) - Euro
- GBP (£) - British Pound
- JPY (¥) - Japanese Yen
- SGD (S$) - Singapore Dollar
- AUD (A$) - Australian Dollar
- CAD (C$) - Canadian Dollar

### Theme Settings
- Light/Dark mode toggle
- System preference detection
- Immediate application
- Persisted to localStorage

### Notifications
- Enable/disable toggle
- Local state management
- Placeholder for future implementation

### About Section
- App version
- Privacy policy link
- Logout action

## Profile Page

### User Information
- Avatar placeholder
- User name display
- Account type indicator

### Quick Actions
- Categories shortcut
- Settings shortcut
- Notifications toggle
- Dark mode toggle
- Help & Support
- Logout

## Implementation

### AppContext
Manages all settings state:
- Currency object with code, symbol, name
- Dark mode boolean
- Persistence to localStorage
- Formatting utilities

### Data Persistence
All preferences saved to localStorage:
- `expense-tracker-currency`
- `expense-tracker-darkMode`
- Loaded on app initialization
