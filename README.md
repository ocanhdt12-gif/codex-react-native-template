# 🚀 Codex React Native Template

> Production-ready template để khởi động project mobile mới với Codex + Expo.  
> Tích hợp Brainstorming → Design → Scope Breakdown → Code → Test → Monitor workflow.

---

## ✨ Tại Sao Dùng Template Này?

- **Brainstorm trước, code sau** — design doc được approve trước khi viết dòng code đầu tiên
- **Scope breakdown tối ưu** — 3 cách chia scope (Feature-Based, Epic-Based, Dependency-Driven)
- **Không mất context** — auto-save/load context qua sessions
- **Không code lung tung** — plan rõ ràng, task nhỏ, test ngay
- **Auto-learn từ mistakes** — continuous learning system
- **Understand codebase** — Graphify knowledge graph
- **Production-ready** — monitoring, error tracking, metrics, CI/CD
- **Mobile-first** — Expo Router + NativeWind + EAS build pipeline

---

## 📋 Yêu Cầu

- [Codex](https://opencode.ai) đã cài
- `git` đã cài
- `bash` (macOS / Linux / WSL) HOẶC `cmd`/`PowerShell` (Windows)
- `npm` hoặc `pnpm`
- `eas-cli` (cho EAS builds): `npm install -g eas-cli`
- Expo account (free): https://expo.dev

---

## 🏁 Bắt Đầu

### Bước 1: Clone template

```bash
git clone https://github.com/ocanhdt12-gif/codex-react-native-template my-app
cd my-app
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

**Option 2: Gõ trực tiếp** (cách cũ)
```
Bạn muốn nhập từ file không? (y/n) [default: n]: n
(Nhấn Enter 2 lần để xong)
```

Sau đó script tự:
- Replace tên vào toàn bộ files
- Ghi brain dump → `docs/BRIEF.md`
- Reset git history (fresh repo)

### Bước 3: Mở Codex

```bash
codex .
```

Codex tự đọc `CODEX.md` → kích hoạt **Brainstorming Phase**.

---

## 🗂️ Cấu Trúc Project

```
my-app/
│
├── CODEX.md                       ← 🔑 Source of truth cho Codex
│
├── docs/
│   ├── BRIEF.md                   ← Brain dump ban đầu
│   ├── SCOPE_BREAKDOWN.md         ← 3 cách chia scope
│   ├── MONITORING.md              ← Sentry + Prometheus + Grafana
│   ├── MEMORY_HOOKS.md            ← Auto-save/load context
│   ├── CONTINUOUS_LEARNING.md     ← Auto-extract patterns
│   ├── GRAPHIFY.md                ← Knowledge graph builder
│   ├── CI_CD_MOBILE.md            ← Mobile CI/CD + EAS flow
│   ├── MOBILE_E2E.md              ← Device testing + release checklist
│   ├── specs/                     ← Design docs (output của brainstorming)
│   │   └── YYYY-MM-DD-[topic]-design.md
│   └── phases/
│       └── phase-0.md             ← Brainstorming instructions
│
├── skills/
│   └── brainstorming/
│       └── SKILL.md               ← Reusable brainstorming workflow
│
├── memory/                        ← Auto-save context từ sessions
│   └── .gitkeep
│
├── .learnings/                    ← Auto-extract patterns + lessons
│   └── .gitkeep
│
├── tasks/
│   ├── todo.md                    ← Task hiện tại + up next
│   ├── done.md                    ← Log tasks đã xong
│   ├── layer-0-todo.md            ← Layer 0 tasks (nếu dùng Dependency-Driven)
│   ├── layer-1-todo.md            ← Layer 1 tasks
│   ├── layer-2-todo.md            ← Layer 2 tasks
│   └── layer-3-todo.md            ← Layer 3 tasks (hoặc thêm layer nếu cần)
│
├── app/                           ← Expo Router entry screens
├── src/                           ← Shared source code
│
├── tests/
│   ├── unit/                      ← Viết cùng lúc với code
│   ├── integration/               ← Viết cuối mỗi layer
│   └── e2e/                       ← Viết trước release
│
├── scripts/
│   ├── start-project.sh           ← Script khởi tạo project
│   ├── start-project.bat          ← Windows CMD version
│   └── start-project.ps1          ← Windows PowerShell version
│
├── .github/
│   └── workflows/
│       ├── ci.yml                 ← Quality gate (lint, typecheck, test, build)
│       ├── eas-preview.yml        ← EAS preview build
│       └── eas-production.yml     ← EAS production build
│
├── eas.json                       ← EAS build profiles
├── app.config.ts                  ← Expo app config
├── .env.example                   ← Env vars template
└── .gitignore
```

**Lưu ý:** Folder structure linh hoạt tùy cách chia scope:
- **Feature-Based:** dùng `tasks/todo.md` chung
- **Epic-Based:** dùng `tasks/epic-1-todo.md`, `tasks/epic-2-todo.md`, etc.
- **Dependency-Driven:** dùng `tasks/layer-0-todo.md`, `tasks/layer-1-todo.md`, etc.

---

## 🔄 Full Dev Process

```
./scripts/start-project.sh
  → Nhập tên + brain dump
  → docs/BRIEF.md tạo xong
        ↓
codex .
        ↓
┌─── PHASE 0: BRAINSTORMING ────────────────────────┐
│  Đọc BRIEF → clarify từng câu một                 │
│  Propose 2-3 approaches + trade-offs              │
│  Present design → confirm từng section            │
│  Viết docs/specs/YYYY-MM-DD-design.md            │
│  Tự review → user approve                        │
│  Phân tích dependency + chia scope                │
└───────────────────────────────────────────────────┘
        ↓
┌─── SCOPE BREAKDOWN ───────────────────────────────┐
│  Chọn cách chia scope:                            │
│  - Feature-Based (scope nhỏ)                      │
│  - Epic-Based (scope lớn, cứng nhắc)             │
│  - Dependency-Driven ⭐ (scope lớn, flexible)    │
│                                                   │
│  Xem docs/SCOPE_BREAKDOWN.md để chọn             │
└───────────────────────────────────────────────────┘
        ↓
┌─── LAYER 0: FOUNDATION ───────────────────────────┐
│  (No dependency)                                  │
│  ┌── TASK LOOP ──────────────────────────────┐   │
│  │ Pick task từ layer-0-todo.md              │   │
│  │ → Code task (1 prompt = 1 task)           │   │
│  │ → Viết unit test ngay                    │   │
│  │ → Chạy test → fix nếu fail               │   │
│  │ → Commit + update todo.md                │   │
│  │ → Lặp lại                                │   │
│  └───────────────────────────────────────────┘   │
│  Cuối layer: Integration test                     │
└───────────────────────────────────────────────────┘
        ↓ (Layer 0 xong → Layer 1 start)
┌─── LAYER 1: CORE FEATURES ────────────────────────┐
│  (Depends on Layer 0)                             │
│  Tương tự Layer 0                                 │
└───────────────────────────────────────────────────┘
        ↓
┌─── LAYER 2: SECONDARY ────────────────────────────┐
│  (Depends on Layer 1)                             │
│  Tương tự Layer 0                                 │
└───────────────────────────────────────────────────┘
        ↓
┌─── LAYER 3: POLISH + RELEASE ─────────────────────┐
│  (Depends on Layer 2)                             │
│  Device testing → fix → EAS preview build        │
│  User review → EAS production build 🚀           │
└───────────────────────────────────────────────────┘
```

**Lợi ích Dependency-Driven:**
- ✅ Agent không bị block (Layer 0 xong → Layer 1 start)
- ✅ Dễ parallelize (nhiều agent làm layer khác nhau)
- ✅ Flexible (có thể adjust layer nếu cần)
- ✅ Tối ưu timeline

---

## 📊 Scope Breakdown

Khi scope lớn, template hỗ trợ 3 cách chia scope:

### 1. Feature-Based
- Chia theo feature/user story
- Ưu: Dễ hiểu, dễ demo
- Nhược: Khó parallelize, có thể bị block
- Dùng khi: Scope nhỏ (< 10 features), features độc lập

### 2. Epic-Based
- Chia theo Epic → Stories, theo phase
- Ưu: Rõ ràng, dễ track progress
- Nhược: Cứng nhắc, khó adjust
- Dùng khi: Scope lớn (> 15 features), timeline cố định

### 3. Dependency-Driven ⭐ (Recommended)
- Chia theo dependency layer (Layer 0 → 1 → 2 → 3 → ...)
- Layer 0: Foundation (no dependency)
- Layer N: Depends on Layer 0 → N-1
- Ưu: Không block, dễ parallelize, flexible, tối ưu timeline
- Nhược: Cần phân tích dependency kỹ
- Dùng khi: Scope lớn, cần parallelize, nhiều agent/team

**QUAN TRỌNG:** Layer count flexible — có thể chia 4, 5, 6+ layers tùy scope, miễn là không vi phạm quy tắc dependency.

Xem `docs/SCOPE_BREAKDOWN.md` để chi tiết.

---

## 📱 Mobile CI/CD + EAS Flow

Template này có 3 lớp verify:

### 1. Local Development
```bash
npm run dev
# hoặc
expo start
```
- Hot reload + debug UI trực tiếp
- Chạy trên simulator/emulator hoặc device
- Nơi để catch lỗi nhanh nhất

### 2. GitHub Actions Quality Gate
Trigger: PR hoặc push vào `main` / `develop`

Workflow: `.github/workflows/ci.yml`

Checks:
- ✅ Lint
- ✅ TypeScript typecheck
- ✅ Unit tests
- ✅ Integration tests
- ✅ Build sanity check

**Nếu fail:** PR không merge được, phải fix local rồi push lại.

### 3. EAS Preview Build
Trigger: push vào `develop` hoặc manual `workflow_dispatch`

Workflow: `.github/workflows/eas-preview.yml`

Output:
- EAS preview build (QR code để test trên device)
- Dùng trước khi merge vào `main`
- Xem `docs/CI_CD_MOBILE.md` để setup EAS

### 4. EAS Production Build
Trigger: manual `workflow_dispatch` (chỉ từ `main`)

Workflow: `.github/workflows/eas-production.yml`

Output:
- EAS production build (sẵn sàng submit App Store / Google Play)
- Có `environment: production` để gắn approval nếu cần

Xem `docs/CI_CD_MOBILE.md` để full guide + EAS setup.

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
pip install graphify

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
- Init Sentry trong React Native
- Setup Prometheus metrics
- Create Grafana dashboards
- Deploy production

---

## 🧪 Testing Strategy

| Loại | Khi nào viết | Tool |
|------|-------------|------|
| **Unit** | Ngay sau mỗi task | Vitest |
| **Integration** | Cuối mỗi layer | Vitest |
| **E2E** | Trước release | Detox |

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

---

## 📝 Prompt Templates

### Bắt đầu task mới
```
Đọc CODEX.md → docs/phases/phase-0.md → tasks/todo.md

Implement task "In Progress".
Chỉ sửa files được liệt kê trong task.

Sau khi xong:
1. Viết unit test
2. Chạy test, fix nếu fail
3. Commit: feat/fix/test: [mô tả ngắn]
4. Move task sang done.md
5. Báo kết quả ngắn gọn
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

- **Scope Breakdown:** `docs/SCOPE_BREAKDOWN.md`
- **Brainstorming Skill:** `skills/brainstorming/SKILL.md`
- **Memory Hooks:** `docs/MEMORY_HOOKS.md`
- **Continuous Learning:** `docs/CONTINUOUS_LEARNING.md`
- **Graphify:** `docs/GRAPHIFY.md`
- **Monitoring:** `docs/MONITORING.md`
- **Mobile CI/CD:** `docs/CI_CD_MOBILE.md`
- **Mobile E2E:** `docs/MOBILE_E2E.md`

---

## 📜 License

MIT
