# Mobile E2E — Device Testing & Release Confidence

> Dùng guide này cho React Native / Expo apps khi cần test flow thật trên simulator, emulator, hoặc máy thật trước release.

## 🎯 Goal

- Verify flow chính trên mobile thay vì browser
- Check permissions, deep links, notifications, keyboard, safe area
- Capture logs / screenshots / videos khi bug xảy ra
- Chuẩn bị internal build trước khi release production

## Stack Khuyến Nghị

### 1. Fast local loop
- `npx expo start`
- Expo Go hoặc dev build
- iOS Simulator / Android Emulator

### 2. Scripted E2E
- **Maestro** cho happy paths + smoke tests
- **Jest + React Native Testing Library** cho screen logic / hooks
- **Optional Detox** khi cần native-level assertions sâu hơn

## Quick Start

### Install Maestro
```bash
curl -Ls "https://get.maestro.mobile.dev" | bash
maestro --version
```

### Run app
```bash
npx expo start
# hoặc build dev client nếu app dùng native modules riêng
```

### Sample Maestro flow
```yaml
appId: com.example.app
---
- launchApp
- tapOn: "Đăng nhập"
- inputText: "user@example.com"
- tapOn: "Tiếp tục"
- assertVisible: "Trang chủ"
```

### Run test
```bash
maestro test .maestro/login-flow.yaml
```

## Test Checklist Trước Release

### Core flows
- [ ] Onboarding / auth
- [ ] CRUD chính của app
- [ ] Empty / loading / error states
- [ ] Logout + token refresh

### Mobile-specific checks
- [ ] iOS + Android permission prompts
- [ ] Keyboard không che CTA quan trọng
- [ ] Safe area đúng ở notch + small devices
- [ ] Dark mode / light mode ổn
- [ ] Offline / flaky network behavior có xử lý
- [ ] Deep link / push notification mở đúng screen

## Debugging Toolkit

### Android
```bash
adb logcat | grep -iE "ReactNative|Expo|your-app"
adb shell screencap -p /sdcard/screen.png
adb pull /sdcard/screen.png .
```

### iOS Simulator
```bash
xcrun simctl list devices
xcrun simctl io booted screenshot screenshot.png
xcrun simctl spawn booted log stream --predicate 'processImagePath contains "YourApp"'
```

## Release Flow

1. Chạy unit + integration tests
2. Chạy Maestro smoke suite
3. Tạo internal build (EAS / CI artifact)
4. QA trên ít nhất 1 iPhone + 1 Android device profile
5. Fix blockers rồi mới release production

## Notes

- Nếu app phụ thuộc native SDK khó mock, ưu tiên dev build thay vì Expo Go
- Document manual steps cho camera, biometrics, push notifications
- Không claim “done” nếu chưa verify trên ít nhất 1 mobile runtime thật
