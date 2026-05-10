---
name: quiz
description: สร้างข้อสอบจากเนื้อหาเพื่อทดสอบความเข้าใจ ใช้เมื่อ user พูด "quiz", "ข้อสอบ", "ทดสอบ", "test me"
---

## When to Use
Activate when user says: `quiz`, `ข้อสอบ`, `ทดสอบ`, `test me`, `ถามหน่อย`

## Workflow

### 1. Get source material
- Check if user specifies a file or topic to quiz on
- If no source specified, ask which file/topic
- Read the source file or review recent conversation context

### 2. Generate questions
Create 5 questions mixing:
- **Multiple choice** (3–4 choices)
- **Short answer** (1–2 sentences expected)
- **True / False** (with explanation required)

Cover key concepts, not trivia. Questions should test understanding, not memorization.

### 3. Ask one at a time
- Show question → wait for answer
- Reveal correct answer + explanation
- Move to next question

### 4. Score
At the end:
```
🎯 คะแนน: {correct}/5
```
- 0–2: "ลองทบทวนอีกรอบ" → suggest which sections to re-read
- 3: "ใช้ได้ ยังมีจุดที่ต้องทวน"
- 4–5: "เยี่ยม! เข้าใจดีแล้ว"
