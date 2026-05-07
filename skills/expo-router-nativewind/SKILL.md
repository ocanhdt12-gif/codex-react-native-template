---
name: Expo Router NativeWind
slug: expo-router-nativewind
version: 1.0.0
description: Production-tested Expo + React Native stack with Expo Router, NativeWind, safe-area, gesture-handler, and Reanimated. Use when scaffolding or debugging a mobile UI foundation for React Native / Expo apps.
---

# Expo Router + NativeWind Stack

## When to Use

Activate when setting up or debugging a React Native / Expo app that needs file-based routing, typed navigation, utility-first styling, dark mode, and common mobile foundation libraries.

**Trigger keywords:** react native, expo, expo router, nativewind, reanimated, gesture handler, safe area, splash screen, deep linking.

## Quick Start

```bash
# 1. Create Expo app
npx create-expo-app@latest . -t blank-typescript

# 2. Core app dependencies
npx expo install expo-router react-native-safe-area-context react-native-screens react-native-gesture-handler react-native-reanimated react-native-svg
pnpm add nativewind tailwindcss zustand @tanstack/react-query

# 3. Testing
pnpm add -D jest-expo @testing-library/react-native @testing-library/jest-native

# 4. NativeWind init
npx nativewind@latest init
```

## app/_layout.tsx (required shape)

```tsx
import 'react-native-gesture-handler'
import { Stack } from 'expo-router'
import { GestureHandlerRootView } from 'react-native-gesture-handler'
import { SafeAreaProvider } from 'react-native-safe-area-context'

export default function RootLayout() {
  return (
    <GestureHandlerRootView style={{ flex: 1 }}>
      <SafeAreaProvider>
        <Stack screenOptions={{ headerShown: false }} />
      </SafeAreaProvider>
    </GestureHandlerRootView>
  )
}
```

## babel.config.js (critical)

```js
module.exports = function (api) {
  api.cache(true)
  return {
    presets: ['babel-preset-expo'],
    plugins: ['nativewind/babel', 'react-native-reanimated/plugin'],
  }
}
```

## tailwind.config.js

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./app/**/*.{ts,tsx}', './src/**/*.{ts,tsx}'],
  presets: [require('nativewind/preset')],
  theme: { extend: {} },
  plugins: [],
}
```

## 8 Common Errors to Avoid

1. **Reanimated plugin must be last** in Babel plugins
2. **Import `react-native-gesture-handler` first** in root layout / entry file
3. **Wrap app with `GestureHandlerRootView`** or gestures break silently
4. **Always use `SafeAreaProvider`** for notches / status bars
5. **NativeWind content globs must include both `app/` and `src/`**
6. **Do not store auth tokens in AsyncStorage** — use SecureStore / Keychain
7. **Configure deep linking early** if auth or notifications open screens
8. **Test dark mode + keyboard overlap on small devices** before shipping

## Dark Mode

```tsx
import { useColorScheme } from 'react-native'

const scheme = useColorScheme()
const isDark = scheme === 'dark'
```

## Verified Foundation

- Expo Router
- NativeWind
- React Native Reanimated
- React Native Gesture Handler
- Safe Area Context
