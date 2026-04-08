<div align="center">

# unified-skill

**The AI skill that pairs with [unified-mcp](https://github.com/orkait/unified-mcp).**

<p>
  <img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" alt="MIT" />
  <a href="https://github.com/orkait/unified-mcp"><img src="https://img.shields.io/badge/requires-unified--mcp-6366f1?style=flat-square" alt="Requires unified-mcp" /></a>
  <img src="https://img.shields.io/badge/plugins-9-10b981?style=flat-square" alt="9 plugins" />
  <a href="https://github.com/orkait/unified-skill/stargazers"><img src="https://img.shields.io/github/stars/orkait/unified-skill?style=flat-square&color=f0c040" alt="Stars" /></a>
</p>
<p>
  <img src="https://img.shields.io/badge/React_Flow-v12-22c55e?style=flat-square&logo=react&logoColor=white" alt="React Flow" />
  <img src="https://img.shields.io/badge/Motion-v12-f59e0b?style=flat-square&logo=framer&logoColor=white" alt="Motion" />
  <img src="https://img.shields.io/badge/Lenis-smooth_scroll-0ea5e9?style=flat-square" alt="Lenis" />
  <img src="https://img.shields.io/badge/React_19-Next.js-61dafb?style=flat-square&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/Tailwind-v4_tokens-06b6d4?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind" />
  <img src="https://img.shields.io/badge/Echo-Go-00ADD8?style=flat-square" alt="Echo" />
  <img src="https://img.shields.io/badge/Golang-practices-00ADD8?style=flat-square" alt="Go" />
  <img src="https://img.shields.io/badge/Rust-practices-ce422b?style=flat-square&logo=rust&logoColor=white" alt="Rust" />
  <img src="https://img.shields.io/badge/UI%2FUX-principles-a855f7?style=flat-square" alt="UI/UX" />
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

Covers 9 libraries and domains through a single skill file:

| Domain | Library | What this skill teaches |
|--------|---------|------------------------|
| Flow UIs | [@xyflow/react](https://reactflow.dev) v12 | Critical gotchas, state decisions, layout choices, custom node/edge patterns |
| Animation | [Motion for React](https://motion.dev) v12 | Import rules, AnimatePresence traps, scroll/gesture/spring decisions |
| Smooth scroll | [Lenis](https://lenis.darkroom.engineering) | GSAP integration, data-lenis-prevent, accessibility, modal locking |
| Frontend | React 19 + Next.js App Router | RSC vs client decisions, state hierarchy, data fetching rules |
| Design system | Tailwind v4 + OKLCH tokens | Three-layer token architecture, @theme vs @theme inline, color ramp rules |
| Web framework | [Echo](https://echo.labstack.com) Go | Middleware order, routing, auth, graceful shutdown |
| Backend | Go best practices + design patterns | Error wrapping, goroutine lifecycle, context, concurrency patterns |
| Systems | Rust best practices | Borrow vs clone, error handling, iterator patterns, ownership decisions |
| Design | UI/UX principles | Typography, color, spacing, elevation, motion, accessibility checklists |

The skill does **not** duplicate API docs - it tells the AI to call the right MCP tool instead, keeping the skill lean and the data always current.

---

## 🚀 Setup

### 1. Install unified-mcp

Follow the setup guide at [orkait/unified-mcp](https://github.com/orkait/unified-mcp). You need the MCP server running before this skill does anything useful.

### 2. Install this skill

**Claude Code** - drop into your skills directory:

```bash
git clone https://github.com/orkait/unified-skill.git ~/.claude/skills/unified-skill
```

The skill is picked up automatically on next session start - no config changes needed.

---

## 🗂 Structure

```
unified-skill/
└── SKILL.md    # The full skill - frontmatter triggers + behavioral guidance
```

The skill has no code. All executable content lives in [unified-mcp](https://github.com/orkait/unified-mcp).

---

## ✏️ Contributing

Edit `SKILL.md` directly. The frontmatter `triggers` list controls when Claude auto-activates the skill - add terms there if you want it to fire on more keywords.

If you find a gotcha that should be documented, open a PR against this repo. If you find missing API data, open it against [unified-mcp](https://github.com/orkait/unified-mcp).

---

## 📄 License

MIT © [Orkait](https://github.com/orkait)
