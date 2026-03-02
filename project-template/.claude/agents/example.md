---
name: example-agent
description: >
  Use this agent when you need to [describe the specific task this agent handles].
  Example: "searching for code patterns across the codebase" or "running and interpreting test output".
  Trigger it explicitly: "use the example-agent to..."
tools:
  - Read
  - Grep
  - Glob
  - Bash
---

# Example Agent

<!-- Rename this file and customize the frontmatter + prompt below. -->

## Purpose

This agent handles [specific task]. Use it when [condition that should trigger this agent].

## Instructions

You are a specialized agent for [task domain]. Your job is to [clear objective].

When called:
1. [Step 1 — what to do first]
2. [Step 2 — what to analyze or produce]
3. [Step 3 — how to return results]

Always return your findings in this format:
- **Finding**: [what you found]
- **Location**: [file:line if applicable]
- **Recommendation**: [what to do about it]

If you find nothing relevant, say so explicitly rather than guessing.
