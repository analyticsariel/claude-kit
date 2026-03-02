# Claude Code Starter Kit

A portable setup for kicking off any project with Claude Code — structured, opinionated, and ready to customize.

---

## What's In Here

```
claude-kit/
├── README.md                        ← you are here
├── global/
│   ├── CLAUDE.md                    ← drop into ~/.claude/CLAUDE.md
│   ├── COLLABORATOR.md              ← drop into ~/.claude/COLLABORATOR.md
│   └── memory/
│       └── MEMORY.md                ← drop into ~/.claude/memory/MEMORY.md
└── project-template/
    ├── .claudeignore                 ← drop into project root
    └── .claude/
        ├── CLAUDE.md                ← project context (fill in the blanks)
        ├── commands/                ← custom slash commands (/do-thing)
        │   └── example.md
        ├── agents/                  ← custom subagent definitions
        │   ├── code-reviewer.md     ← reviews code before committing
        │   ├── debugger.md          ← diagnoses root causes
        │   └── example.md           ← blank template
        └── rules/                   ← domain-specific rule files
            ├── git-commits.md       ← conventional commits format
            ├── security.md          ← security constraints
            └── example.md           ← blank template
```

---

## Setup Steps

### 1. Global config (one-time per machine)

```bash
cp global/CLAUDE.md ~/.claude/CLAUDE.md
cp global/COLLABORATOR.md ~/.claude/COLLABORATOR.md
mkdir -p ~/.claude/memory
cp global/memory/MEMORY.md ~/.claude/memory/MEMORY.md
```

Edit each file: update your OS, shell, tool preferences, and working style. These apply to **every project** on your machine.

### 2. Project config (once per project)

From your new project root:

```bash
cp -r path/to/claude-kit/project-template/.claude ./.claude
cp path/to/claude-kit/project-template/.claudeignore ./.claudeignore
```

Then edit `.claude/CLAUDE.md`:
- Fill in project name, description, tech stack
- Define your success criteria and architecture
- Add repo structure as it grows

### 3. Customize as you go

- Add custom slash commands to `.claude/commands/` (run with `/command-name` in Claude Code)
- Add agent definitions to `.claude/agents/`
- Add rule files to `.claude/rules/` for domain-specific constraints Claude should always follow
- Update `~/.claude/memory/MEMORY.md` with patterns and preferences that should persist across sessions

---

## How the Files Work

| File | Scope | Purpose |
|------|-------|---------|
| `~/.claude/CLAUDE.md` | Global | Environment, code philosophy, git workflow |
| `~/.claude/COLLABORATOR.md` | Global | Working relationship norms, tone, checkpoints |
| `~/.claude/memory/MEMORY.md` | Global | Persistent facts and preferences across sessions |
| `.claude/CLAUDE.md` | Project | Architecture, current state, key decisions |
| `.claude/commands/*.md` | Project | Custom slash commands (type `/filename` in Claude) |
| `.claude/agents/*.md` | Project | Specialized subagents for repeated tasks |
| `.claude/rules/*.md` | Project | Domain constraints Claude always applies |
| `.claudeignore` | Project | Tells Claude what NOT to index (keeps searches fast) |

---

## Tips

- Keep `.claude/CLAUDE.md` updated as the project evolves — it's Claude's source of truth
- Commit `.claude/` to git so the whole team shares the same context
- Never put secrets in `.claude/` files — they're read by Claude and may end up in context
- The `.claudeignore` is especially important for monorepos and projects with large `node_modules` or `.venv` dirs
- Update `~/.claude/memory/MEMORY.md` whenever you establish a pattern worth keeping — Claude reads it at the start of every session
