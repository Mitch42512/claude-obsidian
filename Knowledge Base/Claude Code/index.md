---
type: knowledge
title: Claude Code
updated: 2026-05-24
---

# Claude Code

## What It Is
Claude Code is an AI coding agent that runs in your terminal. It has access to your filesystem, can run commands, read/write files, and execute multi-step tasks. It's what's managing this vault right now.

## Key Concepts
- **Skills** — slash commands that give Claude specialised workflows (e.g. `/wiki`, `/save`)
- **MCP servers** — tools that extend what Claude can access (e.g. your Obsidian vault via `mcp-obsidian`)
- **CLAUDE.md** — the instructions file that tells Claude how to behave in a project
- **Hooks** — automated triggers (e.g. run something after every file write)

## Things I've Learned
<!-- Add notes as you go -->

## Useful Commands
| Command | What It Does |
|---------|--------------|
| `/wiki` | Wiki skill — ingest, query, lint |
| `/save` | Save current conversation as a wiki note |

## Resources
- [Claude Code docs](https://docs.anthropic.com/claude-code)
- This vault's `skills/` folder
