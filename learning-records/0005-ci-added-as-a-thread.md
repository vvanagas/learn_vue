# GitHub Actions CI added — as a thread, not a phase

The learner asked for GitHub Actions to be taught as part of the course. It was
added to [[LEARNING-PLAN.md]] as a ~30 h **thread** woven through Phases 2-7
rather than as an eighth phase, and one success criterion was added to
[[MISSION.md]]: the checks run in CI where red blocks the merge.

**Why threaded.** CI has no single right moment. Taught at Phase 2 alone it is a
toy — nothing worth checking exists yet. Taught only at Phase 7 it arrives after
the habits it exists to enforce have already set. Its value arrives in five
instalments, each attached to the thing that just became worth guarding: the
first typecheck (2), the first pull request (4), the first real database (5A),
the first ruleset (6), the first deploy (7).

**Why it costs no calendar change.** Ten months at 4 h/weekday is ~840 h
nominal; the phases budget 816 h. The thread consumes that ~24 h of slack and
runs ~6 h past nominal — a day and a half against a ten-month estimate. Recorded
rather than hidden, but not treated as a mission-level decision the way the
FastAPI backend was (see [[0003-application-named-and-backend-adopted]]).

**The through-line, and the reason Phase 6 is the anchor.** `coding-rules` tags
rules `[auto]`, `[review]` or `[advisory]`, and `binding-vue` states that a red
linter *is* the violation. That sentence is false until something red blocks
something: on a laptop a failing lint is a suggestion you can commit past.
Required status checks are what convert the `[auto]` tier from a claim into a
mechanism.

**The half that matters more.** CI cannot enforce `[review]`. No runner can
verify that a test was watched failing, for the right reason, before the code
existed — the Iron Law's proof is a captured RED run in the task record, which
is a discipline, not a pipeline. Teaching CI without teaching this produces
someone who reads green as compliant. The exit criterion is written to force the
distinction: say out loud which rules the pipeline enforces and which it merely
watched you claim.

**Teaching hook, verified rather than assumed.** The repository already runs CI
that nobody wrote — `pages build and deployment` has run on every push since
Pages was enabled on 2026-07-30. The first lesson therefore starts by *reading* a
real run instead of writing YAML, which suits a learner who has spent twenty
years reading systems rather than following recipes (see
[[0001-prior-knowledge-and-the-real-gap]]).

**Security is threaded too, not appended.** A workflow is a program running with
your credentials, on someone else's machine, triggered by events other people
influence. Script injection through `${{ }}` interpolation of untrusted context
is CR-4.3's boundary rule wearing YAML, and the mitigation — an intermediate
`env:` variable — is the same move as narrowing at the boundary. Sourced from
GitHub's own "Secure use reference", now in [[RESOURCES.md]].

Cross-links: [[MISSION.md]], [[LEARNING-PLAN.md]], [[RESOURCES.md]]
