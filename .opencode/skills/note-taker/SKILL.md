---
name: note-taker
description: Save personal notes to notes/{topic}.md with timestamps. Use when user types /note.
---

## When to Use
Activate when user types `/note` or `/note "..."` or explicitly asks to save a note.

## What You Should Do

### 1. Detect the topic
- Look at the last 5-10 messages of conversation context
- Identify the **main topic** being discussed
- Infer a **short filename** from the topic (lowercase, hyphen-separated, max 3-4 words), e.g. `skill-usage`, `git-workflow`
- Save to `notes/{topic}.md`

### 2. Read existing notes
- Read `notes/{topic}.md` if exists, create if not
- If file exists, append; if new, create with `# {Topic Title}`

### 3. Append with timestamp
```
## {HH:MM} {label}
- key insight 1
- key insight 2
---
```

### 4. Reply
Confirm: "บันทึกแล้ว → notes/{topic}.md"
