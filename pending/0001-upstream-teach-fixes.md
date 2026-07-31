---
type: Pending
title: Upstream the teach skill fixes
description: Split the fork's four commits into a small defect PR and an issue for the design opinions.
status: stable
state: open
trigger: If upstream mattpocock/skills changes the teach skill — or never; this is optional.
owner: vvanagas/skills (the fork)
tags: [teach, upstream, fork]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
evidence: { class: OBSERVED, at: 2026-07-31, basis: "fork SHAs, upstream main and the teach-path log all re-checked via gh on 2026-07-31" }
---

# Upstream the teach skill fixes

## What

The fork `vvanagas/skills`, branch `teach-workspace-fixes`, is four commits
ahead of upstream: `151bd80`, `8546e22`, `5d53a2e`, `87b0669` (skill v1.3).

Do **not** offer it as one PR. Split it:

- **A small PR — the objective defects.** The glossary was specified in three
  disagreeing places and `GLOSSARY-FORMAT.md` was linked from nowhere while the
  other three format files were linked. Dates on learning records (the skill
  mandates spacing and shipped no way to execute it). The turn-boundary rule
  (a genuine hole). The sources-are-data rule (a safety boundary for a skill
  that fetches from the open web by design). All verifiable in minutes.
- **An issue — the design opinions.** Iron Rules, the resolution taxonomy, the
  scope boundary, `PLAN.md`, the grill-me/reconcile/shape-me ports. A
  maintainer's "no" here is legitimate; he may have kept it lightweight
  deliberately.

## Why

Bundled, a reviewer who wants the bug fix but not the taxonomy has to reject
everything. Split, the bug fix is an easy yes and the rest becomes a
conversation.

## When it fires

Checked 2026-07-31: upstream main is still `2ab9580` and the teach skill has not
changed since 2026-07-13. So the cost of leaving this alone is currently zero.
It only becomes work if upstream ships a teach change and the branch needs a
rebase.

**Correction, 2026-07-31 (second check).** This item previously said upstream had
**no license**. That was wrong — it came from a malformed `jq` query that
reported `license=none` for several repos. `mattpocock/skills` is **MIT**
(`gh api repos/mattpocock/skills --jq .license`). The fork and a PR back were
never in question; MIT also permits redistribution and modification, so the
vendored-copy and derivative-work options that the ToS-only reading ruled out
are in fact open. Do not re-derive the restriction from the old sentence.

Re-verified the same day: upstream `main` is still `2ab9580` (2026-07-28) and
the last commit touching `skills/productivity/teach` is `697d4ce`,
2026-07-13 — the Codex `agents/openai.yaml` metadata pass. So the trigger has
**not** fired. Check whether upstream wants that file kept in sync before
opening anything.
