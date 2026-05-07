# React Native / Expo Boilerplate

> **Chỉ dùng file này khi project stack là React Native / Expo mobile app.**
> Nếu project là web app, Node.js API thuần, Python, hoặc stack khác → bỏ qua folder này.

## Khi Nào Activate

AI sẽ tự động dùng boilerplate này khi:
- User nói "tạo app mobile", "React Native", "Expo", "iOS/Android"
- `docs/BRIEF.md` hoặc spec mention mobile app / native app / cross-platform app
- Stack được chọn trong Phase 0 là React Native-based

## Stack Mặc Định (React Native / Expo Projects)

```
Expo (latest stable) + React Native
TypeScript (strict mode)
Expo Router
NativeWind
Zustand (client state)
TanStack Query (server state)
Jest + React Native Testing Library
ESLint + Prettier
Sentry + Expo / native monitoring hooks
```

## Folder Structure

```
app/
├── _layout.tsx              # Expo Router root layout
├── (tabs)/                  # Main tab flows
├── auth/                    # Login / register / forgot password
└── modal/                   # Modal screens

src/
├── components/              # Reusable UI components
├── features/                # Feature modules
├── hooks/                   # Custom hooks
├── lib/                     # API client, utils, constants
├── providers/               # Query/theme/auth providers
├── store/                   # Zustand stores
├── types/                   # TypeScript type definitions
└── __tests__/               # Test helpers + specs
```

## Setup Commands

```bash
# 1. Create Expo app
npx create-expo-app@latest . -t blank-typescript

# 2. Core navigation + native deps
npx expo install expo-router react-native-safe-area-context react-native-screens react-native-gesture-handler react-native-reanimated react-native-svg expo-secure-store expo-splash-screen expo-font

# 3. State + styling
pnpm add zustand @tanstack/react-query nativewind tailwindcss
npx nativewind@latest init

# 4. Testing
pnpm add -D jest-expo @testing-library/react-native @testing-library/jest-native

# 5. Optional production extras
npx expo install expo-notifications expo-linking expo-localization
```

## Key Config Files

### tsconfig.json (strict mode)
```json
{
  "compilerOptions": {
    "strict": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true,
    "noImplicitReturns": true,
    "paths": { "@/*": ["./src/*"] }
  }
}
```

### babel.config.js
```js
module.exports = function (api) {
  api.cache(true)
  return {
    presets: ['babel-preset-expo'],
    plugins: ['nativewind/babel', 'react-native-reanimated/plugin'],
  }
}
```

### tailwind.config.js
```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./app/**/*.{ts,tsx}', './src/**/*.{ts,tsx}'],
  presets: [require('nativewind/preset')],
  theme: { extend: {} },
  plugins: [],
}
```

### app/_layout.tsx
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

## Skills Liên Quan

Khi dùng boilerplate này, các skill sau sẽ tự động áp dụng:
- `skills/mobile-app-agent/SKILL.md` — screen patterns, mobile architecture
- `skills/typescript/SKILL.md` — type safety rules
- `skills/expo-router-nativewind/SKILL.md` — Expo Router + NativeWind setup rules

## Checklist Trước Khi Code

- [ ] `pnpm install` chạy thành công
- [ ] `npx expo start` khởi động được
- [ ] `npx expo-doctor` không báo lỗi critical
- [ ] TypeScript strict mode bật
- [ ] Babel + Reanimated config đúng
- [ ] NativeWind className hoạt động trong app
- [ ] Root layout có safe area + gesture handler
