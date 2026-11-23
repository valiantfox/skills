---
name: Implement all
description: Implements a whole workload
---

Implement ALL tickets on a single **integration branch**. The tickets are a **task graph** with blocking relationships, so there is always a **frontier** of unblocked tickets ready to be grabbed.

Start every subagent with a fresh context window. Communicate through **context pointers** (spec, tickets, previous commits), not copied text.

## Steps

1. Read the spec and tickets to understand the task graph.

2. Create the integration branch from the current branch.

3. For each ticket on the frontier, spawn a fresh **implementer subagent** in the background, in its own worktree on its own branch based on the integration branch. Each implementer:
   - calls the "implement" skill for its ticket;
   - commits separately, including only its changes and leaving earlier uncommitted changes uncommitted, following the project's commit style;
   - rebases its branch onto the integration branch tip before reporting done, and reruns the tests if the rebase pulled in new commits.

4. When an implementer finishes, fast-forward the integration branch to its branch. If the integration branch moved in the meantime, rebase again first. Never create merge commits.

5. If the frontier changed, spawn implementers for the newly unblocked tickets.

6. Once all tickets are done, call the Skill tool with "code-review" and then "spec-review" on the integration branch. Fix everything they raise in a single fresh implementer subagent.

7. Resolve each ticket the way the issue tracker closes work, report the integration branch, and clean up all worktrees.
