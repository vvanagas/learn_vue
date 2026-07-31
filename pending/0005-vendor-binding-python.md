---
type: Pending
title: Vendor binding-python.txt into the project copy
description: The Python binding exists in the personal coding-rules install but not in the repo's vendored copy.
status: stable
state: open
trigger: When Phase 5A starts and FastAPI code gets written.
owner: learn_vue
tags: [coding-rules, phase-5a]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
evidence: { class: OBSERVED, at: 2026-07-31, basis: "both coding-rules copies listed; the vendored one is missing binding-python" }
---

# Vendor binding-python.txt

## What

`~/.claude/skills/coding-rules/` carries `binding-{typescript,vue,go,php,python}`.
The vendored copy at `.claude/skills/coding-rules/` carries only
`binding-{typescript,vue}`.

## Why it matters then and not now

Personal overrides project, so the personal copy is what loads and Python rules
would apply anyway. The vendored copy exists for **portability** — it is what
travels on clone or handoff. A Python-writing project whose vendored ruleset has
no Python binding hands the next reader an incomplete ruleset.

## How

Copy from the upstream clone per the two-target procedure in `NOTES.md`, then
re-run the projection check against the vendored master.
