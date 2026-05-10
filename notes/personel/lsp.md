# LSP (Language Server Protocol)

## LSP คืออะไร?
> จากบทที่ 6: Configuration

LSP = **Language Server Protocol** — โปรโตคอลมาตรฐานที่ให้ editor หรือ AI coding agent เชื่อมต่อกับ "language server" ซึ่งเป็นโปรแกรมที่เข้าใจภาษานั้นๆ อย่างลึกซึ้ง

**อุปมา:** 
- LSP = "ล่ามแปลภาษา" ระหว่าง AI กับ compiler
- language server = "ผู้เชี่ยวชาญภาษา" ที่รู้ syntax, type, error, autocomplete, goto-definition

**ทำไมต้องมี:**
ปกติ AI (LLM) เห็นแค่ **source code** เป็นข้อความ — มันเดาเอาว่าผิดตรงไหน
LSP ทำให้ AI เห็น **compiler diagnostics** ของจริง — ไม่ต้องเดา

---

## Before vs After LSP

**ก่อนมี LSP:**
```
คุณ: "ทำไมโค้ดพัง?"
AI:  "น่าจะตรงบรรทัด 5 เพราะ syntax ดูแปลกๆ..." (เดา)
    → อาจจะถูก อาจจะผิด
```

**หลังมี LSP:**
```
คุณ: "ทำไมโค้ดพัง?"
AI:  [LSP แจ้ง]
     - บรรทัด 5: Type 'string' is not assignable to 'number' (ts:2322)
     - บรรทัด 12: Cannot find name 'useEffect' (ts:2304)
     → AI เห็น error จาก TypeScript compiler จริง → แก้ตรงจุด
```

---

## ตั้งค่าใน opencode.json

```json
{
  "lsp": {
    "typescript": "typescript-language-server",
    "javascript": "typescript-language-server",
    "go": "gopls",
    "python": "pyright",
    "rust": "rust-analyzer",
    "svelte": "svelte-language-server"
  }
}
```

**รูปแบบ:** `"ภาษา": "ชื่อ-language-server"`

---

## Language Server แต่ละภาษา

| ภาษา | LSP Server | ติดตั้ง |
|------|-----------|---------|
| TypeScript/JavaScript | `typescript-language-server` | `npm install -g typescript-language-server typescript` |
| Go | `gopls` | `go install golang.org/x/tools/gopls@latest` |
| Python | `pyright` | `npm install -g pyright` |
| Rust | `rust-analyzer` | `rustup component add rust-analyzer` |
| Svelte | `svelte-language-server` | `npm install -g svelte-language-server` |

---

## LSP ให้ข้อมูลอะไรกับ AI บ้าง?

| ข้อมูล | คืออะไร | AI เอาไปใช้ยังไง |
|--------|--------|-----------------|
| **Diagnostics** | error/warning จาก compiler | AI รู้ว่าโค้ดพังตรงไหน — แก้ตรงจุด |
| **Go-to-definition** | ฟังก์ชันนี้ประกาศที่ไหน | AI หาต้นทางของโค้ด |
| **Hover info** | type/signature ของตัวแปร | AI รู้ว่า parameter ต้องเป็น type อะไร |
| **References** | ฟังก์ชันนี้ถูกเรียกที่ไหนบ้าง | AI รู้ impact ของการแก้ไข |
| **Autocomplete** | เติมโค้ดให้ | AI แนะนำโค้ดที่ถูก syntax |

---

## Flow การทำงาน

```
1. คุณเปิด OpenCode ในโปรเจค TypeScript
2. OpenCode อ่าน opencode.json → เห็น "typescript": "typescript-language-server"
3. OpenCode เรียก typescript-language-server (ต้องติดตั้งไว้ในเครื่อง)
4. Language server วิเคราะห์โค้ด → ส่ง diagnostics กลับ
5. AI มี diagnostics → ถามอะไรก็ตอบแบบมีข้อมูล compiler จริง
```

---

## ข้อควรรู้

- LSP **ไม่ได้ทำงานบน cloud** — มันรันในเครื่องคุณ
- ต้อง**ติดตั้ง language server ก่อน** — ไม่งั้น LSP ใน config จะไม่ทำงาน
- LSP ทำงาน**อัตโนมัติ**ตลอด session — ไม่ต้องเรียกเอง
- ยิ่งมี LSP → AI ยิ่งแม่น → แก้บั๊กไวขึ้น
