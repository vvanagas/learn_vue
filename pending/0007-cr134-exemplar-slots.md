---
type: Pending
title: Fill the CR-13.4 exemplar slots
description: Both bindings record an OWED exemplar; they need a real file from a codebase that does not exist yet.
status: stable
state: open
trigger: Phase 4 produces the candidate; Phase 6 promotes it.
owner: learn_vue
tags: [coding-rules, phase-6, owed]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
evidence: { class: OBSERVED, at: 2026-07-31, basis: "both bindings read; each carries a literal EXEMPLAR SLOT - OWED" }
---

# Fill the CR-13.4 exemplar slots

## What

`binding-vue.txt` and `binding-typescript.txt` both carry `EXEMPLAR SLOT — OWED`.

## This is not a defect in the ruleset

CR-13.4 says "name at least one file from **YOUR** codebase". The slot is
designed to be filled per adopter — upstream cannot name a file in this repo. An
empty slot correctly recorded as OWED is the rule working as intended.

## What fills it

For `binding-vue`: a component-plus-composable **pair** from Phase 4 — typed
props in type form, exactly one CR-2.13 async union, a real injected port, no
wrapper ceremony. A pair rather than a single file because on the client side
the density failure is usually the *split*: a component and composable that
should have been one, or a store that should have been neither.

For the server side, the realistic filler is `binding-python`'s slot rather than
`binding-typescript`'s, since Phase 5A writes Python.

## Why it cannot be shortcut

The point is anchoring density judgment on real code in real context. Writing a
synthetic exemplar to close the OWED would be precisely the ceremony that §13
exists to prevent.
