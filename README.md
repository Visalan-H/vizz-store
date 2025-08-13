# vizz-store

[![npm version](https://img.shields.io/npm/v/vizz-store.svg?style=flat&color=black&labelColor=white)](https://www.npmjs.com/package/vizz-store)

A lightweight React hook that automatically syncs component state with browser localStorage.

## Features

- 🚀 Simple and intuitive API
- 💾 Automatic localStorage synchronization
- 🔄 Real-time state updates
- 🛡️ TypeScript support with full type safety
- 📦 Zero dependencies (except React peer dependency)
- 🏃‍♂️ Lightweight and performant

## Installation

```bash
npm install vizz-store
```

## Usage

### Basic Example

```jsx
import React from 'react';
import { useLocalStorage } from 'vizz-store';

function App() {
  const [isDarkMode, setIsDarkMode] = useLocalStorage('dark-mode', false);

  //Automatically syncs state with localstorage.

  return (
    <div style={{ 
      backgroundColor: isDarkMode ? '#1a1a1a' : '#ffffff',
      color: isDarkMode ? '#ffffff' : '#000000',
      padding: '20px'
    }}>
      <h1>My App</h1>
      <button onClick={() => setIsDarkMode(!isDarkMode)}>
        {isDarkMode ? 'Switch to Light Mode' : 'Switch to Dark Mode'}
      </button>
    </div>
  );
}
```

### TypeScript Example

```tsx
import { useLocalStorage } from 'vizz-store';

type Theme = 'light' | 'dark';

function ThemeToggle() {
  const [theme, setTheme] = useLocalStorage<Theme>('app-theme', 'light');

  //Automatically syncs state with localstorage.

  return (
    <div className={`app ${theme}-theme`}>
      <h2>Current Theme: {theme}</h2>
      <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
        Toggle to {theme === 'light' ? 'Dark' : 'Light'} Mode
      </button>
    </div>
  );
}
```

## API Reference

### `useLocalStorage<T>(key: string, initialValue: T)`

#### Parameters
- `key` - localStorage key to store the value
- `initialValue` - default value if nothing is stored

#### Returns
- `[value, setValue]` - similar to `useState` hook.

```tsx
// Simple usage
const [theme, setTheme] = useLocalStorage('theme', 'light');

// With TypeScript
const [isDark, setIsDark] = useLocalStorage<boolean>('dark-mode', false);
```

#### Features

- **JSON Serialization**: Automatically serializes/deserializes complex objects
- **Type Safety**: Full TypeScript support with generic type parameter

## Browser Compatibility

This hook works in all modern browsers that support:
- React 16.8+ (hooks)
- localStorage API

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT © [Visalan-H](https://github.com/Visalan-H)

## Repository

[https://github.com/Visalan-H/vizz-store](https://github.com/Visalan-H/vizz-store)
