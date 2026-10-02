---
name: implement
description: "Implement a piece of work based on a spec or set of tickets."
disable-model-invocation: true
---

Implement the work described by the user in the spec or tickets.

If the work is a ticket on the issue tracker, claim it (set its `claimed` lifecycle state, as the tracker config describes) before writing any code.

Use /tdd where possible, at pre-agreed seams.

Run typechecking regularly, single test files regularly, and the full test suite once at the end.

As you make progress in the ticket, tick the `- [ ]` boxes as complete and add a note **[marked by agent]** to the line.

Once done, use /two-axis-review to review the work.

Open the most important file in VS Code and also print the color-coded diff changes you applied to that file in the terminal.

Ask the user to approve the task as complete. If they ask for changes instead, make them and re-run /two-axis-review before asking again.

Once they approve:

- If the work is a ticket on the local markdown tracker, resolve it (`Status: resolved`) so the change lands in the commit.
- Commit your work to the current branch.
- If the work is a ticket on any other tracker, resolve it now (set its `resolved` lifecycle state, as the tracker config describes; on GitHub or GitLab that closes the issue, linking the commit).
