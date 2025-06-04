# Integration Guide for localStorage in QuestForge AI

This guide explains how to integrate the localStorage functionality into your QuestForge AI project.

## Files Overview

I've created the following files for you:

1. **utils/localStorage.ts** - Core utility functions for localStorage operations
2. **hooks/useLocalStorage.ts** - React hook for easy localStorage usage in components
3. **components/ThemeToggle.tsx** - Component for theme switching with localStorage persistence
4. **components/UserPreferences.tsx** - Component for storing user preferences in localStorage

## Integration Steps

### 1. Create the Directory Structure

First, make sure you have these directories in your project:

```
src/
├── utils/
├── hooks/
└── components/
```

### 2. Copy the Files

Copy each file to its respective directory in your project:

- `utils/localStorage.ts` → `src/utils/localStorage.ts`
- `hooks/useLocalStorage.ts` → `src/hooks/useLocalStorage.ts`
- `components/ThemeToggle.tsx` → `src/components/ThemeToggle.tsx`
- `components/UserPreferences.tsx` → `src/components/UserPreferences.tsx`

### 3. Add Theme Toggle to Layout

Modify your layout.tsx file to include the ThemeToggle component in the header:

```tsx
// Import at the top of your layout.tsx file
import { ThemeToggle } from '@/components/ThemeToggle';

// Then add it to your header section
<header className="sticky top-0 z-10 flex h-14 items-center gap-4 border-b bg-background/80 px-4 backdrop-blur-md sm:static sm:h-auto sm:border-0 sm:bg-transparent sm:px-6 sm:py-4">
  <SidebarTrigger className="sm:hidden" />
  {/* Add ThemeToggle here */}
  <div className="ml-auto">
    <ThemeToggle />
  </div>
  {/* Breadcrumbs or Page Title can go here */}
</header>
```

### 4. Update HTML Class for Theme Support

Modify your layout.tsx to use the theme from localStorage instead of hardcoding "dark":

```tsx
// Change this line in your RootLayout component:
<html lang="en" className="dark">

// To this (which will be dynamically updated by ThemeToggle):
<html lang="en">
```

### 5. Add UserPreferences to Settings Page

Add the UserPreferences component to your settings page:

```tsx
// In your settings page file (e.g., src/app/settings/page.tsx)
import { UserPreferences } from '@/components/UserPreferences';

export default function SettingsPage() {
  return (
    <div className="space-y-6">
      <h1 className="text-2xl font-bold">Settings</h1>
      <UserPreferences />
      {/* Other settings components */}
    </div>
  );
}
```

## Usage Examples

### Using localStorage in Your Components

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

## Troubleshooting

1. **"use client" Directive**: Ensure all components using React hooks have the "use client" directive at the top of the file.

2. **Import Paths**: Make sure import paths match your project structure. If you're not using the @/ alias, adjust imports accordingly.

3. **Hydration Errors**: If you see hydration errors, check that components using localStorage are properly handling the SSR case (as done in ThemeToggle).

4. **TypeScript Errors**: If you encounter TypeScript errors, ensure your tsconfig.json includes the proper paths and settings.
