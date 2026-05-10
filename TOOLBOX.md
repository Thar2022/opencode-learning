# TOOLBOX — Skills & Agents

ระบบที่สร้างไว้สำหรับเรียนรู้หนังสือ/เอกสารต่าง ๆ — 2026-05-10

## Skills (10)

| # | Skill | Trigger | ทำอะไร |
|---|-------|---------|--------|
| 1 | `git-commit` | `เอาขึ้น`, `commit` | commit + push จัดกลุ่มไฟล์ |
| 2 | `note-taker` | `/note` | จดโน้ตลง `notes/personel/{topic}.md` |
| 3 | `note-link` | `/link` | โยงโน้ต personel → opencode-note.md |
| 4 | `note-verify` | auto ก่อน commit | ตรวจโน้ตกันเนื้อหาผิด/ก่อนวัย |
| 5 | `self-improve` | `ปรับปรุง`, `improve` | เรียนรู้ข้อผิดพลาด → อัปเดต AGENTS/SKILL |
| 6 | `summarize` | `สรุป`, `summarize` | สรุปเนื้อหาเป็น structured notes |
| 7 | `quiz` | `quiz`, `ข้อสอบ` | สร้างข้อสอบ 5 ข้อ + เฉลย |
| 8 | `mindmap` | `mindmap`, `แผนผัง` | สร้าง mermaid mindmap |
| 9 | `book-progress` | `เริ่มเล่ม`, `สถานะเล่ม` | จัดการ TOC + PROGRESS ต่อเล่ม |
| 10 | `glossary` | `glossary`, `ศัพท์` | สะสมศัพท์เทคนิค |

## Agents (8)

| # | Agent | เรียก | ทำอะไร | Type |
|---|-------|------|--------|------|
| — | `plan` | `Tab` | อ่านอย่างเดียว วางแผน | built-in |
| — | `build` | default | ทำจริงทุก tool | built-in |
| — | `@general` | `@general` | งานซับซ้อนหลายขั้น | built-in |
| — | `@explore` | `@explore` | ค้นหาโค้ดเร็ว read-only | built-in |
| 1 | `@reviewer` | `@reviewer` | review โค้ด security/perf | custom |
| 2 | `@debugger` | `@debugger` | หา root cause bug | custom |
| 3 | `@tutor` | `@tutor` | สอน Socratic ถามนำ | custom |
| 4 | `@researcher` | `@researcher` | วิจัยเชิงลึก cross-ref | custom |
