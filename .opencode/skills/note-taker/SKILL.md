---
name: note-taker
description: Save personal notes to notes/{date}.md with timestamps. Use when user types /note.
---

## When to Use
Activate when user asks to save a note, concept, or learning point.

## Workflow
1. Read current date (YYYY-MM-DD)
2. Read `notes/{date}.md` if exists, create if not
3. Append note with timestamp to file
4. Format:
```
## {HH:MM}
{user's note}
---
```
5. Reply: "บันทึกแล้ว → notes/{date}.md"
