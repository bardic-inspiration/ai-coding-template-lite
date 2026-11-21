# Using This Template

How to start a new project from this template. Delete this file once done.

## What's in the box

| Path | Purpose |
|---|---|
| [`AGENTS.md`](AGENTS.md) | How to work: rules, working loop, spikes, decisions, PRs, commands. |
| [`SPEC.md`](SPEC.md) | The design document skeleton. |
| [`DECISIONS.md`](DECISIONS.md) | The decision log. |
| [`CLAUDE.md`](CLAUDE.md) | Imports `AGENTS.md` for Claude Code; adds tool specifics. |
| [`README.md`](README.md) | Project README skeleton. |
| [`.github/`](.github/) | The CI gate and the PR template. |
| [`.claude/`](.claude/) | Permissions, the cloud-session hook, and the `ask-me` / `grill-me` skills. |

## Conventions

`{{UPPER_SNAKE}}` is a value to fill in. `<!-- TEMPLATE: … -->` (or
`# TEMPLATE:` in YAML and shell) is guidance: act on it, then delete it. Find
what's left:

```bash
grep -rnE '\{\{[A-Z_0-9]+\}\}|TEMPLATE:' --exclude-dir=.git .
```

## Adopting

1. **Create the repo** from this template.
2. **Write the spec** — start with purpose, non-goals, and open questions.
   The design and the stack can wait; `ask-me` helps here.
3. **When there's code to check, wire up the stack:**
   - define `check` in the stack's task runner, and fill in `AGENTS.md`
     "Commands" and `.claude/settings.json`;
   - replace the placeholder step in `.github/workflows/ci.yml` with
     toolchain setup, install, and `check`;
   - add the install step to `.claude/hooks/session-start.sh`;
   - add the toolchain's entries to `.gitignore`.
4. **Clear `DECISIONS.md`** down to its header and entry format — the
   entries there record how this template was built, not your project.
5. **Fill the remaining placeholders**, delete this file and the README
   banner, and run the grep above until it returns nothing.

## GitHub settings

- **Pull Requests:** allow only **squash merging**, with the default message
  "Pull request title and description." Turn on "Automatically delete head
  branches."
- **Branch ruleset on `main`:** require a pull request (0 approvals) and the
  `gate` status check; block force pushes.
