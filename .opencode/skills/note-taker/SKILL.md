---
name: note-taker
description: Save personal notes to notes/personel/{topic}.md with timestamps. Use when user types /note.
---

## When to Use
Activate when user types `/note` or `/note "..."` or explicitly asks to save a note.

## What You Should Do

### 1. Detect the topic
- Look at the last 5-10 messages of conversation context
- Identify the **main topic** being discussed
- Infer a **short filename** from the topic (lowercase, hyphen-separated, max 3-4 words), e.g. `skill-usage`, `git-workflow`
- Save to `notes/personel/{topic}.md`

### 2. Detect which chapter (if any)
- Check `PROGRESS.md` — which chapter is currently `กำลังเรียน` or was most recently completed
- If conversation context mentions a specific chapter's content → tag it
- If no chapter is relevant → skip this step

### 3. Read existing notes
- Read `notes/personel/{topic}.md` if exists, create if not
- If file exists, append; if new, create with `# {Topic Title}`

### 4. Append with timestamp
```
## {HH:MM} {label}
> จากบทที่ X: {ชื่อบท}
- key insight 1
- key insight 2
---
```
If no chapter detected, omit the `> จากบทที่...` line.

### 4. When user says "ละเอียด" or wants detail
Write comprehensive notes with:
- Tables (comparisons, features, commands)
- Code examples with explanations
- Before/After comparisons
- Flow diagrams (text-based)
- Real-world examples from the conversation
- Reasons WHY something works the way it does

### 5. Reply
Confirm: "บันทึกแล้ว → notes/personel/{topic}.md"
