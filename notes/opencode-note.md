# OpenCode Notes

## บทที่ 1: ติดตั้ง & เริ่มต้น — 2026-05-09
- OpenCode = AI coding agent แบบ open-source ใช้ใน terminal, desktop app, IDE
- `/connect` = เชื่อมต่อ LLM provider (Claude, GPT, Gemini)
- `/init` = ให้ AI วิเคราะห์ project → อธิบายว่ามีอะไรบ้าง → สร้าง AGENTS.md
- ติดตั้งผ่าน: curl script, npm, brew

## บทที่ 2: Agents (Plan/Build) — 2026-05-09
- **Build mode** = default, ทำจริงทุกอย่าง (read, write, edit, bash)
- **Plan mode** = วิเคราะห์อย่างเดียว ไม่แก้ไฟล์ ไม่รันคำสั่ง
- สลับด้วย `Tab` หรือ `@plan` / `@build`
- **@general** = sub-agent — ลูกน้อง AI ที่รับงานก้อนใหญ่แล้วแยกไปทำเอง (ค้นหา จัดกลุ่ม หลายขั้นตอน) โดยไม่ต้องคอยสั่งทีละขั้น
- @general เหมาะกับงานที่ต้อง explore โค้ดเยอะๆ หรือทำงานซับซ้อนหลายขั้นในครั้งเดียว

## บทที่ 3: ไฟล์ & แก้ไขโค้ด — 2026-05-09
- Read / Edit / Write ไม่ใช่คำสั่ง — เป็น tools ที่ AI ใช้เบื้องหลัง
- เราบอกสิ่งที่ต้องการ → AI เลือก tool เอง
- `/undo` = ย้อนการแก้ไขล่าสุด
- `/redo` = ทำซ้ำที่ undo ไป

## ระบบการเรียนรู้ — 2026-05-09
- **AGENTS.md** = "คู่มือครู AI" — AI อ่านอัตโนมัติทุก session
- **PROGRESS.md** = "สมุดพก" — เก็บสถานะว่าบทไหนเสร็จ
- **TUTORIAL.md** = "สารบัญ" — 9 บทเรียน
- **Flow**: เปิด OpenCode → AI อ่าน AGENTS.md → PROGRESS.md → สอนบทปัจจุบัน

## โครงสร้างโปรเจค — 2026-05-09
```
├── AGENTS.md       → AI instruction
├── TUTORIAL.md     → เนื้อหา 9 บท
├── PROGRESS.md     → สถานะเรียน
├── README.md       → reference
├── CONTRIBUTING.md
├── .opencode/skills/
│   ├── note-taker/SKILL.md
│   └── git-commit/SKILL.md
└── notes/
    └── opencode-note.md ← สรุปบทเรียน
```
