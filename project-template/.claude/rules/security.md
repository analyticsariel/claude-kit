# Security Rules

## When These Rules Apply

These rules apply whenever writing code that handles user input, authentication, data storage, external APIs, or environment configuration.

---

## Rules

### Secrets and Credentials
- Never hardcode API keys, tokens, passwords, or secrets in source code
- Always read secrets from environment variables or a secrets manager
- Never log or print secret values, even in debug mode
- Never commit `.env` files — only commit `.env.example` with placeholder values

### Input Validation
- Validate all user input at the system boundary before it touches business logic
- Never pass raw user input to SQL queries, shell commands, file paths, or HTML
- Sanitize and encode output appropriate to its context (HTML, JSON, SQL)

### Authentication and Authorization
- Never roll your own auth — use established libraries
- Always check authorization, not just authentication
- Fail closed: if a permission check fails or throws, deny access

### Dependencies
- Never install packages from untrusted or unknown sources
- Flag any new external dependency at a checkpoint before adding it
- Prefer packages with active maintenance and a clear security track record

### Never Do
- Never expose stack traces or internal error details to end users
- Never store passwords in plain text — always hash with bcrypt or argon2
- Never disable SSL/TLS verification, even temporarily in development
- Never use `eval()` or equivalent with user-supplied input

---

## Examples

### Correct

```python
import os

api_key = os.environ["API_KEY"]  # read from environment
```

```python
# Parameterized query — safe from SQL injection
cursor.execute("SELECT * FROM users WHERE id = ?", (user_id,))
```

### Incorrect

```python
api_key = "sk-abc123..."  # hardcoded — never do this
```

```python
# String interpolation in SQL — injection risk
cursor.execute(f"SELECT * FROM users WHERE id = {user_id}")
```
