# Global Claude Code Rules
## Applies to every project and session

> See also: `COLLABORATOR.md` — defines how we work together as collaborators. Read it at the start of every session.

---

## Environment

- Always create a project-level virtual environment before installing any packages. Never install into the global Python environment
```
python -m venv .venv
source .venv/bin/activate
pip install <package>
```
- Prefer `uv` over `pip` when available — it's faster and produces cleaner dependency resolution
- Use `ruff` for linting and formatting on all Python projects

---

## Code Philosophy

- Build only what is explicitly asked for. No speculative features, no premature abstractions
- When replacing functionality, remove the old code — don't deprecate and leave it
- Boring and obvious beats clever. If it needs explanation, simplify it
- Single responsibility per function — if it's doing two things, split it
- Always place test files in a `/tests` folder at the project root. Never create test files alongside source code

---

## Code Discipline

- **Minimum surface area** — every code change should touch only what the problem requires. If a fix reaches beyond the direct problem area, stop and surface it as a checkpoint before proceeding — don't just explain after the fact
- **Root cause first** — identify the root cause before writing a single line. No patching symptoms. If the root cause is unclear, surface it at a checkpoint rather than guessing. Exception: explicit hotfixes requested by the human are allowed, but must be accompanied by an immediate follow-up to-do item to address the root cause properly
- **Never modify tests to make them pass** — fix the code, not the test. If the test itself is genuinely wrong, surface it as a checkpoint first and get agreement before changing it

---

## Project Setup

- At the start of every new project, create a `.claude/CLAUDE.md` file that defines scope, success criteria, architecture, and progress. This is the project-level source of truth. Do not wait to be asked — create it proactively as the first step.

---

## Git

- Always create a new branch per task. Never commit directly to main
- Commit after each meaningful, working unit of change — not at the end of a session
- Write commit messages that describe why, not just what

---

## Performance

- Always create a `.claudeignore` at the project root when a project has large dependency or build directories. This prevents Claude Code from indexing tens of thousands of irrelevant files and keeps searches fast.
- Standard entries to always include:

```
# Python
.venv/
__pycache__/
*.pyc

# Node
node_modules/
.next/

# Build / binary artifacts
dist/
build/
*.db
```

- Add project-specific noise (e.g. `output/`, `*.webm`) as needed.

---

## Platform

<!-- CUSTOMIZE: update to match your machine -->
- macOS (update version), Apple Silicon
- Default shell: zsh
- Python: use `python3` explicitly, never `python`
