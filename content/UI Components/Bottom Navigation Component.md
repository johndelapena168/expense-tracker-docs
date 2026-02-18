# Bottom Navigation Component

This document describes the BottomNav component.

## Overview

Fixed bottom navigation bar optimized for mobile devices.

## Features

- 5 navigation tabs
- Active state highlighting
- Floating action button (center)
- React Router integration

## Navigation Targets

| Tab | Path | Icon |
|-----|------|------|
| Dashboard | / | Home |
| Expenses | /expenses | List |
| Add | /add-expense | Plus (FAB) |
| Reports | /reports | Chart |
| Profile | /profile | User |

## Implementation

```tsx
const BottomNav = () => {
  const location = useLocation();
  const navigate = useNavigate();
  
  const isActive = (path: string) => location.pathname === path;
  
  return (
    <nav className="fixed bottom-0 left-0 right-0 bg-white dark:bg-gray-900">
      {/* Navigation buttons */}
    </nav>
  );
};
```

## Styling

- Fixed positioning at bottom
- White/dark background
- Border top for separation
- Safe area padding for notched devices
- Max-width container for larger screens

## Floating Action Button

- Centered position
- Elevated with negative margin
- Gradient background
- Shadow effect

## Accessibility

- Semantic nav element
- Button elements for interactions
- Visual focus indicators
- ARIA labels for icons
