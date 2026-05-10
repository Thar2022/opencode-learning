---
name: summarize
description: อ่าน doc/บทเรียนแล้วสรุปเป็น structured notes พร้อม key concepts, examples, tables. ใช้เมื่อ user พูด "สรุป", "summarize", "ย่อย", "จด"
---

## When to Use
Activate when user says: `สรุป`, `summarize`, `ย่อย`, `จด`, `take notes on`, or provides a file/URL to summarize.

## Workflow

### 1. Read the source
- If user provides a file path → read it
- If user provides a URL → fetch it
- If user provides text directly → use it

### 2. Extract structure
Identify:
- Main topic / title
- Sections / headings
- Key concepts (bold terms, definitions, jargon)
- Code examples or commands
- Tables / lists
- Relationships between concepts

### 3. Write structured notes
Save to `notes/personel/{topic}.md` using this format:

```markdown
# {Topic} — {Date}

## Key Concepts
| Concept | Definition |
|---------|------------|
| ... | ... |

## Step-by-Step
1. ...
2. ...

## Code / Commands
```lang
...
```

## Summary
- Bullet points of key takeaways
```

### 4. Reply
```
📝 สรุปแล้ว: notes/personel/{topic}.md
   {N} concepts, {M} examples
```
