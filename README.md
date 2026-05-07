# 🚀 Codex React Native Template

> Production-ready template để khởi động project mobile mới với Codex.  
> Tích hợp Brainstorming → Design → Plan → Code → Test → Monitor workflow.

---

## ✨ Tại Sao Dùng Template Này?

- **Brainstorm trước, code sau** — design doc được approve trước khi viết dòng code đầu tiên
- **Không mất context** — auto-save/load context qua sessions
- **Không code lung tung** — plan rõ ràng, task nhỏ, test ngay
- **Auto-learn từ mistakes** — continuous learning system
- **Understand codebase** — Graphify knowledge graph
- **Production-ready** — monitoring, error tracking, metrics
- **Mobile-first** — flow tối ưu cho React Native / Expo thay vì web

---

## 📋 Yêu Cầu

- [Codex](https://opencode.ai) đã cài
- `git` đã cài
- `bash` (macOS / Linux / WSL) HOẶC `cmd`/`PowerShell` (Windows)
- `python 3.10+` (cho Graphify)
- `npm` hoặc `pnpm`
- iOS Simulator / Android Emulator / Expo Go trên máy thật
- Khuyến nghị thêm `maestro` cho E2E mobile

---

## 🏁 Bắt Đầu

### Bước 1: Clone template

```bash
git clone https://github.com/ocanhdt12-gif/codex-react-native-template my-project
cd my-project
```

### Bước 2: Chạy script khởi tạo

**Linux / macOS:**
```bash
./scripts/start-project.sh
```

**Windows (CMD):**
```cmd
scripts\start-project.bat
```

**Windows (PowerShell):**
```powershell
.\scripts\start-project.ps1
```

Script hỏi 2 thứ:

```
Step 1/4: Project name
  Tên project: my-awesome-app

Step 2/4: Brain dump ý tưởng
  Bạn muốn nhập từ file không? (y/n) [default: n]: 
```

**Option 1: Nhập từ file** (cho ý tưởng dài)
```
Bạn muốn nhập từ file không? (y/n) [default: n]: y
Đường dẫn file: /path/to/brain-dump.txt
```
→ Script sẽ đọc file và ghi vào `docs/BRIEF.md`

**Option 2: Gõ trực tiếp** (cách cũ)
```
Bạn muốn nhập từ file không? (y/n) [default: n]: n
(Nhấn Enter 2 lần để xong)
```
→ Gõ brain dump trực tiếp

Sau đó script tự:
- Replace tên vào toàn bộ files
- Ghi brain dump → `docs/BRIEF.md`
- Reset git history (fresh repo)

### Bước 3: Mở Codex

```bash
opencode .
```

Codex tự đọc `CODEX.md` → kích hoạt **Phase 0: Brainstorming**:

```
Đọc docs/BRIEF.md
      ↓
Hỏi từng câu một để clarify
      ↓
Propose 2-3 approaches + trade-offs
      ↓
Present design từng section → confirm
      ↓
Viết docs/specs/YYYY-MM-DD-design.md → commit
      ↓
Tự review spec
      ↓
Anh review + approve
      ↓
Phân tích dependency + chia scope
```

┌─── SCOPE BREAKDOWN ─────────────────────────────────────────────────────────┐
│  Chọn cách chia scope:                                                      │
│  - Feature-Based (scope nhỏ)                                                │
│  - Epic-Based (scope lớn, cứng nhắc)                                        │
│  - Dependency-Driven ⭐ (scope lớn, flexible)                              │
│                                                                              │
│  Xem docs/SCOPE_BREAKDOWN.md để chọn                                        │
└──────────────────────────────────────────────────────────────────────────────┘
        ↓
┌─── LAYER 0: FOUNDATION ──────────────────────────────────────────────────────┐
│  (No dependency)                                                             │
│  ┌── TASK LOOP ──────────────────────────────────────────────────────────┐  │
│  │ Pick task từ layer-0-todo.md                                         │  │
│  │ → Code task (1 prompt = 1 task)                                      │  │
│  │ → Viết unit test ngay                                               │  │
│  │ → Chạy test → fix nếu fail                                          │  │
│  │ → Commit + update todo.md                                           │  │
│  │ → Lặp lại                                                           │  │
│  └────────────────────────────────────────────────────────────────────────┘  │
│  Cuối layer: Integration test                                               │
└──────────────────────────────────────────────────────────────────────────────┘
        ↓ (Layer 0 xong → Layer 1 start)
┌─── LAYER 1: CORE FEATURES ───────────────────────────────────────────────────┐
│  (Depends on Layer 0)                                                        │
│  Tương tự Layer 0                                                           │
└──────────────────────────────────────────────────────────────────────────────┘
        ↓
┌─── LAYER 2: SECONDARY ───────────────────────────────────────────────────────┐
│  (Depends on Layer 1)                                                        │
│  Tương tự Layer 0                                                           │
└──────────────────────────────────────────────────────────────────────────────┘
        ↓
┌─── LAYER 3: POLISH + RELEASE ────────────────────────────────────────────────┐
│  (Depends on Layer 2)                                                        │
│  E2E test → fix → deploy staging                                            │
│  Anh review staging → deploy production 🚀                                   │
└──────────────────────────────────────────────────────────────────────────────┘
```

**Lợi ích Dependency-Driven:**
- ✅ Agent không bị block (Layer 0 xong → Layer 1 start)
- ✅ Dễ parallelize (nhiều agent làm layer khác nhau)
- ✅ Flexible (có thể adjust layer nếu cần)
- ✅ Tối ưu timeline/
```

---

## 📱 Mobile E2E & Device Testing

Template dùng **simulator / emulator / real device + Maestro** thay cho browser automation web.

### What is the mobile testing stack?
- Expo app chạy trên iOS / Android runtime thật
- Maestro script để test happy paths end-to-end
- Jest + React Native Testing Library cho screen logic
- adb / xcrun để lấy log, screenshot, debug native issues

### Quick Start
```bash
# Install Maestro
curl -Ls "https://get.maestro.mobile.dev" | bash
maestro --version

# Start Expo app
npx expo start

# Run smoke flow
maestro test .maestro/login-flow.yaml
```

### Usage
- Phase 4: E2E testing trước release
- Test user flows (onboarding, login, create, edit, delete)
- Check permissions, deep links, offline states, keyboard, safe area
- Capture screenshots / logs khi có bug

Xem `docs/MOBILE_E2E.md` để full guide.

---

## 🗂️ Cấu Trúc Project

```
my-project/
│
├── CODEX.md                      ← 🔑 Source of truth cho Codex
│
├── docs/
│   ├── BRIEF.md                   ← Brain dump ban đầu
│   ├── MONITORING.md              ← Sentry + Prometheus + Grafana setup
│   ├── MEMORY_HOOKS.md            ← Auto-save/load context
│   ├── CONTINUOUS_LEARNING.md     ← Auto-extract patterns
│   ├── GRAPHIFY.md                ← Knowledge graph builder
│   ├── MOBILE_E2E.md              ← Device testing + release checklist
│   ├── specs/                     ← Design docs (output của brainstorming)
│   │   └── YYYY-MM-DD-[topic]-design.md
│   └── phases/
│       ├── phase-0.md             ← Brainstorming instructions
│       ├── phase-1.md             ← Foundation
│       ├── phase-2.md             ← Core Features
│       ├── phase-3.md             ← UI + Polish
│       └── phase-4.md             ← Testing + Release
│
├── skills/
│   ├── brainstorming/
│   │   └── SKILL.md               ← Reusable brainstorming workflow
│   ├── mobile-app-agent/
│   │   └── SKILL.md               ← Mobile architecture + implementation patterns
│   ├── expo-router-nativewind/
│   │   └── SKILL.md               ← Expo Router + NativeWind foundation
│   ├── mobile-auth-state/
│   │   └── SKILL.md               ← Auth, secure storage, protected routes
│   ├── mobile-data-forms/
│   │   └── SKILL.md               ← Query, mutation, forms, validation patterns
│   ├── mobile-api-integration/
│   │   └── SKILL.md               ← Typed client, auth, pagination, upload, errors
│   ├── mobile-testing-release/
│   │   └── SKILL.md               ← Testing pyramid + release gate
│   ├── expo-eas-pipeline/
│   │   └── SKILL.md               ← EAS build profiles, CI, release pipeline
│   ├── mobile-i18n-theme/
│   │   └── SKILL.md               ← Localization + theme rules
│   └── boilerplate/
│       └── react-native-expo/
│           └── BOILERPLATE.md     ← Expo bootstrap reference
│
├── memory/                        ← Auto-save context từ sessions
│   └── .gitkeep
│
├── .learnings/                    ← Auto-extract patterns + lessons
│   └── .gitkeep
│
├── tasks/
│   ├── todo.md                    ← Task hiện tại + up next
│   └── done.md                    ← Log tasks đã xong
│
├── app/                           ← Expo Router entry screens
├── src/                           ← Shared source code
├── tests/
│   ├── unit/                      ← Viết cùng lúc với code
│   ├── integration/               ← Viết cuối mỗi phase
│   └── e2e/                       ← Viết trước release
│
├── scripts/
│   └── start-project.sh           ← Script khởi tạo project
│
├── .github/
│   └── workflows/ci.yml           ← CI pipeline
│
├── docker-compose.monitoring.yml  ← Prometheus + Grafana
├── prometheus.yml                 ← Prometheus config
├── .env.example                   ← Env vars template
└── .gitignore
```

---

## 🔄 Full Dev Process

```
./scripts/start-project.sh
  → Nhập tên + brain dump
  → docs/BRIEF.md tạo xong
        ↓
opencode .
        ↓
┌─── PHASE 0: BRAINSTORMING ─────────────────────────┐
│  Đọc BRIEF → clarify từng câu một                  │
│  Propose 2-3 approaches                            │
│  Present design → confirm từng section             │
│  Viết docs/specs/YYYY-MM-DD-design.md              │
│  Tự review → user approve                          │
│  Chia phases + tạo tasks/todo.md                   │
└─────────────────────────────────────────────────────┘
        ↓
┌─── PHASE 1-3: DEVELOPMENT ─────────────────────────┐
│                                                    │
│  ┌── TASK LOOP ──────────────────────────────┐    │
│  │ Pick task từ todo.md                      │    │
│  │ → Code task (1 prompt = 1 task)           │    │
│  │ → Viết unit test ngay                     │    │
│  │ → Chạy test → fix nếu fail                │    │
│  │ → Verify trên simulator / emulator        │    │
│  │ → Commit + update todo.md                 │    │
│  │ → Lặp lại                                 │    │
│  └───────────────────────────────────────────┘    │
│                                                    │
│  Cuối mỗi phase: Integration test                  │
│  Review memory/ + .learnings/ để tránh lỗi cũ      │
└─────────────────────────────────────────────────────┘
        ↓
┌─── PHASE 4: RELEASE ───────────────────────────────┐
│  E2E mobile test → internal build → QA            │
│  Anh review build → release production 🚀         │
└─────────────────────────────────────────────────────┘
```

---

## 🚦 Mobile CI/CD Flow

Template này dùng 3 lớp verify:

1. **Local simulator/emulator** — dev test trực tiếp trên máy
2. **GitHub Actions CI** — lint, typecheck, tests, Expo doctor
3. **EAS cloud builds** — preview build cho QA và production build cho release

Files chính:
- `.github/workflows/ci.yml`
- `.github/workflows/eas-preview.yml`
- `.github/workflows/eas-production.yml`
- `docs/CI_CD_MOBILE.md`

> CI/CD mobile không tự build thẳng lên simulator máy anh; nó build artifact/link trên cloud. Simulator vẫn là bước local dev.

---

## 📊 Scope Breakdown (Yêu cầu lớn)

Khi scope lớn, template hỗ trợ 3 cách chia scope:

1. **Feature-Based** — Chia theo feature (dễ hiểu, nhưng khó parallelize)
2. **Epic-Based** — Chia theo phase (rõ ràng, nhưng cứng nhắc)
3. **Dependency-Driven** ⭐ — Chia theo dependency layer (tối ưu timeline, dễ parallelize)

Xem `docs/SCOPE_BREAKDOWN.md` để chọn cách phù hợp.

**Lưu ý:** Template ví dụ dùng 4 layers (0-3), nhưng hoàn toàn flexible — agent/team có thể tự chia thêm layer nếu cần (Layer 4, 5, 6...), miễn là không vi phạm quy tắc: **Layer N chỉ depend on Layer 0 → N-1**.

---

## 🧠 Memory & Learning

### Memory Hooks
Auto-save/load context qua sessions:
- Session end: save → `memory/YYYY-MM-DD.md`
- Session start: load từ `memory/`
- Xem `docs/MEMORY_HOOKS.md` để setup

### Continuous Learning
Auto-extract patterns + lessons:
- Extract → `.learnings/YYYY-MM-DD-[topic].md`
- Promote → AGENTS.md / TOOLS.md khi validated
- Tránh lỗi cũ lần sau
- Xem `docs/CONTINUOUS_LEARNING.md` để setup

---

## 📊 Knowledge Graph (Graphify)

Auto-generate knowledge graph từ codebase:

```bash
# Install
pip install graphifyy

# Generate graph
graphify ./src

# Output
graphify-out/
  ├── graph.html              # Interactive visualization
  ├── GRAPH_REPORT.md         # Core nodes + surprises
  ├── graph.json              # Queryable graph (for Codex)
  └── cache/
```

**Usage:**
- Review `GRAPH_REPORT.md` sau major changes
- Open `graph.html` để explore architecture
- Codex reads `graph.json` để hiểu structure
- Run trước release để catch architecture drift

Xem `docs/GRAPHIFY.md` để full guide.

---

## 📊 Monitoring

Production-ready monitoring stack:

### Tools
- **Sentry** — Error tracking + source maps
- **Prometheus** — Metrics collection
- **Grafana** — Metrics visualization

### Quick Start

**1. Setup Sentry**
```bash
# Tạo account: https://sentry.io
# Lấy DSN → .env
SENTRY_DSN=https://xxx@xxx.ingest.sentry.io/xxx
```

**2. Start Prometheus + Grafana**
```bash
docker-compose -f docker-compose.monitoring.yml up -d

# Access
# Prometheus: http://localhost:9090
# Grafana: http://localhost:3000 (admin/admin)
```

**3. Full Guide**
Xem `docs/MONITORING.md` để:
- Init Sentry trong Node.js backend + React Native / Expo app
- Setup Prometheus metrics
- Create Grafana dashboards
- Release production an toàn hơn

---

## 🧠 Brainstorming Skill (Thêm Feature Mới)

Khi project đang chạy và muốn thêm feature mới:

```
"Đọc skills/brainstorming/SKILL.md và brainstorm feature sau:
[Mô tả feature muốn thêm]"
```

Skill sẽ tự động:
1. Explore context hiện tại
2. Hỏi từng câu để clarify
3. Propose 2-3 approaches
4. Viết design doc mới vào `docs/specs/`
5. Tạo tasks cho feature đó

---

## 🧩 Skill Map

| Skill | Dùng khi nào |
|------|---------------|
| `mobile-app-agent` | build screen/flow, refactor feature, device API integration |
| `expo-router-nativewind` | setup hoặc fix routing + NativeWind foundation |
| `mobile-auth-state` | login/logout, session restore, protected routes |
| `mobile-data-forms` | query/mutation, form submit, validation, retry/offline |
| `mobile-api-integration` | connect app với backend API, auth header, refresh, pagination, upload |
| `mobile-testing-release` | thêm test, verify feature trước merge/release |
| `expo-eas-pipeline` | setup EAS, env, preview/prod build, CI |
| `mobile-i18n-theme` | đa ngôn ngữ, dark mode, token/theme consistency |

---

## 🧪 Testing Strategy

| Loại | Khi nào viết | Tool |
|------|-------------|------|
| **Unit** | Ngay sau mỗi task | Jest |
| **Integration** | Cuối mỗi phase | Jest + React Native Testing Library |
| **E2E** | Trước release | Maestro |

---

## 📌 Rules Vàng

| Rule | Lý do |
|------|-------|
| Brainstorm trước khi code | Tránh build sai thứ |
| Design doc phải được approve | Hard gate, không skip |
| `CODEX.md` là source of truth | Codex đọc đầu tiên |
| 1 prompt = 1 task | Context nhỏ → output tốt |
| Test viết ngay, không để cuối | Tránh bug chồng bug |
| Commit sau mỗi task | Rollback dễ |
| Review memory/ + learnings/ | Tránh lỗi cũ |
| **Phase 0: Dùng GPT-5.5** | Brainstorming tốt hơn |

| **Verify trên device/runtime** | Mobile bug không lộ hết nếu chỉ đọc code |

---

## 📝 Prompt Templates

### Bắt đầu task mới
```
Đọc CODEX.md → docs/phases/phase-N.md → tasks/todo.md

Implement task "In Progress".
Chỉ sửa files được liệt kê trong task.

Sau khi xong:
1. Viết unit test
2. Chạy test, fix nếu fail
3. Verify trên simulator / emulator hoặc document rõ blocker
4. Commit: feat/fix/test: [mô tả ngắn]
5. Move task sang done.md
6. Báo kết quả ngắn gọn
```

### Thêm feature mới
```
Đọc skills/brainstorming/SKILL.md và brainstorm feature sau:
[Mô tả feature]
```

### Generate knowledge graph
```bash
graphify ./src
# Review graphify-out/GRAPH_REPORT.md
```

---

## 🔗 Resources

- **Brainstorming Skill:** `skills/brainstorming/SKILL.md`
- **Mobile App Agent:** `skills/mobile-app-agent/SKILL.md`
- **Expo Boilerplate:** `skills/boilerplate/react-native-expo/BOILERPLATE.md`
- **Mobile E2E:** `docs/MOBILE_E2E.md`
- **Mobile CI/CD:** `docs/CI_CD_MOBILE.md`
- **Memory Hooks:** `docs/MEMORY_HOOKS.md`
- **Continuous Learning:** `docs/CONTINUOUS_LEARNING.md`
- **Graphify:** `docs/GRAPHIFY.md`
- **Monitoring:** `docs/MONITORING.md`

---

## 📜 License

MIT
