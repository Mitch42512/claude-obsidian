---
type: reference
title: Plugin Guide
updated: 2026-05-24
---

# claude-obsidian — Plugin Reference

This vault runs on the **claude-obsidian** plugin: a Claude Code companion that builds and maintains a persistent, compounding wiki. Everything here is generated and maintained by Claude — zero manual filing.

Based on [Andrej Karpathy's LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).

---

## How It Works

Drop a source file into `.raw/`, then tell Claude: `ingest [filename]`.  
Ask any question — Claude reads the index and relevant wiki pages, cites sources.  
Run `lint the wiki` to catch orphans, dead links, and gaps.

---

## Commands

| You say | Claude does |
|---------|------------|
| `/wiki` | Setup check, scaffold, or continue |
| `ingest [file]` | Read source → 8-15 wiki pages, update index & log |
| `what do you know about X?` | Read index → relevant pages → synthesize answer |
| `/save` | File the current conversation as a wiki note |
| `/autoresearch [topic]` | Autonomous research: search, fetch, synthesize, file |
| `/canvas` | Open or create the visual canvas |
| `lint the wiki` | Health check: orphans, dead links, gaps |
| `update hot cache` | Refresh wiki/hot.md with latest context summary |

---

## Skills (11 total)

| Skill | What it does |
|-------|-------------|
| `wiki` | Orchestrator — setup, scaffold, route |
| `wiki-ingest` | Source ingestion (8-15 pages per source) |
| `wiki-query` | Answer questions with citations (3 depth modes) |
| `wiki-lint` | Health check — orphans, dead links, gaps |
| `wiki-fold` | Log rollup (DragonScale Mechanism 1) |
| `save` | File conversations as structured wiki notes |
| `autoresearch` | Autonomous research loop with boundary scoring |
| `canvas` | Visual layer — images, PDFs, notes on Obsidian canvas |
| `defuddle` | Strip ads/boilerplate from web pages |
| `obsidian-bases` | Obsidian Bases database layer |
| `obsidian-markdown` | Obsidian syntax reference |

Skills live in `skills/` (hidden from Obsidian view).

---

## Wiki Modes

| Mode | Use when |
|------|---------|
| A: Website | Sitemap, content audit, SEO wiki |
| B: GitHub | Codebase map, architecture wiki |
| C: Business | Project wiki, competitive intelligence |
| D: Personal | Second brain, goals, journal synthesis |
| E: Research | Papers, concepts, thesis |
| F: Book/Course | Chapter tracker, course notes |

---

## Vault Structure

```
wiki/           Knowledge base (auto-maintained)
  index.md      Master catalog
  hot.md        Session context cache (~500 words)
  log.md        Append-only operation log
  concepts/     Concept pages
  entities/     People, projects, orgs
  sources/      Ingested source summaries
  meta/         Dashboards, diagrams, release notes
.raw/           Source documents (drop files here)
_templates/     Obsidian Templater templates
```

---

## Functional Files (root, hidden from Obsidian)

| Path | Purpose |
|------|---------|
| `skills/` | Skill definitions (Claude Code) |
| `commands/` | Slash command definitions |
| `agents/` | Parallel agent definitions |
| `hooks/hooks.json` | SessionStart / Stop hot cache hooks |
| `scripts/` | DragonScale helper scripts |
| `CLAUDE.md` | Project instructions (auto-loaded) |
| `README.md` | Public plugin README |

---

## Documentation

- [[docs/install-guide|Install Guide]] — full setup walkthrough
- [[docs/dragonscale-guide|DragonScale Guide]] — advanced memory features
- [[WIKI.md|Wiki Schema Reference]] — note types, frontmatter spec
- [[AGENTS.md|Multi-Agent Guide]] — parallel ingestion setup
- [[CHANGELOG.md|Changelog]] — release history
- [[ATTRIBUTION.md|Attribution]] — credits & license

---

## MCP Setup (Optional)

Lets Claude read and write vault notes directly without copy-paste.

```bash
# REST API based (recommended)
claude mcp add-json obsidian-vault '{
  "type": "stdio",
  "command": "uvx",
  "args": ["mcp-obsidian"],
  "env": {
    "OBSIDIAN_API_KEY": "your-key",
    "OBSIDIAN_HOST": "127.0.0.1",
    "OBSIDIAN_PORT": "27124",
    "NODE_TLS_REJECT_UNAUTHORIZED": "0"
  }
}' --scope user
```

See [[docs/install-guide|Install Guide]] for full MCP options.

---

## Cross-Project Use

Point any Claude Code project at this vault — add to that project's `CLAUDE.md`:

```markdown
## Wiki Knowledge Base
Path: ~/path/to/vault

When you need context not already in this project:
1. Read wiki/hot.md first (recent context cache)
2. If not enough, read wiki/index.md
3. Read the relevant domain sub-index
4. Only then drill into specific wiki pages
```
