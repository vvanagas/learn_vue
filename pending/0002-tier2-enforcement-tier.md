---
type: Pending
title: A Tier-2 enforcement tier for coding-rules
description: Deterministic checks that are not linters, sitting between [auto] and [review].
status: stable
state: open
trigger: When the Phase 2 CI thread starts — build it in learn_vue first, not in coding-rules.
owner: learn_vue (proposal); coding-rules only once it has earned it
tags: [coding-rules, enforcement, ci, decision]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
verified: { by: human:vvanagas, at: 2026-07-31T13:30:00Z }
---

# A Tier-2 enforcement tier for coding-rules

## What

`coding-rules` has `[auto]` (a linter's red output *is* the violation) and
`[review]` (human judgment) and **nothing between**. Add a third tier:
deterministic, free, and honestly labelled a *proxy* — the shape
`addyosmani/agent-skills` runs in CI (stemmed TF-IDF over skill descriptions,
erroring at >=75% pairwise similarity, warning at >=50%, plus a rank-1 floor
that ratchets and "never lower it to make a regression pass").

Four candidate checks, roughly ten lines each:

1. Every `[auto:` names a mechanism. The master already declares a bare
   `[auto]` invalid; nothing enforces it.
2. Every named lint rule exists in the installed plugin's rule list.
3. Every `verified:` date is within N months, and no `stale_after` has passed.
4. The projection check, which already exists, moves under this umbrella as
   Tier 1.

## Why

Two Tier-2-shaped defects were hit in a single day, and neither existing tier
catches either:

- `binding-vue` shipped `[auto]` on CR-5.4 naming no mechanism. Caught only
  because a grep happened to run.
- `binding-vue` shipped an `[auto]` naming an a11y package nobody had verified
  existed. Caught only because it was checked against npm by hand.

## Why this is a decision, not a task

`coding-rules` is currently **pure text**: no `scripts/`, no `package.json`, no
CI, zero dependencies. That is a property — it vendors into any project by
copying five files. Adding executable checks gives the repo a runtime, and the
master's `## Enforcement model` section changes, which is a version bump
touching all five bindings.

**Recommendation:** build the checks inside `learn_vue`'s CI thread at Phase 2,
where Actions is being learned anyway and the checks have something real to run
against. Upstream them only if they prove themselves over a few months. That
inverts the failure this project keeps hitting — it earns its place before it is
written into a ruleset.
