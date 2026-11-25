---
name: fox-next
description: Perform the next logical task
---

If tasks remain, use the invocation arguments and session context to pick the next task, then run its command.

If there is neither, check the issue tracker (see `docs/agents/issue-tracker.md`), suggest the next command, and wait for the user. Don't run it.

Examples of next commands:

- If a ticket from a plan is next: `@fox-plan <plan-number> <ticket-number>`
- If an implementation ticket is next: `@fox-implement <ticket-number>`
- For a standalone refinement that is not part of a plan: `@fox-refine`
- For a completed spec: `@fox-to-tickets`

If no tickets remain on a plan and its **Not yet specified** section is empty, the plan is finished. Ask the user whether to close it, and close it on yes.
