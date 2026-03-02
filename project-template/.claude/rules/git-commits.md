# Git Commit Rules

## When These Rules Apply

These rules apply whenever writing or reviewing git commit messages.

---

## Format

Every commit message must follow Conventional Commits:

```
<type>(<scope>): <short description>

[optional body]

[optional footer]
```

- **type**: `feat`, `fix`, `refactor`, `test`, `docs`, `chore`, `perf`
- **scope**: the module or area affected (optional but encouraged)
- **short description**: imperative mood, lowercase, no period, ≤72 chars

---

## Rules

### Subject Line
- Use imperative mood: "add", "fix", "remove" — not "added", "fixes", "removing"
- Describe *why* the change exists when the reason isn't obvious from the what
- ≤72 characters

### Body (when needed)
- Wrap at 72 characters
- Explain the motivation — what problem does this solve?
- Note trade-offs or alternatives considered

### Never Do
- Never commit directly to `main`
- Never use vague messages: "fix bug", "update", "WIP", "misc changes", "tweaks"
- Never bundle unrelated changes in a single commit — one logical change per commit
- Never use `--no-verify` to skip hooks unless explicitly instructed by the human

---

## Examples

### Correct

```
feat(auth): add token refresh on 401 response

Prevents users from being silently logged out mid-session.
Tokens now auto-refresh if expiry is within 5 minutes.
```

```
fix(url-builder): include mapBounds in searchQueryState

Zillow returns empty results when mapBounds is absent, even
when other filters are correct. This was the root cause of
the empty listing responses seen in production.
```

### Incorrect

```
fixed stuff
update auth
WIP
added some things
```
