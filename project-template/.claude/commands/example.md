# Example Custom Command

This file is a template for creating custom slash commands in Claude Code.
Rename this file and edit the content below.

**How it works:** When you type `/example` in Claude Code, Claude receives the contents of this file as an injected prompt and executes accordingly.

---

## Usage

Type `/example` in Claude Code to run this command.

To create your own command:
1. Copy this file and rename it (e.g., `review-pr.md`, `standup.md`)
2. Replace the content below with your prompt
3. Use `$ARGUMENTS` as a placeholder if your command takes input

---

## Prompt (edit this section)

Perform a quick code review of the current changes in this repository. Focus on:

1. **Correctness** — does the logic do what it claims?
2. **Security** — any injection risks, exposed secrets, or unsafe operations?
3. **Simplicity** — is this the simplest solution? Would a future reader understand it?
4. **Tests** — are there test cases missing for edge cases?

Summarize findings as a bulleted list ordered by severity (high → low).
If there are no issues, say so clearly and suggest one potential improvement anyway.

$ARGUMENTS
