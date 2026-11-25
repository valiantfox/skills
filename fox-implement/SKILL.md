---
name: fox-implement
description: Implement the next logical task and commit it
---

This skill has two modes:
- If a ticket is given: Implement that ticket
- If a spec was provided: Implement that spec
- Otherwise ask the user to provide a ticket or spec

Run each step. Each step is mandatory.

1. **Implementing:** Spawn a subagent with fresh context calling the "fox-write-code" skill.
2. **Reviewing:** Spawn two subagents with fresh context
  a. One calling the "fox-code-review" skill.
  b. One calling the "fox-spec-review" skill.
3. **Fixing:** Spawn a subagent with fresh context to fix the findings.

Commit it separately, including only your changes and leaving earlier uncommitted changes uncommitted. One ticket, one commit. Follow the project's commit style.

Close the ticket.

If tasks remain, tell the user the recommended command to continue. Example: "Recommended Next: `@fox-implement #87` to continue the effort"
