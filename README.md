# Firebase Studio

This is a NextJS starter in Firebase Studio.

To get started, take a look at src/app/page.tsx.
# QuestForge AI - LocalStorage Integration

This repository contains the localStorage integration for QuestForge AI, a tool for DMs and writers to generate rich, dynamic quests and NPCs using guided AI tools.

## Features

- **Type-safe localStorage Utilities**: Secure and type-safe wrapper around browser's localStorage API
- **React Hooks**: Easy-to-use React hooks for localStorage integration
- **Theme Persistence**: Toggle between light and dark themes with automatic preference saving
- **User Preferences**: Store and retrieve user preferences for AI settings, genre preferences, and more

## Directory Structure

```
src/
├── utils/
│   └── localStorage.ts - Core utility functions
├── hooks/
│   └── useLocalStorage.ts - React hook for localStorage
├── components/
│   ├── ThemeToggle.tsx - Theme switching component
│   └── UserPreferences.tsx - User preferences component
└── app/
    └── layout.tsx - Example layout integration
```

## Integration Guide

See the [localStorage Integration Guide](./localStorage-integration-guide.md) for detailed instructions on how to integrate these components into your QuestForge AI project.

## Usage Examples

### Using the localStorage Hook

```tsx
"use client";

import { useLocalStorage } from '@/hooks/useLocalStorage';

export function YourComponent() {
  // Store data with localStorage persistence
  const [data, setData] = useLocalStorage('your-key', defaultValue);
  
  // Use like regular React state
  const updateData = () => {
    setData(newValue);
  };
  
  return (
    // Your component JSX
  );
}
```

### Direct localStorage Access

```typescript
import { setStorageItem, getStorageItem } from '@/utils/localStorage';

// Save data
setStorageItem('your-key', yourData);

// Get data
const data = getStorageItem('your-key', defaultValue);
```

## Requirements

- Next.js 13+ with App Router
- React 18+
- TypeScript
