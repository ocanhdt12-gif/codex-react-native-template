---
name: mobile-app-agent
description: Build and refactor React Native / Expo app features with strong mobile architecture, screen composition, navigation, device APIs, offline-aware state, and performance guardrails. Use when implementing mobile screens, flows, hooks, stores, permissions, or app structure.
---

# Mobile App Agent

Prefer Expo-first solutions unless the spec proves native-only work is required.

## Do first

1. Read the current phase/task docs.
2. Identify the flow: auth, CRUD, onboarding, settings, media, notifications, or offline sync.
3. Check whether existing app structure already defines patterns for navigation, state, forms, networking, and storage.
4. Keep edits scoped to the task.

## Architecture defaults

- Organize by feature, not by giant shared folders.
- Keep screens thin; move business logic into hooks/services.
- Split state into:
  - server state → TanStack Query
  - client UI state → Zustand or local component state
  - persisted sensitive state → SecureStore/MMKV wrapper
- Prefer typed adapters around device APIs.
- Handle loading, empty, error, retry, and permission-denied states explicitly.

## Screen checklist

For each new screen or major flow, verify:

- Safe area respected
- Keyboard does not hide key actions
- Back/navigation behavior is clear
- Dark mode does not break readability
- Small-device layout still works
- Network and permission failure states are visible

## Performance rules

- Avoid unnecessary global state.
- Memoize expensive lists/selectors only when measured or obvious.
- Use FlatList/FlashList for long collections.
- Avoid inline anonymous renderers in hot lists unless trivial.
- Keep bridge-heavy or animation-heavy logic isolated.

## Device integration rules

- Prefer Expo modules first.
- Add permission copy and fallback UI before wiring the API.
- Never store auth tokens in plain AsyncStorage.
- Document manual test steps for camera, notifications, biometrics, deep links, or background behavior.

## Done means

Do not call a mobile task done until one of these happened:

- verified on simulator/emulator, or
- blocked by missing runtime/device and the blocker is stated clearly.
