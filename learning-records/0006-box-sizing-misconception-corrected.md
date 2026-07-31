# The declared `width` is the content box — a half-model corrected

`2026-07-31`

Status: active — concept **not closed**. See *Evidence*.

Probed before authoring lesson `0001` with `width:300px; padding:20px;
border:2px`. Answer: **304px** — border added on both sides, padding not. So the
learner already held a *layered* model of the box and did not treat `width` as
the on-screen size; the layer boundary was simply in the wrong place. The real
misconception was specific and worth naming: **border is outside the declared
width but padding is inside it.** Under the default `box-sizing: content-box`
both are outside.

## Evidence

- Probe (pre-lesson, cold): 304px. Wrong by exactly the padding.
- Transfer question immediately post-lesson: two 500px columns with 16px padding
  and 1px border in a 1000px container — answered *"by padding and border don't
  fit"*. Correct mechanism, unprompted, on a case not shown in the lesson. The
  68px was not produced and was not asked for.

**This is fluency, not storage, and the record says so deliberately.** The
transfer answer came minutes after reading the lesson, which is the one case the
format's own table rules out as evidence. The concept stays open and gets
re-tested cold at the top of lesson `0002`. If it comes back then, promote it to
Demonstrated in a new record; if it does not, this record was the floor and it
was not there.

## Implications

- **A first attempt at a transfer question was malformed and is my error, not a
  retrieval failure.** It used `width: 50%`, which requires knowing what a
  percentage resolves against — never taught. The learner declined to guess,
  correctly. Re-asked in absolute pixels, it transferred first try. *Check a
  transfer question for untaught variables before reading its result as
  evidence:* a badly formed question produces a real-looking negative.
- Percentage resolution against the containing block is now a **named gap**,
  surfaced by that bad question. It is the natural companion to the box model
  and belongs early in Phase 1.
- The layered-model instinct was already there before teaching. Expect the same
  elsewhere in CSS: the gap is likely to be *which* layer a property acts on,
  rather than the existence of layers. Probe boundaries, do not re-teach
  foundations.
- The devtools Computed-pane box diagram was introduced as the instrument for
  reading this rather than computing it. Untested — no evidence the learner has
  opened it. Do not assume it in a later lesson.
