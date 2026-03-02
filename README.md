# Claude Code Starter Kit

A portable setup for kicking off any project with Claude Code — structured, opinionated, and ready to customize.

---

## What's In Here

```
shareables/
├── README.md                        ← you are here
├── global/
│   └── CLAUDE.md                    ← drop into ~/.claude/CLAUDE.md
└── project-template/
    ├── .claudeignore                 ← drop into project root
    └── .claude/
        ├── CLAUDE.md                ← project context (fill in the blanks)
        ├── COLLABORATOR.md          ← how to work with Claude
        ├── commands/                ← custom slash commands (/do-thing)
        │   └── example.md
        ├── agents/                  ← custom subagent definitions
        │   └── example.md
        └── rules/                   ← domain-specific rule files
            └── example.md
```

---

## Setup Steps

### 1. Global config (one-time per machine)

```bash
cp global/CLAUDE.md ~/.claude/CLAUDE.md
```

Edit it: update your OS, shell, and any tool preferences. This applies to **every project** on your machine.

### 2. Project config (once per project)

From your new project root:

```bash
cp -r project-template/.claude ./.claude
cp project-template/.claudeignore ./.claudeignore
```

Then edit `.claude/CLAUDE.md`:
- Fill in project name, description, tech stack
- Define your success criteria and architecture
- Add repo structure as it grows

### 3. Customize as you go

- Add custom slash commands to `.claude/commands/` (run with `/command-name` in Claude Code)
- Add agent definitions to `.claude/agents/`
- Add rule files to `.claude/rules/` for domain-specific constraints Claude should always follow

---

## How the Files Work

| File | Scope | Purpose |
|------|-------|---------|
| `~/.claude/CLAUDE.md` | Global (all projects) | Environment, code philosophy, git workflow |
| `.claude/CLAUDE.md` | Project | Architecture, current state, key decisions |
| `.claude/COLLABORATOR.md` | Project | Working relationship norms, tone, checkpoints |
| `.claude/commands/*.md` | Project | Custom slash commands (type `/filename` in Claude) |
| `.claude/agents/*.md` | Project | Specialized subagents for repeated tasks |
| `.claude/rules/*.md` | Project | Domain constraints Claude always applies |
| `.claudeignore` | Project | Tells Claude what NOT to index (keeps searches fast) |

---

## Tips

- Keep `CLAUDE.md` updated as the project evolves — it's Claude's source of truth
- Commit `.claude/` to git so the whole team shares the same context
- Never put secrets in `.claude/` files — they're read by Claude and may end up in context
- The `.claudeignore` is especially important for monorepos and projects with large `node_modules` or `.venv` dirs
