---
type: Pending
title: teach review Tier 3 — state root, risk routing, format contracts, pedagogy
description: The larger or judgment-heavy half of the pre-use review, including four citations that must be verified before adoption.
status: stable
state: open
trigger: After Tier 2 settles; the pedagogy item needs its sources checked first, whenever it is taken up.
owner: vvanagas/skills (the fork)
tags: [teach, review]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
---

# teach review Tier 3

Full review: [../docs/teach-skill-review.md](../docs/teach-skill-review.md).

## What

- **`.teach/` state root plus a manifest** (§1). Directionally good; a breaking
  change for every existing workspace, so it needs a migration path and should
  probably be optional rather than the default. Note the review partly argues
  against a design the skill does not have: "one mission per workspace" already
  implies a dedicated directory.
- **High-risk domain routing** (§8) — the skill advertises yoga and fitness, and
  "delegate to a community" is not a safeguard.
- **`LESSON-FORMAT.md` / `REFERENCE-FORMAT.md`** (§12) — turn "beautiful",
  "short" and "self-contained" into checkable requirements.
- **Pedagogy revisions** (§9) — cognitive-load framing instead of the
  knowledge-vs-skill difficulty rule, worked-example fading, a corrective
  feedback ladder.

## The trap in the pedagogy item

§9 cites four papers. **Verify them before adopting them.** Adopting unverified
sources would break the exact provenance rule the review praises, inside the
skill whose Iron Rule is "ground every claim". The irony would be total and it
would be shipped.
