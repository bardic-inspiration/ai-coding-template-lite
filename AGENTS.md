# AGENTS.md — How to Work Here

The guide for any agent (or person) working in this repo. One developer, one
agent, one design document. [`SPEC.md`](SPEC.md) says **what to build**; this
file says **how to work**.

Sessions start with no memory of earlier ones. Anything the next session needs
— the design, decisions, open questions, follow-ups — goes into the repo, not
just the chat.

## The files

| File | Holds | Update it when |
|---|---|---|
| [`SPEC.md`](SPEC.md) | The design: purpose, concepts, behavior, open questions. Present tense. | The design changes — in the same PR as any code that follows from it. |
| [`DECISIONS.md`](DECISIONS.md) | A log of decisions and why they were made. | A choice is made that someone might later question or undo. |
| `README.md` | What the project is, and how to run it. | Setup or the one-paragraph pitch changes. |
| `AGENTS.md` | This guide. | The way of working changes. |

Add other docs only when one of these gets too long to read by section — for
example, split a large spec into `docs/spec/<area>.md` and keep `SPEC.md` as
the index.

## Rules

- **Don't guess at the design.** If the spec is silent, ambiguous, or looks
  wrong, stop and ask. Record the question in `SPEC.md` "Open questions";
  once answered, write the answer into the spec (and `DECISIONS.md` if it was
  a real choice) before building on it.
- **Spec and code agree on `main`.** A change to behavior updates `SPEC.md`
  in the same PR. If they disagree, one of them is wrong — fix that one.
- **Record decisions as they're made**, including ones settled in chat
  (below).
- **One concern per PR.** Out-of-scope ideas go in a follow-up issue or the
  spec's open questions, not into the current change and not into a `TODO`.
- **`check` is green before merging.** Never skip, disable, or weaken a test
  to get there.

## Working loop

1. **Read first:** the task, the relevant parts of `SPEC.md`, and recent
   entries in `DECISIONS.md`.
2. **Shape it if it's fuzzy.** Use the `ask-me` skill to form intent, or
   `grill-me` to stress-test a plan. Write what comes out into the spec.
3. **Branch from `main`.** Use `type/short-description` (`feat/login-form`),
   or the branch name your agent platform assigns.
4. **Build, with tests.** Behavior that's settled ships with tests; writing
   the test first is the default.
5. **Run `check`** (Commands, below).
6. **Open a PR** with a clear title and description (below). Fix CI if it
   goes red. The developer merges.

Changing only Markdown? Skip steps 4–5.

## Spikes

When the question is "would this work?" or "A or B?", spike it: throwaway
code on a `spike/<question>` branch, no tests or tidiness required. Open it
as a **draft PR** titled `spike: <question>` with the findings in the
description — question, what you tried, what worked, recommendation. Then
record the outcome in `SPEC.md` and `DECISIONS.md`, close the PR unmerged,
and rebuild the real thing through the working loop.

## Recording decisions

Add an entry to [`DECISIONS.md`](DECISIONS.md) when a choice:

- picks between real alternatives,
- would look arbitrary or tempting to reverse later, or
- changes or drops something the spec used to say.

Entries are short: what was decided, why, and what else was considered.
Newest at the top; never edit an old entry's substance — supersede it with a
new one and mark the old one `Superseded by D-n`. The spec states the
outcome; a rule that needs explaining can point to its entry (`See D-4.`).

## Pull requests and commits

PRs land by **squash merge**, so the PR title becomes the commit subject on
`main` and the description becomes its body.

- **Title:** a [Conventional Commits](https://www.conventionalcommits.org/)
  subject — `type(scope): imperative subject`, ≤ 72 characters. Types:
  `feat`, `fix`, `docs`, `test`, `refactor`, `chore`, `ci`, `build`.
- **Description:** fill in the
  [template](.github/pull_request_template.md) — what and why, decisions
  made, how it was tested. Delete the guidance comments.
- **Branch commits** don't reach `main`; any message that says what the step
  did is fine. Don't force-push a branch you've pushed — merge `main` in to
  catch up.

## Documentation style

- **Present tense.** Docs describe the project as it is now. History lives
  in git and `DECISIONS.md`; don't leave struck-through or "updated in v2"
  text behind.
- **One home per fact.** Other docs link to it rather than copying it.
- **Short and skimmable.** Every doc opens with a `# Title` and one line on
  what it's for. Link relatively, and cite sections by heading.
- **Naming:** root meta-files in `ALL-CAPS.md`; everything under `docs/` in
  `kebab-case.md`.

## Commands

| Task | Command |
|---|---|
| Install | `{{INSTALL_CMD}}` |
| **Check — the gate** | `{{CHECK_CMD}}` |
| Run one test, or a few | `{{TEST_CMD}}` |
| Run the project | `{{RUN_CMD}}` |

`check` runs everything a change must pass — lint, format check, typecheck,
tests, whatever the stack has — and never modifies files. CI runs the same
command, so green locally means green in CI.
