# User Interface Components

This document describes the reusable UI components in the application.

## BottomNav Component

Fixed bottom navigation with:
- 5 navigation tabs
- Active state highlighting
- Floating action button (Add Expense)
- Icon and label for each tab

### Navigation Targets
1. Dashboard (Home icon)
2. Expenses (List icon)
3. Add Expense (Plus icon - centered, elevated)
4. Reports (Chart icon)
5. Profile (User icon)

## Common UI Patterns

### Cards
- White background (light mode)
- Dark gray background (dark mode)
- Rounded corners (xl)
- Shadow effects
- Consistent padding

### Buttons
- Primary: Purple gradient
- Secondary: Gray/outline
- Icon buttons: Circular
- Full-width on mobile

### Forms
- Labeled inputs
- Focus rings
- Error states
- Currency prefix for amount

### Lists
- Dividers between items
- Icon + text layout
- Right-aligned actions
- Empty states

## Responsive Design

### Mobile-First Approach
- Base styles for mobile
- Breakpoints: sm, md, lg, xl
- Touch-friendly targets (min 44px)
- Bottom navigation for thumb reach

### Dark Mode Support
- `dark:` prefix classes
- Document class toggling
- Smooth transitions
- Consistent contrast ratios
