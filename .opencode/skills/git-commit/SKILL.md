---
name: git-commit
description: Smart commit — group related files, commit in batches, then push. Activate when user says "เอาขึ้น" or "commit".
---

## When to Use
Activate when user says `เอาขึ้น` or `commit`.

## Workflow

### 1. Check what changed
```
git status
```

### 2. Group files by purpose
Look at all modified/untracked files and group them logically by what they do:
- e.g. "skill files" (`.opencode/skills/`), "docs" (`*.md`), "config", etc.
- If unrelated topics → commit separately
- If all related → single commit is fine

### 3. Commit each group
For each logical group:
```
git add {group files}
git commit -m "describe this group's change"
```

### 4. Push once at the end
```
git push origin main
```

### 5. Reply
Summarize all commits:
```
commit แล้ว:
- abc1234: message 1
- def5678: message 2
```
