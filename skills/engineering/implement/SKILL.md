---
name: implement
description: "Implement a piece of work based on a spec or set of tickets."
disable-model-invocation: true
---

Implement the work described by the user in the spec or tickets.

Use /tdd where possible, at pre-agreed seams.

Run typechecking regularly, single test files regularly, and the full test suite once at the end.

As you make progress in the ticket, tick the `- [ ]` boxes as complete and add a note **[marked by agent]** to the line.

Once done, use /two-axis-review to review the work.

Open the most important file in VS Code and also print the color-coded diff changes you applied to that file in the terminal.

Ask the user to approve the task as complete. If they ask for changes instead, make them and re-run /two-axis-review before asking again.

Once they approve:

- If using local markdown issue tracker, mark the ticket as complete.
- Commit your work to the current branch.
