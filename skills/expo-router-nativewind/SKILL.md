---
name: expo-router-nativewind
description: Set up or debug Expo Router + NativeWind foundations for React Native / Expo apps, including root layout, safe area, gesture handler, Reanimated, theme wiring, and route structure. Use when scaffolding or fixing the mobile UI base layer.
---

# Expo Router + NativeWind

Use this when the app needs a clean Expo foundation with file-based routing and utility styling.

## Default stack

- Expo latest stable
- Expo Router
- NativeWind
- react-native-safe-area-context
- react-native-gesture-handler
- react-native-reanimated

## Required foundation

### Root layout

- Import `react-native-gesture-handler` first.
- Wrap the app in `GestureHandlerRootView`.
- Wrap the app in `SafeAreaProvider`.
- Mount a top-level `Stack` or route group intentionally.

### Babel

- Include `nativewind/babel`
- Keep `react-native-reanimated/plugin` last

### Tailwind / NativeWind

- Include both `app/**/*` and `src/**/*` globs.
- Keep theme tokens centralized.
- Prefer reusable className patterns over giant one-off strings.

## Route structure defaults

- `app/_layout.tsx` for providers + navigation shell
- `app/(tabs)/` for primary signed-in flows
- `app/auth/` for login/register/forgot-password
- `app/modal/` for modal-only screens

## Common failure checks

- Gesture handler imported too late
- Reanimated plugin not last
- Safe area missing on notch devices
- NativeWind content globs incomplete
- Theme state not persisted or not reflected after relaunch
- File-based routes created without a navigation plan
