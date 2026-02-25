<div align="center">

# Context Engineering for Creators

**The patterns behind auto-activating AI coding agents**

*How to build AI systems that load the right knowledge at the right time — without manual prompt management.*

[![Context Engineering](https://img.shields.io/badge/context_engineering-patterns-blue?style=for-the-badge)](#patterns)
[![Claude Code](https://img.shields.io/badge/Claude_Code-compatible-emerald?style=for-the-badge)](https://docs.anthropic.com)
[![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](LICENSE)

</div>

---

## What Is Context Engineering?

Context engineering is the discipline of designing systems that dynamically construct the right context for AI models. Instead of writing better prompts, you build systems that assemble the right information automatically.

> "The hottest new programming paradigm is not prompting. It's context engineering." — Andrej Karpathy

## The Three Pillars

### 1. Skill Activation (What to Load)

Skills are domain knowledge files that auto-activate based on signals:

```
Signal: User opens a .tsx file
→ System loads: react-patterns, typescript-docs skills

Signal: User mentions "blog post"
→ System loads: article-creator, seo-fundamentals skills

Signal: User types "ultrawork"
→ System loads: multi-agent swarm orchestration
```

**Implementation pattern:**

```javascript
// skill-activation.js — runs on UserPromptSubmit
const signals = {
  filePatterns: { '*.tsx': ['react-patterns', 'typescript-docs'] },
  keywords: { 'blog': ['article-creator', 'seo-fundamentals'] },
  magicWords: { 'ultrawork': ['swarm-orchestration'] }
};
```

### 2. Memory Injection (What to Remember)

Three-tier memory architecture:

| Tier | Persistence | Use Case |
|------|-------------|----------|
| **Session** | Current conversation | Working state, current task |
| **Project** | MEMORY.md files | Patterns, conventions, decisions |
| **Global** | Intelligence system | Cross-project insights |

### 3. Lifecycle Hooks (When to Act)

Hooks intercept AI tool usage at key moments:

```
SessionStart     → Load previous state + activate skills
UserPromptSubmit → Match keywords → inject relevant context
PreToolUse       → Quality gate before edits
PostToolUse      → Learn from outcomes
PreCompact       → Preserve critical context
Stop             → Save state for next session
```

## Patterns

### Pattern 1: Progressive Disclosure

Don't load everything at once. Load context progressively as the AI needs it.

```
Level 0: CLAUDE.md (always loaded, <200 lines)
Level 1: Skill rules (keyword → skill mapping)
Level 2: Full skill files (loaded on activation)
Level 3: Reference docs (loaded on demand)
```

### Pattern 2: Context Budget Management

Track how much context you're using and optimize:

```javascript
// context-budget-tracker.ts
const BUDGET = {
  skills: 0.3,      // 30% for domain knowledge
  codebase: 0.4,    // 40% for relevant code
  conversation: 0.2, // 20% for chat history
  system: 0.1       // 10% for system prompts
};
```

### Pattern 3: Skill Routing

Route requests to specialized agents based on complexity:

```
Simple task (1-2 keywords) → Single skill activation
Medium task (3+ keywords)  → Skill chain
Complex task (magic word)  → Multi-agent swarm
```

### Pattern 4: Learning Loops

Track what works and feed it back:

```
Action → Outcome → Pattern → Future Context
  ↑                              |
  └──────────────────────────────┘
```

## Apply to Your Projects

### Quick Start

1. Create `.claude/skills/` with domain knowledge files
2. Create `.claude/hooks/skill-activation-prompt.sh` for auto-loading
3. Add `CLAUDE.md` with project conventions
4. Add `MEMORY.md` for cross-session patterns

### Full System

Install the [Agentic Creator OS](https://github.com/frankxai/agentic-creator-os) — 90+ skills, 15 hooks, and the complete context engineering system pre-built.

```bash
git clone https://github.com/frankxai/agentic-creator-os.git ~/.acos
cd ~/.acos && ./install.sh
```

## Further Reading

- [ACOS: The Operating System for AI Creators](https://github.com/frankxai/agentic-creator-os)
- [Claude Code Hooks](https://github.com/frankxai/claude-code-hooks) — The hook system
- [ACOS Plugin Marketplace](https://github.com/frankxai/agentic-creator-skills) — 8 domain plugins
- [FrankX.AI](https://frankx.ai) — Creator hub

## License

MIT
