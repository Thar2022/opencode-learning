---
name: book-progress
description: จัดการโครงสร้างหนังสือ — สร้าง TOC, PROGRESS, notes per chapter. ใช้เมื่อ user พูด "เริ่มเล่ม", "book start", "อ่านเล่ม", "book"
---

## When to Use
Activate when user says: `เริ่มเล่ม`, `book start`, `อ่านเล่ม`, `book`, `ตำรา`, `สถานะเล่ม`

## Workflow

### 1. Initialize a new book
When user says "เริ่มเล่ม {ชื่อ}" or "book start {name}":
- Create `books/{book-slug}/` with:
  - `TOC.md` — สารบัญ
  - `PROGRESS.md` — tracking table
  - `notes/` — directory for chapter notes

**TOC.md template:**
```markdown
# {Book Name}

## Chapters
| # | Chapter | Pages | Status |
|---|---------|-------|--------|
| 1 | ... | ... | ยังไม่เริ่ม |
```

**PROGRESS.md template:**
```markdown
# {Book Name} — Progress

| บทที่ | ชื่อ | สถานะ | วันที่ |
|-------|------|--------|-------|
| 1 | ... | ยังไม่เริ่ม | - |
```

### 2. Track progress (same pattern as main PROGRESS.md)
- When chapter complete → mark `เสร็จ` + date in PROGRESS.md
- Summarize key learnings → save to `books/{book-slug}/notes/chapter-{N}.md`
- Commit message: "Complete Book:{book} Chapter {N}: {name}"

### 3. Show status
When user says "สถานะ {book}" or "progress {book}":
- Read `books/{book-slug}/PROGRESS.md`
- Display the table
- Show % complete

### 4. Add chapters to TOC
When user provides a chapter list or source doc:
- Extract chapter titles
- Update TOC.md table

### Book slug rules
- Lowercase, no spaces, hyphens instead: `python-crash-course`, `the-go-programming`
