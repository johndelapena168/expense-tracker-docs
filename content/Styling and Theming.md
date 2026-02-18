# Styling and Theming

<cite>
**Referenced Files in This Document**
- [tailwind.config.ts](file://tailwind.config.ts)
- [index.css](file://src/index.css)
- [AppContext.tsx](file://src/contexts/AppContext.tsx)
- [BottomNav.tsx](file://src/components/BottomNav.tsx)
- [page.tsx](file://src/pages/dashboard/page.tsx)
- [page.tsx](file://src/pages/settings/page.tsx)
</cite>

## Table of Contents
1. [Introduction](#introduction)
2. [Tailwind CSS Configuration](#tailwind-css-configuration)
3. [Dark Mode Implementation](#dark-mode-implementation)
4. [Color System](#color-system)
5. [Component Styling Patterns](#component-styling-patterns)
6. [Responsive Design](#responsive-design)
7. [Custom Utilities](#custom-utilities)

## Introduction
The Expense Tracker uses Tailwind CSS for styling, providing a utility-first approach that enables rapid UI development while maintaining consistency. The theming system supports both light and dark modes with smooth transitions.

## Tailwind CSS Configuration

The project uses Tailwind CSS v4 with custom configuration:

```typescript
// tailwind.config.ts
export default {
  content: ['./index.html', './src/**/*.{js,ts,jsx,tsx}'],
  darkMode: 'class',
  theme: {
    extend: {
      colors: {
        primary: {
          50: '#f5f3ff',
          100: '#ede9fe',
          500: '#8b5cf6',
          600: '#7c3aed',
          700: '#6d28d9',
        },
      },
    },
  },
};
```

### Key Features
- **Dark Mode**: Class-based toggling
- **Custom Colors**: Brand-specific palette
- **Responsive**: Mobile-first breakpoints

## Dark Mode Implementation

### Context-Based Theme Management

```typescript
// AppContext.tsx
const [darkMode, setDarkMode] = useState(false);

useEffect(() => {
  if (darkMode) {
    document.documentElement.classList.add('dark');
  } else {
    document.documentElement.classList.remove('dark');
  }
  localStorage.setItem('darkMode', JSON.stringify(darkMode));
}, [darkMode]);
```

### Usage in Components

```tsx
<div className="bg-white dark:bg-gray-900 text-gray-900 dark:text-white">
  Content adapts to theme
</div>
```

### Theme-Aware Classes

| Light Mode | Dark Mode | Purpose |
|------------|-----------|---------|
| `bg-white` | `dark:bg-gray-900` | Background |
| `text-gray-900` | `dark:text-white` | Primary text |
| `text-gray-600` | `dark:text-gray-400` | Secondary text |
| `border-gray-200` | `dark:border-gray-700` | Borders |
| `bg-gray-50` | `dark:bg-gray-800` | Card backgrounds |

## Color System

### Primary Brand Colors
- **Purple-500** (#8b5cf6): Primary actions, highlights
- **Purple-600** (#7c3aed): Hover states
- **Purple-700** (#6d28d9): Active states

### Semantic Colors
- **Green**: Success, positive trends
- **Red**: Error, negative trends, deletions
- **Yellow**: Warnings, alerts
- **Blue**: Information, links

### Category Colors
Categories use a predefined palette:
- Red (#FF6B6B): Food & Dining
- Teal (#4ECDC4): Health & Fitness
- Mint (#95E1D3): Transportation
- Coral (#F38181): Housing
- Purple (#AA96DA): Entertainment
- Pink (#FCBAD3): Utilities
- Yellow (#FFFFD2): Shopping
- Green (#A8E6CF): Healthcare

## Component Styling Patterns

### Card Pattern
```tsx
<div className="bg-white dark:bg-gray-800 rounded-xl shadow-sm border border-gray-200 dark:border-gray-700 p-4">
  Card content
</div>
```

### Button Pattern
```tsx
<button className="bg-purple-600 hover:bg-purple-700 text-white font-medium py-2 px-4 rounded-lg transition-colors">
  Action
</button>
```

### Input Pattern
```tsx
<input className="w-full px-4 py-2 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent dark:bg-gray-800 dark:text-white" />
```

### Navigation Pattern
```tsx
<nav className="fixed bottom-0 left-0 right-0 bg-white dark:bg-gray-900 border-t border-gray-200 dark:border-gray-700">
  Navigation content
</nav>
```

## Responsive Design

### Breakpoints
- **sm**: 640px
- **md**: 768px
- **lg**: 1024px
- **xl**: 1280px

### Mobile-First Approach
```tsx
// Base styles for mobile
<div className="grid grid-cols-1 gap-4">
  {/* Tablet and up */}
  <div className="md:grid-cols-2">
    {/* Desktop and up */}
    <div className="lg:grid-cols-3">
```

### Container Pattern
```tsx
<div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
  Content constrained and centered
</div>
```

## Custom Utilities

### Animation Classes
```css
/* index.css */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.animate-fade-in {
  animation: fadeIn 0.3s ease-in-out;
}
```

### Gradient Backgrounds
```tsx
<div className="bg-gradient-to-br from-purple-500 to-pink-500">
  Gradient content
</div>
```

### Glass Effect
```tsx
<div className="backdrop-blur-md bg-white/80 dark:bg-gray-900/80">
  Glass morphism effect
</div>
```

## Best Practices

1. **Use semantic colors** for meaning (green for success, red for errors)
2. **Always include dark mode variants** for new components
3. **Use responsive prefixes** for mobile-first design
4. **Leverage Tailwind's spacing scale** for consistency
5. **Group related utilities** with arbitrary values sparingly

## Troubleshooting

### Styles not applying
- Check Tailwind content configuration
- Verify class name spelling
- Ensure PostCSS is configured

### Dark mode not working
- Verify `darkMode: 'class'` in config
- Check that `dark` class is on HTML element
- Ensure dark variants are used in classes
