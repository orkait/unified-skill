---
name: unified-skill
description: >-
  Build flow-based UIs with React Flow v12 (@xyflow/react) and animate React
  components with Motion for React (motion/react). Use for nodes, edges, flow
  diagrams, workflow builders, DAGs, canvas UIs, custom nodes/edges, Zustand
  flow state, layout algorithms (dagre/elk), animations, transitions, gestures,
  drag, scroll animations, layout animations, exit animations, spring physics,
  variants, keyframes, whileHover, whileTap, whileInView, AnimatePresence,
  framer-motion, or motion values.
metadata:
  author: claude
  version: "1.0.0"
  license: MIT
triggers:
  - react flow
  - nodes and edges
  - flow diagram
  - workflow builder
  - pipeline editor
  - DAG editor
  - canvas UI
  - node-based editor
  - draggable nodes
  - xyflow
  - motion
  - framer-motion
  - animate
  - animation
  - AnimatePresence
  - exit animation
  - layout animation
  - whileHover
  - whileTap
  - whileInView
  - spring
  - variants
  - motion value
  - useScroll
activation:
  mode: fuzzy
  priority: high
---

# unified-mcp Skill

This skill relies on [unified-mcp](https://github.com/orkait/unified-mcp). Always use the MCP tools below for all API details, props, code examples, patterns, and transitions. This skill covers judgment, gotchas, and decisions only — unified-mcp provides all actual data.

---

## React Flow — MCP Tools

| Tool | What it returns |
|------|----------------|
| `reactflow_list_apis` | All 56 APIs grouped by kind (component/hook/utility/type) with one-line descriptions |
| `reactflow_get_api("Name")` | Full props table, usage snippet, code examples, tips, and related APIs |
| `reactflow_get_pattern("name")` | Complete implementation code for enterprise patterns (store, undo/redo, layout, etc.) |
| `reactflow_get_template("name")` | Production-ready TSX starter for custom-node, custom-edge, or zustand-store |
| `reactflow_get_examples("category")` | Curated code examples filtered by category |
| `reactflow_get_migration_guide` | v11 → v12 breaking changes with before/after diffs |
| `reactflow_generate_flow("description")` | Ready-to-use TSX generated from a prose description |
| `reactflow_search_docs("keyword")` | Full-text search across all API docs, patterns, and templates |

Patterns: zustand-store, undo-redo, drag-and-drop, auto-layout-dagre, auto-layout-elk, context-menu, copy-paste, save-restore, prevent-cycles, keyboard-shortcuts, performance, dark-mode, ssr, subflows, edge-reconnection, custom-connection-line, auto-layout-on-mount

Templates: custom-node, custom-edge, zustand-store

---

## React Flow — Critical Rules

- nodeTypes and edgeTypes must be defined outside components — never inline, causes remount on every render
- memo() all custom nodes and edges — they re-render aggressively otherwise
- node.measured.width/height is read-only — set by the library, do not set it yourself
- deleteElements() is async — returns Promise with deletedNodes and deletedEdges
- onBeforeDelete must be async — return Promise false to cancel, Promise true to confirm
- Hooks outside ReactFlow must be wrapped in ReactFlowProvider
- getNode() and getEdge() return undefined (not null) when not found — v12 change
- useUpdateNodeInternals() — call after adding or removing handles programmatically
- Attribution — use proOptions hideAttribution on free tier

---

## React Flow — Decisions

State management: single component use useNodesState and useEdgesState; shared across components use Zustand via reactflow_get_pattern zustand-store; undo/redo needed use Zustand with zundo via reactflow_get_pattern undo-redo

Layout: tree or left-right hierarchy use dagre via reactflow_get_pattern auto-layout-dagre; complex graphs nested ports use ELK via reactflow_get_pattern auto-layout-elk; on first render use useNodesInitialized with useEffect via reactflow_get_pattern auto-layout-on-mount

Custom nodes: always memo() with useCallback on handlers; use useNodeId() inside node to avoid prop drilling; use useNodesData(ids) to subscribe to specific node data; template via reactflow_get_template custom-node

Custom edges: destructure 5 values edgePath labelX labelY offsetX offsetY from path utils; complex labels use EdgeLabelRenderer (renders in DOM not SVG); template via reactflow_get_template custom-edge

Connection validation: prevent cycles via reactflow_get_pattern prevent-cycles; restrict handle types via isValidConnection prop on Handle or ReactFlow

Groups and subflows: parentId with extent parent and expandParent true on child nodes; add zIndexMode auto on ReactFlow for correct z-ordering

Performance: hide off-screen elements via onlyRenderVisibleElements prop; batch node updates via setNodes updater not repeated updateNode calls; full guide via reactflow_get_pattern performance

---

## Motion for React — MCP Tools

| Tool | What it returns |
|------|----------------|
| `motion_list_apis` | All 32 APIs grouped by kind (component/hook/function/utility) with one-line descriptions |
| `motion_get_api("Name")` | Full props table, usage snippet, code examples, tips, and related APIs |
| `motion_get_examples("category")` | Curated code examples filtered by category |
| `motion_get_transitions` | Complete transition reference: spring presets, tween, inertia, orchestration |
| `motion_generate_animation("description")` | Ready-to-use TSX animation generated from a prose description |
| `motion_search_docs("keyword")` | Full-text search across all API docs and examples |

Example categories: animation, gestures, scroll, layout, exit, drag, hover, svg, transitions, variants, keyframes, spring, reorder, performance

---

## Motion for React — Critical Rules

- Import from motion/react not framer-motion; framer-motion has been replaced by motion, swap imports and uninstall the old package
- AnimatePresence goes outside the conditional — wrap the show and component expression, not the inner element
- exit requires AnimatePresence parent — without it, exit animations are silently ignored
- AnimatePresence direct children need unique key props — required for tracking mount and unmount
- MotionValues are NOT React state — do not read them in render; subscribe with useMotionValueEvent
- AnimatePresence mode popLayout — direct custom component children must be wrapped in forwardRef (React 18) or accept ref as a prop (React 19)
- useReducedMotion() — always respect for accessibility; check before heavy animations
- dragConstraints with a ref — pass constraintsRef to a rendered motion.div; pixel object with top left right bottom is the simpler alternative
- stagger() — import from motion/react, use inside variant transition.delayChildren
- useScroll container vs target — container is a scrollable element needing overflow scroll or auto; target is an element whose position is tracked within the container; default tracks the viewport

---

## Motion for React — Decisions

Basic animation: simple one-off use initial and animate props on motion.div; reusable states use variants with string labels via motion_get_api motion; imperative control use useAnimate hook via motion_get_api useAnimate

Exit animations: always use AnimatePresence with exit prop and unique key on child; old page exits before new enters use mode wait; keep siblings in layout during exit use mode popLayout; details via motion_get_api AnimatePresence

Layout animations: single element reflow use layout prop on motion.div; cross-component shared transition use layoutId with same string on both elements; sync siblings that do not re-render together use LayoutGroup wrapper; details via motion_get_api LayoutGroup

Scroll-linked: progress bar or parallax use useScroll with useTransform; enter viewport use whileInView or useInView; details via motion_get_api useScroll

Physics and spring: bouncy feel use transition type spring with stiffness and damping; smooth follow use useSpring with a motionValue via motion_get_api useSpring; presets via motion_get_transitions

Gestures: hover and tap states use whileHover and whileTap with no JS event handlers needed; drag use drag prop and constrain with dragConstraints ref; custom drag trigger use useDragControls with dragListener false on element; details via motion_get_api useDragControls

Staggered lists: use variants on container and children; set delayChildren stagger 0.3 in parent variant transition; examples via motion_get_examples variants

Performance: animate transform and opacity only, avoid width height top left which triggers layout; pass scrollXProgress or scrollYProgress directly to style or via useTransform for GPU-accelerated scroll animations; examples via motion_get_examples performance
