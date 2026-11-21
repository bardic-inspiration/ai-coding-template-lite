# Decisions

A log of the decisions this project has acted on, and why. Each entry is
added by the PR that acted on it. Newest first. How and when to add one:
[`AGENTS.md`](AGENTS.md) "Recording decisions".

<!-- Entry format — copy for each new decision, numbering upward:

## D-1 — Short name of the decision

`YYYY-MM-DD` · #PR · Accepted   (or: Superseded by D-n)

**Decision:** What was chosen, in a sentence or two.

**Why:** The reason — the constraint, goal, or evidence that settled it.

**Considered:** The alternatives, and why each lost. Omit if there were none.
-->

## D-6 — Record decisions in the PR that acts on them

`2026-11-21` · PR pending · Accepted

**Decision:** Every PR adds a `DECISIONS.md` entry for each decision it acts
on, including ones settled in chat, and lists them in its description.
Decisions that are discussed but never acted on are not logged.

**Why:** Chat is lost when a session ends, so a decision that shapes the code
but isn't written down is gone. Logging only acted-on decisions keeps the log
a record of the project as built, not of every idea discussed.

**Considered:** Logging decisions the moment they're made — rejected, because
it fills the log with choices that were later dropped.

## D-5 — Keep an explicit decision log file

`2026-11-21` · PR pending · Accepted

**Decision:** Decisions live in `DECISIONS.md`, with a `Why:` pointer from the
spec where needed.

**Why:** During early conceptual iteration, many decisions are made before
any code exists, and are hard to find in PR history.

**Considered:** The full template's approach — reasons only in PR
descriptions and squash commits, with no decision file.

## D-4 — Spikes are guarded by draft-PR status only

`2026-11-21` · PR pending · Accepted

**Decision:** A spike is a draft PR titled `spike: …`, closed unmerged. No CI
check blocks it.

**Why:** With one developer merging, the fact that a draft can't be merged is
guard enough.

**Considered:** The full template's `pr-title` check that fails spike PRs.

## D-3 — Tests for settled behavior; test-first is the default, not a rule

`2026-11-21` · PR pending · Accepted

**Decision:** Behavior that's settled ships with tests. Writing the test
first is the default, not a requirement.

**Why:** Early iteration involves exploratory code where strict test-first
slows learning; the `check` gate still guards merges.

**Considered:** Mandatory test-first, as in the full template.

## D-2 — One `check` gate in CI, run on every change

`2026-11-21` · PR pending · Accepted

**Decision:** CI is a single `gate` job running `check`. There's no
fast path that skips Markdown-only changes, and no PR-title check or
Dependabot.

**Why:** These are the basic checks before merging; the rest is upkeep a
solo early-stage project doesn't need yet.

**Considered:** Keeping the full template's docs-only detection, title
check, and Dependabot.

## D-1 — Lite template for one developer, one agent, one spec

`2026-11-21` · PR pending · Accepted

**Decision:** Pare the full template down to `AGENTS.md`, `SPEC.md`,
`DECISIONS.md`, `README.md`, `CLAUDE.md`, the CI gate, the PR template, and
the `ask-me` / `grill-me` skills.

**Why:** The goal is early conceptual iteration with tidy docs, recorded
decisions, and a basic merge check — not multi-contributor governance.

**Considered:** Kept nothing of: `docs/` (folded into `AGENTS.md`),
`CONTRIBUTING.md`, issue templates, plan/sub-issue workflow, the routine
queue, `modules/`, and the LLM Facts label.
