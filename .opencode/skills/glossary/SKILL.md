---
name: glossary
description: สะสมศัพท์เทคนิคจากเนื้อหาที่เรียน — พร้อมคำนิยามและความสัมพันธ์ ใช้เมื่อ user พูด "glossary", "ศัพท์", "คำศัพท์", "definition"
---

## When to Use
Activate when user says: `glossary`, `ศัพท์`, `คำศัพท์`, `definition`, `นิยาม`

## Workflow

### 1. Extract terms
Scan source:
- If user says "glossary บทนี้" → use current chapter/context
- If user says "glossary {file}" → read that file
- Look for: capitalized words, quoted terms, bold/italic terms, code identifiers, repeated jargon

### 2. Define each term
For each term:
- **Short definition** (1 sentence in the user's language)
- **Context** — where it appeared in the source
- **Related terms** — synonyms, parent/child concepts

### 3. Save / update
Save to `notes/glossary.md` using this format:

```markdown
# Glossary

## {Chapter / Topic}
| Term | Definition | Related |
|------|------------|---------|
| term1 | definition | related1, related2 |
| term2 | definition | — |
```

If `notes/glossary.md` already exists, append new terms under their topic heading, avoiding duplicates.

### 4. Reply
```
📚 เพิ่ม {N} คำศัพท์ใน glossary
   ดูทั้งหมด: notes/glossary.md
```
