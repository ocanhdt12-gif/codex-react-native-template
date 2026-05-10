# Phase 0: Brainstorming + Planning

> **Goal:** Design rõ ràng, spec được approve, phases + tasks sẵn sàng trước khi code  
> **Output:** design doc trong `docs/specs/` + phases + tasks/todo.md  
> **Status:** ⬜ Todo

---

## Definition of Done
- [ ] `docs/BRIEF.md` đã được đọc
- [ ] Design doc đã viết vào `docs/specs/YYYY-MM-DD-design.md`
- [ ] Spec đã tự review (no placeholder, no contradiction)
- [ ] User đã approve spec
- [ ] `docs/phases/phase-1.md` đến `phase-4.md` đã điền đầy đủ
- [ ] `CODEX.md` đã update Stack + Folder Structure
- [ ] `tasks/todo.md` đã có tasks Phase 1
- [ ] Block "FIRST TIME SETUP" đã xóa khỏi `CODEX.md`
- [ ] Commit tất cả changes

---

## Flow

```
Đọc docs/BRIEF.md
      ↓
Clarify từng câu một
(chỉ hỏi những gì còn mơ hồ)
      ↓
Propose 2-3 approaches + trade-offs
      ↓
Present design từng section
→ confirm sau mỗi section
      ↓
Viết docs/specs/YYYY-MM-DD-design.md
→ commit ngay
      ↓
Tự review spec
(placeholder? contradiction? scope? ambiguity?)
      ↓
User review + approve
      ↓
Chia phases → docs/phases/phase-1..4.md
Update CODEX.md
Tạo tasks/todo.md Phase 1
Xóa FIRST TIME SETUP block
```

---

## Brainstorming Rules (QUAN TRỌNG)

- Hỏi **từng câu một** — không hỏi nhiều cùng lúc
- Ưu tiên **multiple choice** khi có thể
- Đề xuất **2-3 approaches** trước khi chốt design
- Confirm **từng section** của design trước khi đi tiếp
- **KHÔNG code** cho đến khi spec được approve
- **Dùng GPT-5.5** cho Phase 0 (brainstorming tốt hơn)

### Model cho Phase 0

Trước khi bắt đầu Phase 0, chuyển sang GPT:
```bash
/model openai-codex/gpt-5.4
```

Sau khi Phase 0 xong, quay lại Sonnet:
```bash
/model aihub-claude/claude-sonnet-4-6
```

---

## Tự Review Spec (QUAN TRỌNG)

Trước khi user review, kiểm tra design doc:
- Placeholder còn sót không? (TBD, TODO, [...])
- Có mâu thuẫn giữa các section không?
- Scope có quá lớn không? (nếu có → chia sub-projects)
- Có requirement nào mơ hồ không?
- **Có chức năng nào trong SPECIFICATIONS.md mà chưa được mention trong design doc không?** ← QUAN TRỌNG

Nếu có thiếu → fix design doc trước khi user approve. Không skip bước này.

---

## Skill Reference
Chi tiết: `skills/brainstorming/SKILL.md`

### Task Size Guidelines (QUAN TRỌNG)

Khi chia task trong layer:
- Mỗi task nên đủ nhỏ để 1 agent có thể hoàn thành trong 1-3 ngày
- Nếu chức năng lớn → chia thành nhiều task nhỏ hơn
- Có thể chia nhiều layer, nhiều task trong 1 layer cũng được
- Mỗi task phải cụ thể, dễ estimate, dễ test
- Tránh task mơ hồ hoặc quá scope

**Ví dụ:**
- ❌ Sai: "Implement User Management" (quá lớn)
- ✅ Đúng: "Create user list page", "Add user form", "Delete user API", "User validation" (chia nhỏ)
