---
type: Pending
title: Read the performance pack, against a real symptom
description: Unread by choice; anchored on Core Web Vitals, which is Google's ranking framing and not this app's problem.
status: stable
state: open
trigger: When a real performance symptom appears — probably the first list screen with a few thousand rows, Phase 4. Failing that, Phase 7.
owner: learn_vue
tags: [performance, phase-7, reading]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
---

# Read the performance pack

## What is unread

From `addyosmani/agent-skills` (MIT): `skills/performance-optimization/`,
`references/performance-checklist.md` (7.4 KB),
`skills/browser-testing-with-devtools/`.

Skipped deliberately on 2026-07-31 — the reading budget went to items with
near-term consequences. Recorded as unread in `RESOURCES.md` rather than
summarized from a directory listing.

## The caveat that decides how to read it

The pack is anchored on **Core Web Vitals** — LCP, INP, CLS. That is Google's
*ranking-signal* framing, designed for public pages competing in search. This
app is an internal CRUD admin tool behind JWT auth. Nobody is ranking it.

Some of it still transfers: INP is a decent proxy for "does this feel
responsive" regardless of who is measuring. But the metrics likely to bite here
are different — time-to-interactive on a dense data table, bundle size over a
slow connection, and API latency, which is a backend problem wearing a frontend
symptom (the corpus's `fan_out` seam has more to say about it than any CWV
checklist).

## Why the trigger is a symptom, not a phase

Reading a performance checklist in the abstract produces a list of things to
worry about. Reading it against a page that is actually slow produces a fix.
