# CLAUDE.md

Claude Code–specific notes. [`AGENTS.md`](AGENTS.md) is the guide; Claude
Code loads only this file on its own, so it imports the guide here:

@AGENTS.md

## Watching PRs

After opening a PR, subscribe to its activity (`subscribe_pr_activity`) and
end the turn; CI results and review comments wake the session. Fix red CI on
the same branch. Unsubscribe once the PR is merged or closed. Don't watch a
spike's draft PR. Without that tool (a local session), run
`gh pr checks <number> --watch` before handing back.

## Configuration

| File | What it does |
|---|---|
| [`.claude/settings.json`](.claude/settings.json) | Pre-approves `check`, the test command, and read-only git. Blocks force-pushes and reading `.env` files. |
| [`.claude/hooks/session-start.sh`](.claude/hooks/session-start.sh) | In cloud sessions, installs dependencies at startup so `check` can run. |

## Skills

| Skill | When |
|---|---|
| [`ask-me`](.claude/skills/ask-me/SKILL.md) | The goal or scope is still fuzzy — interview to form intent. |
| [`grill-me`](.claude/skills/grill-me/SKILL.md) | A plan exists — stress-test it before building. |
