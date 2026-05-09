# OpenCode Learning

## What is OpenCode?

OpenCode is an open-source AI coding agent that works in terminal, desktop app, or IDE extension. It differs from Claude Code in that it's:
- 100% open-source
- Provider-agnostic (works with Claude, OpenAI, Gemini, local models)
- Terminal-first design
- Built-in LSP support

## Installation

```bash
# Linux/Mac
curl -fsSL https://opencode.ai/install | bash

# Windows (recommended WSL)
npm install -g opencode
```

## Basic Commands

| Command | Description |
|---------|-------------|
| `/init` | Analyze project and create AGENTS.md |
| `/connect` | Connect to LLM provider |
| `/undo` | Undo last changes |
| `/redo` | Redo changes |
| `Tab` | Switch between Build/Plan agents |

## Agents

- **Build** - Default agent with full tool access
- **Plan** - Read-only agent for analysis and planning

## Getting Started

1. Run `opencode`
2. Use `/connect` to set up your LLM provider
3. Use `/init` to analyze your project
4. Start asking questions!

## Resources

- Website: https://opencode.ai
- Docs: https://opencode.ai/docs
- GitHub: https://github.com/anomalyco/opencode