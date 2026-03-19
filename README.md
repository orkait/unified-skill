<div align="center">

# unified-skill

**The AI skill that pairs with [unified-mcp](https://github.com/orkait/unified-mcp).**

<p>
  <a href="https://github.com/orkait/unified-skill/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue" alt="License" /></a>
  <a href="https://github.com/orkait/unified-mcp"><img src="https://img.shields.io/badge/requires-unified--mcp-6366f1" alt="Requires unified-mcp" /></a>
  <a href="https://www.npmjs.com/package/@xyflow/react"><img src="https://img.shields.io/badge/@xyflow%2Freact-v12-22c55e?logo=npm" alt="React Flow v12" /></a>
  <a href="https://motion.dev"><img src="https://img.shields.io/badge/motion%2Freact-v12-f59e0b?logo=framer" alt="Motion v12" /></a>
</p>

<br/>

> A Claude Code skill that teaches your AI assistant **when and how** to use unified-mcp tools.
> The skill handles judgment, gotchas, and decisions.
> The MCP server provides the actual data.

</div>

---

## 🧩 How they fit together

```
unified-skill  →  tells the AI which MCP tools to call and when
unified-mcp    →  serves API refs, examples, patterns, and code generation
```

Neither is useful without the other. Install both.

---

## 📦 What's in this skill

Covers two libraries through a single skill file:

| Domain | Library | Taught by this skill |
|--------|---------|---------------------|
| Flow UIs | [@xyflow/react](https://reactflow.dev) v12 | Critical gotchas, state decisions, layout choices, custom node/edge patterns |
| Animation | [Motion for React](https://motion.dev) v12 | Import rules, AnimatePresence traps, scroll/gesture/spring decisions |

The skill does **not** duplicate API docs - it tells the AI to call `reactflow_get_api()` or `motion_get_api()` instead, keeping the skill lean and the data always up to date from the MCP server.

---

## 🚀 Setup

### 1. Install unified-mcp

Follow the setup guide at [orkait/unified-mcp](https://github.com/orkait/unified-mcp). You need the MCP server running before this skill does anything useful.

### 2. Install this skill

**Claude Code** - drop into your skills directory:

```bash
git clone https://github.com/orkait/unified-skill.git ~/.claude/skills/unified-skill
```

Or if you use a superpowers plugin:

```bash
git clone https://github.com/orkait/unified-skill.git ~/.claude/plugins/superpowers/skills/unified-skill
```

The skill is picked up automatically on next session start - no config changes needed.

---

## 🗂 Structure

```
unified-skill/
└── SKILL.md    # The full skill - frontmatter triggers + behavioral guidance
```

The skill intentionally has no code. All executable content lives in [unified-mcp](https://github.com/orkait/unified-mcp).

---

## ✏️ Contributing

Edit `SKILL.md` directly. The frontmatter `triggers` list controls when Claude auto-activates the skill - add terms there if you want it to fire on more keywords.

If you find a gotcha that should be documented, open a PR against this repo. If you find missing API data, open it against [unified-mcp](https://github.com/orkait/unified-mcp).

---

## 📄 License

MIT © [Orkait](https://github.com/orkait)
