---
type: Pending
title: teach review Tier 2 — real scheduling state, provenance IDs, split SKILL.md
description: The structural half of the pre-use review; the scheduling queue changes what kind of tool teach is.
status: stable
state: open
trigger: FIRED 2026-07-31 on lesson one — see "Observed". Ordering is demonstrably wrong; the remaining decision is how much machinery to answer it with.
owner: vvanagas/skills (the fork)
tags: [teach, review, decision]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
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

## Observed 2026-07-31 — the predicted failure, on lesson one

The trigger above expected "a few real lessons". One was enough.

`learning-records/0006` is the **newest** record and the **only open** concept
in the workspace: the box-model transfer answer was correct but arrived minutes
after reading, so it is fluency rather than storage and needs a cold re-test.
Oldest-first sorts it **last**, behind `0001`-`0005` — five settled decision
records (prior knowledge, mission, stack, corpus, CI) that carry nothing to
retrieve and will resurface every session forever.

So the review's charge is no longer an argument, it is an observation: **a
creation date is not review state.** The one record that needs attention is the
one the current ordering reaches last, and the records it reaches first are
permanently inert. The `NEXT:` line in `NOTES.md` is currently carrying the
scheduling decision by hand, in prose — which works at one open concept and is
exactly the thing that does not scale.

Note what this does *not* settle: it is evidence the ordering is wrong, not
evidence the answer is a full queue with a schema. A cheaper fix may exist —
e.g. a `status:`/`next_due:` line in the records that already exist, sorted on
read, with no new state root. Weigh that before adopting §3 wholesale.
