# App Context

This document describes the AppContext for global settings.

## Purpose

Manages application-wide settings:
- Currency selection
- Dark mode toggle
- Amount formatting

## Interface

```typescript
interface AppContextType {
  currency: Currency;
  setCurrency: (code: string) => void;
  darkMode: boolean;
  setDarkMode: (enabled: boolean) => void;
  formatAmount: (amount: number) => string;
}

interface Currency {
  code: string;
  symbol: string;
  name: string;
}
```

## Usage

```typescript
const { currency, setCurrency, darkMode, setDarkMode, formatAmount } = useApp();
```

## Persistence

Stored in localStorage:
- `expense-tracker-currency`: Currency code
- `expense-tracker-darkMode`: Boolean

## Dark Mode

When darkMode changes:
1. State updated
2. localStorage persisted
3. Document class toggled

```typescript
useEffect(() => {
  if (darkMode) {
    document.documentElement.classList.add('dark');
  } else {
    document.documentElement.classList.remove('dark');
  }
}, [darkMode]);
```

## Format Amount

Formats numbers with currency symbol:

```typescript
const formatAmount = (amount: number): string => {
  return `${currency.symbol}${amount.toFixed(2)}`;
};
```

## Supported Currencies

- USD ($) - US Dollar
- PHP (₱) - Philippine Peso
- EUR (€) - Euro
- GBP (£) - British Pound
- JPY (¥) - Japanese Yen
- SGD (S$) - Singapore Dollar
- AUD (A$) - Australian Dollar
- CAD (C$) - Canadian Dollar
