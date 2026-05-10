---
name: mindmap
description: สร้าง mermaid mindmap แสดงความสัมพันธ์ของคอนเซปต์ ใช้เมื่อ user พูด "mindmap", "แผนผัง", "diagram"
---

## When to Use
Activate when user says: `mindmap`, `แผนผัง`, `diagram`, `ความสัมพันธ์`, `map`

## Workflow

### 1. Read source
- Read the file or content the user wants mapped
- If no source specified, use recent conversation context

### 2. Extract concepts & relationships
Identify:
- Root topic (center of map)
- Sub-topics (2–3 levels deep)
- Cross-relationships (depends on, extends, alternative to)
- Categories / groupings

### 3. Generate mermaid mindmap
Use this format:
```markdown
## {Topic} — Mindmap

```mermaid
mindmap
  root((Main Topic))
    Sub-topic A
      Detail 1
      Detail 2
    Sub-topic B
      Detail 3
      Detail 4
    Cross-cutting
      Concept X
      Concept Y
```
```

Keep mindmap focused — max 15–20 nodes. Too complex = not useful.

### 4. Save & reply
- Save to `notes/personel/{topic}-mindmap.md`
- Display the diagram inline
- Reply: `🗺️ แผนผังแล้ว: notes/personel/{topic}-mindmap.md`
