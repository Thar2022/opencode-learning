---
name: note-verify
description: Verify notes/opencode-note.md accuracy — check for premature content and fix mistakes. Run before every commit of notes.
---

## When to Use
Run automatically BEFORE any commit that touches `notes/opencode-note.md`.

## What to Check

### 1. Cross-reference with PROGRESS.md
- Read `PROGRESS.md` — note which chapters are marked `เสร็จ`
- If `notes/opencode-note.md` mentions a command/concept from a chapter not yet `เสร็จ` → it's premature → remove it

### 2. Check for unsupported claims
- Flag any statement the AI hasn't actually demonstrated during the session
- If doubtful → remove or mark with `[?]`

### 3. Chapter content map (what each chapter covers)
| Chapter | What's taught |
|---------|---------------|
| 1 | `/init`, `/connect`, install |
| 2 | Build/Plan mode, Tab, `@general` |
| 3 | Read/Edit/Write tools, `/undo`, `/redo` |
| 4 | Git commit, branch, PR, push |
| 5 | `/share`, `/connect` details |
| 6 | `opencode.json`, LSP, custom agents |
| 7 | Sub-agents |
| 8 | Skills |
| 9 | Advanced |

A note for chapter N must NOT mention anything from chapter N+ or later unless explicitly taught early.

### 4. Fix it
- If violations found → edit `notes/opencode-note.md` to remove premature content
- Add a comment `<!-- verified -->` at bottom of file

### 5. Report
- If fixed: "✅ note-verify: {N} issues fixed"
- If clean: "✅ note-verify: clean"
