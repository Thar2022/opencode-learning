# OpenCode Notes

## บทที่ 1: ติดตั้ง & เริ่มต้น — 2026-05-09
- OpenCode = AI coding agent แบบ open-source ใช้ใน terminal, desktop app, IDE
- `/connect` = เชื่อมต่อ LLM provider (Claude, GPT, Gemini)
- `/init` = ให้ AI วิเคราะห์ project → อธิบายว่ามีอะไรบ้าง → สร้าง AGENTS.md
- ติดตั้งผ่าน: curl script, npm, brew

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
