---
type: Pending
title: Reconcile CR-7.5 forward-only with the tested-down-path rule
description: A genuine ambiguity in a shared ruleset, not a typo; it belongs upstream as an issue once settled.
status: stable
state: open
trigger: When the first real migration gets written, Phase 5A.
owner: coding-rules (as an upstream issue, once the resolution is known)
tags: [coding-rules, phase-5a, migrations]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
verified: { by: human:vvanagas, at: 2026-07-31T13:30:00Z }
---

# Reconcile CR-7.5 with the tested-down-path rule

## The tension

CR-7.5 states: "Connection pool size is explicit; pool exhaustion returns a
typed error. **Migrations are forward-only and do not break existing APIs.**"

The expand/contract source states: "**Every migration has a tested down path.** A
migration you can't reverse is a deploy you can't roll back. Write and run the
`down` before merging."

## Why it is not semantics

Both are defensible and they target different environments:

- **Forward-only** is a *production* discipline. You never run a `down` against
  live data, because a down migration that drops a column destroys rows a
  rollback cannot restore. You fix forward with a new migration.
- **A tested `down`** is a *development* discipline. Writing and running the
  reverse in CI proves the migration is understood and that the change is
  genuinely additive. It is a test, not a runbook.

## Proposed resolution, deliberately unwritten

Forward-only in production; expand/contract is the mechanism that makes
forward-only survivable, because if every change is additive you never *need* a
down; a `down` is required in dev/CI as evidence of reversibility, never as a
production procedure.

## Why it stays unwritten for now

Writing a rule about migrations before having written a migration is exactly the
imagination-derived rule problem that `binding-vue` already demonstrates. Settle
it against a real migration.

## Ownership

The ambiguity is in the shared ruleset — anyone vendoring `coding-rules` hits
the same question — so the resolution belongs upstream as an issue, not as a
private note here.
