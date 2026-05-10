---
name: note-link
description: Link detailed notes in notes/personel/ to the chapter summary in notes/opencode-note.md.
---

## When to Use
- After a `/note` is saved to `notes/personel/`
- When user says `/link` or explicitly asks to link notes
- Before committing to ensure all detailed notes are referenced

## Workflow

### 1. Scan for unlinked notes
- List all `.md` files in `notes/personel/`
- Read `notes/opencode-note.md`
- Find notes in `personel/` that are NOT yet linked in `opencode-note.md`

### 2. Match to chapter
- Map each `personel/{topic}.md` to its corresponding chapter in `opencode-note.md`
- e.g. `lsp.md` → chapter 6 (Configuration)

### 3. Add link
Under the matching chapter, append:
```
📝 [อ่านละเอียด: {Topic}](./personel/{topic}.md)
```

### 4. Reply
"🔗 linked: {N} notes added to opencode-note.md"
