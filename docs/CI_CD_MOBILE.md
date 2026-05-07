# Mobile CI/CD Flow

> Mục tiêu: code xong là có quality gate tự động, preview build cho QA, và production build có kiểm soát.

## 1. Local dev

Dùng trên máy dev để test nhanh UI/logic:

```bash
npx expo start
npx expo run:ios
npx expo run:android
```

Đây là chỗ simulator/emulator được dùng trực tiếp.

## 2. GitHub Actions quality gate

Workflow: `.github/workflows/ci.yml`

Trigger:
- pull request vào `main` hoặc `develop`
- push lên `main` hoặc `develop`

Checks mặc định:
- install dependencies
- lint
- typecheck
- unit tests
- integration tests
- Expo doctor
- build sanity check nếu project có script `build`

## 3. Preview build cho QA

Workflow: `.github/workflows/eas-preview.yml`

Mục đích:
- tạo build cloud qua EAS
- gửi link/artifact cho QA hoặc internal testing
- không cần ngồi trên máy dev để build thủ công

Trigger:
- push lên `develop`
- hoặc chạy tay bằng `workflow_dispatch`

Profile khuyến nghị:
- `development`: dev client build
- `preview`: internal QA build

## 4. Production build

Workflow: `.github/workflows/eas-production.yml`

Mục đích:
- build production có kiểm soát
- optional submit store sau khi build xong

Trigger:
- chỉ chạy tay (`workflow_dispatch`)
- gắn với GitHub Environment `production` để có approval nếu muốn

## 5. Secrets cần có trên GitHub

Tối thiểu:
- `EXPO_TOKEN`

Thường sẽ cần thêm ở project thật:
- API base URL theo môi trường
- Sentry auth/token nếu upload sourcemaps
- EAS/Apple/Google credentials tùy cách release

## 6. `eas.json` khuyến nghị

```json
{
  "cli": { "version": ">= 10.0.0" },
  "build": {
    "development": {
      "developmentClient": true,
      "distribution": "internal"
    },
    "preview": {
      "distribution": "internal"
    },
    "production": {}
  },
  "submit": {
    "production": {}
  }
}
```

## 7. Flow em recommend

- Dev local → test trên simulator/emulator
- Push branch/PR → CI check tự chạy
- Merge/push `develop` → EAS preview build
- QA test build preview
- Manual trigger production build → release

## 8. Agent rule of thumb

- simulator/emulator = local dev concern
- EAS preview = QA/internal concern
- EAS production = release concern
- đừng gọi task mobile là xong nếu chưa rõ nó đã qua level nào ở trên
