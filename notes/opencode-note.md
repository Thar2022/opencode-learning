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

## บทที่ 4: Git & GitHub — 2026-05-09

### Git พื้นฐาน
| คำสั่ง | ทำอะไร |
|--------|--------|
| `git checkout -b <branch>` | สร้าง branch ใหม่ |
| `git commit -m "msg"` | commit การเปลี่ยนแปลง |
| `git push origin <branch>` | push ขึ้น remote |
| `git push -f origin <branch>` | force push (เขียนทับ commit เก่า - ระวัง!) |

### Pull Request
| คำสั่ง | ทำอะไร |
|--------|--------|
| `gh pr create --title "..." --body "..."` | สร้าง PR |
| `gh pr merge <num>` | merge PR |
| flow จริง: branch → commit → push → PR → merge | — |

### OpenCode Bot (GitHub Actions)

Bot ที่ทำงานใน GitHub Actions — รัน AI ให้จัดการ issue/PR อัตโนมัติ

**วิธีติดตั้ง:**
1. ไปที่ github.com/apps/opencode-agent → ติดตั้ง app บน repo
2. สร้าง `.github/workflows/opencode.yml` (อยู่ใน repo ที่ยังไม่ commit ด้วย token scope)
3. เพิ่ม secret `ANTHROPIC_API_KEY` ใน repo Settings → Secrets

**Workflow file:**
```yaml
name: opencode
on:
  issue_comment:   # trigger เมื่อมี comment ใน issue หรือ PR
jobs:
  run:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: anomalyco/opencode-action@v1
        with:
          model: anthropic/claude-sonnet-4-20250514
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
```

**Events ที่ trigger ได้:**

| Event | Trigger เมื่อไหร่ | Bot ทำอะไร |
|-------|------------------|-----------|
| `issue_comment` | comment มี `/opencode` หรือ `/oc` | อ่าน issue → วิเคราะห์/แก้ไข → เปิด PR |
| `pull_request_review_comment` | comment บน code ใน PR | อ่าน diff context → ตอบแบบ targeted |
| `issues` | issue เปิดใหม่หรือแก้ไข | อ่านเนื้อหา → วิเคราะห์ให้ |
| `pull_request` | PR เปิด/อัปเดต | AI review PR |
| `schedule` | ตาม cron schedule | รันอัตโนมัติ (ต้องใส่ `prompt`) |
| `workflow_dispatch` | กดรันเองจาก Actions tab | รัน on-demand |

**คำสั่งที่ใช้ใน comment:**

| คำสั่ง | ต้องใช้กับ | ผลลัพธ์ |
|--------|-----------|---------|
| `/opencode explain this issue` | issue | อ่าน issue + ทุก comment → สรุปให้ |
| `/opencode fix this` | issue | สร้าง branch → แก้ bug → เปิด PR |
| `/oc review` | PR | review โค้ดใน PR |
| `/oc implement` | PR comment | แก้ตามที่ขอใน code line comment |

**ข้อดี:**
- ไม่ต้องเปิด OpenCode เอง — bot ทำให้
- ทำงานใน GitHub runner (ปลอดภัย, private)
- คนในทีมใช้ได้แค่ comment
- commit/PR จะแสดงว่ามาจาก bot

**หมายเหตุ:** Token ต้องมี `workflow` scope ถึงจะ push workflow file ได้

### Skills ที่เกี่ยว
- `git-commit` (`เอาขึ้น`) จัด commit+push ให้อัตโนมัติ

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
