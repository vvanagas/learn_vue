---
okf_version: "0.2"
---

# Pending

Open work for the `learn_vue` course and the rulesets it depends on. An
[OKF](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
bundle: one concept per item, `type: Pending`, frontmatter carrying `state`,
`trigger` and `owner` as producer extensions.

**Nothing here blocks a lesson.** Each item names the condition that fires it, so
the list can be ignored safely until reality arrives. `history.txt` records what
ran; this records what has not run yet and when it would matter.

Numbers are creation order and permanent — they get cited from commit messages,
so they never renumber. Priority is not the number. Closing an item means setting
`state: done` and naming the commit that closed it, never deleting the file.

# Fires at a known phase

* [0005 — Vendor binding-python.txt](0005-vendor-binding-python.md) - the Python binding is missing from the vendored copy; Phase 5A.
* [0008 — Reconcile CR-7.5 forward-only](0008-cr75-forward-only-wording.md) - forward-only vs a tested down path; settle against a real migration, Phase 5A.
* [0007 — Fill the CR-13.4 exemplar slots](0007-cr134-exemplar-slots.md) - needs real code; Phase 4 produces it, Phase 6 promotes it.
* [0002 — A Tier-2 enforcement tier](0002-tier2-enforcement-tier.md) - deterministic checks that are not linters; build in the Phase 2 CI thread, upstream only if earned.
* [0006 — Verify the Claude plan](0006-verify-claude-plan.md) - cloud sessions are Pro/Max/Team only; check before phone hand-off matters.

# Fires on a symptom or an event

* [0012 — Read the performance pack](0012-read-performance-pack.md) - read it against a slow page, not in the abstract; Core Web Vitals is the wrong frame for an internal tool.
* [0001 — Upstream the teach fixes](0001-upstream-teach-fixes.md) - split into a small defect PR and an issue; costs nothing until upstream moves.
* [0010 — Read the remaining corpus files](0010-read-remaining-corpus-files.md) - archetype-stage-dissection holds the 12-stage pipeline everything else is expressed against.
* [0011 — Re-save server-corpus-open-issues.txt](0011-resave-server-open-issues.md) - no text representation in Box; the server-side ledger has never been read.

# Done

* [0014 — Version the global agent config](0014-version-the-global-agent-config.md) - DONE 2026-07-31, private repo `vvanagas/claude-config` with recovered history and a symlink.

# Decisions, no date

* [0009 — OI-02, canonical home for Vue](0009-oi02-canonical-for-vue.md) - the same obligations now live in two places; the corpus's own rule forbids it.
* [0003 — teach review Tier 2](0003-teach-review-tier-2.md) - a scheduling queue would change what kind of tool teach is; it also fixes a mechanism that is broken as designed.
* [0004 — teach review Tier 3](0004-teach-review-tier-3.md) - state root, risk routing, format contracts; verify the pedagogy citations before adopting them.
* [0013 — Two teach gaps left unfixed](0013-teach-gaps-left-unfixed.md) - design extensions, not defects; only if real use shows they bite.
