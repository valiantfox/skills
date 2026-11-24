---
name: implement-next
description: Implement the next logical task and commit it
---

Implement ONE ticket: the next unblocked one. 

Run each step. Each step is mandatory.

1. Spawn a subagent with fresh context calling the "implement" skill. 
2. Spawn two subagents with fresh context
  a. One calling the "code-review" skill.
  b. One calling the "spec-review" skill.
3. Spawn a subagent with fresh context to fix the findings.

Commit it separately, including only your changes and leaving earlier uncommitted changes uncommitted. Follow the project's commit style.

If tasks remain, tell me the recommended command to continue. Example: "Recommended Next: `@implement-next #87` to continue the effort"

