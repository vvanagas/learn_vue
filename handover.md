---
type: Handover
title: Session handover — 2026-07-30/31
description: What a fresh session needs that is not already written down elsewhere, plus the map to everything that is.
status: stable
generated: { by: claude/opus-5, at: 2026-07-31T17:30:00Z }
verified: { by: claude/opus-5, at: 2026-07-31T17:30:00Z }
stale_after: 2026-09-30
---

# Session handover

**Read this, then verify it against `git log` and the actual files.** It is
point-in-time and can be wrong. Everything below was true at the SHAs named.

Most durable state is already recorded in the workspace — this document
deliberately does **not** duplicate it. It carries the map, the traps, and the
things that existed only in one session's context.

## The one next action

**Run `/teach` in `C:\darbas4\learn_vue` and author lesson `0001`** — Phase 1,
the browser layer: hand-written HTML and CSS, no Vue, no build tools.

Nothing blocks it. Mission, plan, resources and backlog are all settled.
`lessons/`, `reference/` and `assets/` are **empty** — after two days of work,
zero lessons exist. That is the single most important fact in this file. The
session built a great deal of scaffolding and no teaching.

`/teach` is `disable-model-invocation` — the user types it; an agent cannot.

## Repository state

| Repo | Branch | SHA | Notes |
|---|---|---|---|
| `vvanagas/learn_vue` | `main` | `c91d1f8` | public — the course workspace |
| `vvanagas/claude-config` | `main` | `a04bd7a` | **private** — global rules under version control |
| `vvanagas/coding-rules` | `master` | `aea1df6` | public — the ruleset, 5 bindings |
| `vvanagas/skills` | `teach-workspace-fixes` | `87b0669` | fork of `mattpocock/skills`, 4 commits ahead, **unmerged upstream by choice** |

All four were in sync with GitHub and had clean working trees at handover.

## Where the durable state already lives — do not re-derive

- **`NOTES.md`** (105 lines) — learner background, budget, teaching
  preferences, environment, standing decisions, and the `NEXT:` line. Read at
  the start of every session; kept deliberately short for that reason.
- **`pending/`** — 14 OKF items, one file each, with `state` / `trigger` /
  `owner`. Start at `pending/index.md`. Nothing there blocks a lesson.
- **`docs/`** — three reference concepts: `coding-rules-precedence.md`,
  `phone-access.md`, `teach-skill-review.md`.
- **`learning-records/`** — 5 records, dated, ADR-style.
- **`MISSION.md` / `LEARNING-PLAN.md`** — the mission and the ~816 h / 8-phase
  plan, including the Definition of Done and the CI thread.
- **`history.txt`** — 2036 lines, 23 entries, the mechanical ledger. **It is
  git-ignored and exists only on this machine.** Do not look for it in a clone.
- **Memory** — `~/.claude/projects/C--darbas4-learn-vue/memory/`, 3 notes plus
  `MEMORY.md`. This is the only auto-loaded surface.

## Traps that will bite a fresh session

1. **The Edit tool refuses to write through symlinks.** `~/.claude/CLAUDE.md`
   is a symlink into `claude-config`. Edit
   `C:\darbas4\claude-config\CLAUDE.md` directly. Reads through the symlink are
   fine.
2. **`history.txt` is git-ignored.** It is a desk artifact — PC paths, PC
   ledger. A cloud session cannot see or append to it; phone work lands in git
   and gets its ledger entry on the next PC session.
3. **`coding-rules`: personal overrides project.**
   `~/.claude/skills/coding-rules/` is what loads, everywhere. The vendored copy
   in this repo is inert on this machine and exists for portability. Do not read
   the vendored copy to learn which rules are in force.
4. **Memory is per project.** `~/.claude/projects/<slug>/memory/`. Do not
   hardcode another project's path.
5. **The installed `teach` skill is a patched fork**, not upstream — 9 changes
   across 4 commits. Upstream `mattpocock/skills` has not moved since the fork.
6. **Pester 3.4.0 and 6.0.1 are both installed.** Import 6 explicitly:
   `Import-Module Pester -MinimumVersion 6.0.0 -Force`.

## Findings that generalise — the actual value of the session

**Policy without mechanism.** Repeatedly, a rule was written and nothing
carried it out. The teach review's central charge, and it was fair. Test: after
writing any rule, ask *what executes this?* If the answer is "the agent will
remember", it is not a rule yet.

**Authoring is not shipping.** Three times an artifact was "done" but not in
the copy that actually loads — `binding-vue`'s router entry, the `coding-rules`
local delta, the `teach` fixes needing installation. Change what loads, then
read it back.

**Vacuous tests.** Three tests passed with the implementation entirely absent
(`Should -Throw` satisfied by `CommandNotFoundException`; an assertion on an
empty directory). Invisible once the code exists. The prophylactic is in
superpowers' `writing-good-tests.md`: *name the production change that would
make this test fail* — before writing the body.

**Self-review caught nothing.** Every genuine defect this session was found by
something outside the working context: an external review document, a mutation
check, the npm registry, the Vue docs, or the user. Not once did re-reading my
own work with my own context intact surface my own error.

**Two kinds of drift need two mechanisms.** Implementation ↔ spec is caught by
a fresh-context reviewer given only the spec and the diff. Spec ↔ reality is
caught only by checking the spec against the source. The Vue 3.5 correction
would have passed any conformance review.

## Corrections made mid-session — do not re-adopt the wrong version

- **`coding-rules` precedence**: personal overrides project. My first
  recommendation was the exact inverse and was acted against.
- **OKF is a real Google Cloud spec** (Apache-2.0, v0.2), not a local
  convention. I asserted the latter from a directory listing.
- **Vue 3.5 made props destructure reactive.** The corpus's "reactivity loss via
  destructuring" predates it; copied verbatim it forbids correct code. Corrected
  in `binding-vue` V-2, in the corpus (`client-controls.txt` v0.2), and recorded
  in `client-corpus-open-issues.txt` OI-01.
- **`gh` reported `license=none` for two repos** because of a malformed jq
  query, not because they are unlicensed. Both are MIT/Apache-2.0.

## Open threads with resume context

- **`pending/0002`** — a Tier-2 enforcement tier for `coding-rules`:
  deterministic checks that are not linters. A **decision**, not a task; build it
  in the Phase 2 CI thread first, upstream only if earned.
- **`pending/0008`** — CR-7.5 "migrations are forward-only" vs "every migration
  has a tested down path". Reconcilable; settle it against a real migration at
  Phase 5A.
- **`pending/0001`** — upstreaming the `teach` fixes: split into a small
  defect PR and an issue for the design opinions. Costs nothing until upstream
  moves.
- **`claude-config`** — one behaviour is knowingly unprotected: the mutation
  check shows a plain `Copy-Item` passes all 26 tests, because they describe a
  copy rather than an *atomic* copy. Recorded in the test file and README rather
  than closed with a flaky timing test.
- **`check-drift.ps1`** — the IO/presentation shell has no automated tests; its
  contract was verified manually across nine paths. The pure core
  (`DriftCore.ps1`) has 26.

## What was verified vs assumed

**Verified against a source:** skill precedence, GitHub plan and Pages
constraints, cloud-session limits, Vue 3.5 props behaviour, both a11y package
versions on npm, OKF's spec text, every repo SHA, and every `RED`/`GREEN` in the
TDD rebuild.

**Assumed and still unverified:** the Claude account plan (Pro/Max/Team — cloud
sessions depend on it, `pending/0006`); five corpus files never read
(`pending/0010`); the performance pack never read (`pending/0012`).
