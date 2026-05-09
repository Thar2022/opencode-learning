# OpenCode บทเรียน

## บทที่ 1: ติดตั้ง & เริ่มต้น
- ติดตั้ง OpenCode
- `/connect` เชื่อมต่อ LLM provider
- `/init` วิเคราะห์ project
- คำสั่งแรก: "อธิบาย project นี้หน่อย"

## บทที่ 2: Agents (Plan/Build)
- Build mode: ทำจริง (default)
- Plan mode: วิเคราะห์ก่อน ไม่แก้ไฟล์
- สลับด้วย `Tab`
- ใช้ `@general` สำหรับ task ซับซ้อน

## บทที่ 3: ไฟล์ & แก้ไขโค้ด
- อ่านไฟล์ (Read tool)
- เขียนไฟล์ (Write tool)
- แก้ไขเฉพาะจุด (Edit tool)
- `/undo` และ `/redo`

## บทที่ 4: Git & GitHub
- commit, branch, push
- สร้าง PR ผ่าน OpenCode
- GitHub Actions + OpenCode bot

## บทที่ 5: คำสั่งพิเศษ
- `/share` แชร์ session
- `/connect` เปลี่ยน provider
- `/init` สร้าง AGENTS.md
- `@plan` / `@general` invoke subagent

## บทที่ 6: Configuration
- `opencode.json` config
- ตั้งค่า LSP
- สร้าง custom agent
- MCP servers

## บทที่ 7: Sub-agents
- `@general` — general-purpose สำหรับ task ซับซ้อน
- `@explore` — อ่านอย่างเดียว ค้นหาโค้ดเร็ว
- สร้าง custom subagent ใน `opencode.json`
- ใช้ `@` mention ในข้อความ

## บทที่ 8: Skills
- Skill = คำสั่งเฉพาะทางที่โหลดเมื่อต้องการ
- ใช้ skill tool เพื่อโหลด workflow
- สร้าง skill เอง
- ตัวอย่าง: code-review, test-runner, deploy

## บทที่ 9: ขั้นสูง
- ทำงานหลาย session พร้อมกัน
- Client/Server architecture
- Local models
- Privacy & security