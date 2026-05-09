# 📝 Concepts — โน๊ตส่วนตัว

> **AI ไม่อ่านไฟล์ใน `/notes`** — โน๊ตสำหรับเราเองเท่านั้น

---

## AGENTS.md คืออะไร?

AGENTS.md = "คู่มือครู AI"
- AI อ่านอัตโนมัติทุก session
- บอก AI ว่าต้องสอนเรายังไง
- บอกให้ไปอ่าน PROGRESS.md หาว่าเรียนถึงบทไหน
- ไม่ควรใส่นoteปน → AI อาจสับสน

## PROGRESS.md คืออะไร?

PROGRESS.md = "สมุดพก"
- เก็บสถานะว่าบทไหนเสร็จ/ยังไม่เริ่ม
- AI อ่านตอนเข้า session → รู้บทปัจจุบัน
- เวลาเรียนจบบท → อัปเดตที่นี่

## TUTORIAL.md คืออะไร?

TUTORIAL.md = "สารบัญบทเรียน"
- รายชื่อทั้ง 9 บท
- AI อ่านเพื่อรู้ว่าสอนอะไรในแต่ละบท

## Flow การเรียนรู้

```
เปิด OpenCode → AI อ่าน AGENTS.md → ไป PROGRESS.md → หาบทปัจจุบัน → สอนจาก TUTORIAL.md
```

## Project Structure

```
├── AGENTS.md       → AI instruction เท่านั้น
├── TUTORIAL.md     → เนื้อหาบทเรียน
├── PROGRESS.md     → สถานะเรียน
├── README.md       → reference
├── CONTRIBUTING.md → แนวทาง contribute
└── notes/          → โน๊ตเราเอง
    └── concepts.md → อธิบาย concept ต่างๆ
```
