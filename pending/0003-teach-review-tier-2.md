---
type: Pending
title: teach review Tier 2 — real scheduling state, provenance IDs, split SKILL.md
description: The structural half of the pre-use review; the scheduling queue changes what kind of tool teach is.
status: stable
state: open
trigger: After a few real lessons exist — the queue's shape will be better specified by use than by design.
owner: vvanagas/skills (the fork)
tags: [teach, review, decision]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
verified: { by: human:vvanagas, at: 2026-07-31T13:30:00Z }
---

# teach review Tier 2

Full review: [../docs/teach-skill-review.md](../docs/teach-skill-review.md).
Section numbers below point into it.

## What

- **Real scheduling state** (§3, §6) — `last_attempt`, `last_outcome`,
  `next_due` per concept, replacing "read learning records oldest-first".
- **Claim-level provenance** (§7) — resource IDs plus locators.
- **Split `SKILL.md` into `references/`** (§15).

## Why

The scheduling item **fixes a mechanism added on 2026-07-31 that is broken as
designed**. Dated learning records were necessary and are not sufficient: a
creation date is not review state, so oldest-first will keep resurfacing
old-but-stable concepts while missing a recently failed one whose record is
newer, and it requires reading an unbounded number of files.

Provenance: "traces to an entry in `RESOURCES.md`" establishes bibliography
membership, not claim support. A resource can be topical and not support the
specific claim.

`SKILL.md` went 9.6 KB -> 23.3 KB across this session's edits, mostly rationale
that is read once and paid for every turn thereafter.

## The decision inside this item

A scheduling queue is where `teach` **stops being a lightweight skill and
becomes a spaced-repetition system with a schema**. That may well be correct. It
should be chosen deliberately rather than drifted into.
