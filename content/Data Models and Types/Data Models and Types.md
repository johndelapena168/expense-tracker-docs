# Data Models and Types

This document provides an overview of the data models and types used in the application.

## Overview

The application uses TypeScript interfaces to define data structures for:
- Expenses
- Categories
- Currency
- Payment methods

## Type Safety

All data models are defined as TypeScript interfaces with:
- Strict typing
- Required vs optional fields
- Union types for enumerations
- Nested object types

## Persistence

Data is persisted to localStorage as JSON:
- Automatic serialization/deserialization
- Type guards for validation
- Default values for missing data

See detailed documentation:
- [Category Entity](Category%20Entity.md)
- [Expense Entity](Expense%20Entity.md)
- [Type Definitions and Validation](Type%20Definitions%20and%20Validation.md)
