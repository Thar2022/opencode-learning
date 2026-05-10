---
name: self-improve
description: Review recent mistakes and update AGENTS.md or SKILL.md to prevent repeat. Use when user says "improve", "fix memory", or "ปรับปรุง".
---

## When to Use
Activate when user says `improve`, `fix memory`, `ปรับปรุง`, or similar.

## Workflow

### 1. Scan for issues
Look at the last 10-20 messages of conversation context for:
- User complaints or corrections (e.g. "you didn't teach me properly", "don't do that again", "you forgot to check")
- User suggestions on how to improve
- Mistakes you made: incorrect behavior, wrong assumptions, bad file placement
- Things the user had to remind you about more than once

### 2. Categorize the issue

| Type | Fix where |
|------|-----------|
| Teaching style | `AGENTS.md` — Teaching style section |
| Committing behavior | `AGENTS.md` — How to track progress |
| Skill behavior | `.opencode/skills/{skill}/SKILL.md` |
| Config issue | `opencode.json` |
| Wrong file location | Move file to correct location |

### 3. Apply the fix
- Read the target file first
- Add or modify the specific rule/instruction
- Be precise — change only what needs changing
- Write the rule as: "**When user does X** → do Y instead"
- Avoid vague instructions

### 4. Confirm
Reply with:
- What issue was found
- What file was updated
- What rule was added

Example:
```
🔧 self-improve:
  Issue: AI created notes in /notes/ instead of /notes/personel/
  Fix: Updated note-taker/SKILL.md → save to notes/personel/{topic}.md
  Rule added: "Save to notes/personel/{topic}.md, not notes/"
```
