# Issue tracker: Local Markdown

Issues and specs for this repo live as markdown files in `.scratch/`.

## Conventions

- One feature per directory: `.scratch/<feature-slug>/`
- The spec is `.scratch/<feature-slug>/spec.md`
- Implementation issues are one file per ticket at `.scratch/<feature-slug>/issues/<NN>-<slug>.md`, numbered from `01`, never a single combined tickets file
- Each issue file carries a plain `Status:` line near the top (see **Status values** below)
- Comments and conversation history append to the bottom of the file under a `## Comments` heading

## Status values

The `Status:` line holds exactly one value, from one of two sets:

- **Triage roles**: the strings in `triage-labels.md` (`needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`). `/triage` sets these.
- **Lifecycle states**: `claimed` (someone is working on it) and `resolved` (the work is done). `/implement` and `/wayfinder` set these. They replace the triage role once work starts, since a local file has no separate assignee or open/closed flag.

A ticket is **closed** when its Status is `resolved` or `wontfix`, and **open** otherwise. A blocker clears only when its Status is `resolved`; a `wontfix` blocker leaves its dependents blocked, so flag them to the user.

## When a skill says "claim the ticket"

Set `Status: claimed` and save before any work.

## When a skill says "resolve the ticket"

Set `Status: resolved` and save.

## When a skill says "close as wontfix"

Set `Status: wontfix` and append the reason under `## Comments`.

## When a skill says "publish to the issue tracker"

Create a new file under `.scratch/<feature-slug>/` (creating the directory if needed).

## When a skill says "fetch the relevant ticket"

Read the file at the referenced path. The user will normally pass the path or the issue number directly.

## Wayfinding operations

Used by `/wayfinder`. The **map** is a file with one **child** file per ticket.

- **Map**: `.scratch/<effort>/map.md` (the Notes / Decisions-so-far / Fog body).
- **Child ticket**: `.scratch/<effort>/issues/NN-<slug>.md`, numbered from `01`, with the question in the body. A `Type:` line records the ticket type (`research`/`prototype`/`grilling`/`task`); the `Status:` line carries a lifecycle state (see **Status values**).
- **Blocking**: a `Blocked by: NN, NN` line near the top. A ticket is unblocked when every file it lists is `resolved`.
- **Frontier**: scan `.scratch/<effort>/issues/` for files that are open, unblocked, and not `claimed`; first by number wins.
- **Claim**: claim the ticket (see above).
- **Resolve**: append the answer under an `## Answer` heading, resolve the ticket (see above), then append a context pointer (gist + link) to the map's Decisions-so-far in `map.md`.
