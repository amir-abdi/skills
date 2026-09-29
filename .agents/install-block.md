# The canonical install block

One install story, one wording. `README.md`, `.changeset/*`, and every page under `docs/` must say **this** and nothing else. Change it here first, then propagate.

`amirabdi-skills` is **not** in Claude Code's official marketplace: this repo is a personal fork, so `.claude-plugin/marketplace.json` makes the repo its own single-plugin marketplace (`amirabdi`) and that marketplace has to be added before the plugin can be installed. Updates are a `/plugin update` away, not automatic.

## Claude Code: the plugin

<canonical-block name="claude-code">

```bash
claude plugin marketplace add amir-abdi/skills
claude plugin install amirabdi-skills@amirabdi
```

Or, from inside a session:

```
/plugin marketplace add amir-abdi/skills
/plugin install amirabdi-skills@amirabdi
```

It installs the promoted set as a read-only bundle. Pull later changes with `/plugin update amirabdi-skills`.

</canonical-block>

## Codex, and other agents: skills.sh

The plugin is Claude Code only. Everywhere else, [skills.sh](https://skills.sh) copies editable skill files into the project. It reads the GitHub repo directly, so no registry listing is needed. Use the whole-set form on `README.md`:

<canonical-block name="skills-sh-whole-set">

```bash
npx skills@latest add amir-abdi/skills
```

Pick the skills you want, and which coding agents to install them on. **The installer lets you choose which skills to take: make sure `setup-amirabdi-skills` is one of them.**

</canonical-block>

…and the single-skill form wherever one skill is named on its own. Note that **`docs/` pages are not a consumer of this block**: the docs site renders the install widget above the body, so a page that writes the commands out duplicates it. See [writing-docs.md](./writing-docs.md).

<canonical-block name="skills-sh-one-skill">

```bash
npx skills@latest add amir-abdi/skills --skill=<name>
```

```bash
npx skills@latest update <name>
```

</canonical-block>

`skills@latest` is the pinned spelling in all three. The pages under `docs/` used to carry their own copy of these commands; those blocks are now deleted rather than corrected, because the site renders the install commands itself.

## Working on this repo, not installing it

`scripts/link-skills.sh` symlinks every skill outside `deprecated/` and `misc/` into `~/.claude/skills` and `~/.agents/skills`. That is the route to use on the machine where this repo is checked out: edits land live and a `git pull` updates every installed skill. It is not one of the two install routes below, and it must not be mixed with them.

## The two routes are exclusive

The plugin is a managed, read-only bundle you subscribe to. skills.sh writes files you own and edit. Installing both leaves the user with every skill twice: always say "pick one".
