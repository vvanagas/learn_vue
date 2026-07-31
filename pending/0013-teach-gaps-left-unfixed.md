---
type: Pending
title: Two teach gaps left unfixed on purpose
description: Retention outcomes over time, and a home for the learner's own code; both change the teaching model rather than repair it.
status: stable
state: open
trigger: Only if real use shows they bite. Neither is a defect; both are design extensions.
owner: vvanagas/skills (the fork)
tags: [teach, design]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
verified: { by: human:vvanagas, at: 2026-07-31T13:30:00Z }
---

# Two teach gaps left unfixed on purpose

## 1. No record of retention outcomes over time

Lessons run quizzes with a feedback loop, but nothing persists whether an answer
was right *later*. Learning records are written on evidence of understanding,
with `Evidence` optional. Overlaps with the Tier-2 scheduling queue
([0003](0003-teach-review-tier-2.md)) and may be absorbed by it.

## 2. No home for the learner's own work

The workspace has `lessons/`, `reference/`, `learning-records/` and `assets/`,
and nowhere for the artifact being built. Fine for yoga; awkward for a
programming mission where the app is the point.

## Why they were not fixed

Both change the skill's **teaching model** rather than repairing an
inconsistency in it. Every other change made to the fork corrected something
that was internally contradictory, unexecutable, or unsafe. These two would be
redesigning someone else's skill on a hunch — and doing that unasked, before a
single lesson has run, is the imagination-derived-rule failure again.
