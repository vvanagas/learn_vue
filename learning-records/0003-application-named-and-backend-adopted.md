# Application named: CRUD admin tool, on a backend the learner writes

The OWED item from [[0002-mission-established]] is half-closed. The application
is a **CRUD admin tool with JWT auth** — deliberately the shape already known
from .NET work, so that novelty concentrates in the browser layer where the
deficit actually is. What it administers is still unnamed, and is now the
narrower OWED in [[MISSION.md]].

Alongside it, the learner adopted a backend stack that the mission had not
previously assumed: **FastAPI + Postgres under Docker**, with learning FastAPI
named explicitly as a *secondary* goal. Everything — progress, lessons, code —
lives in GitHub so sessions can resume from any machine or a phone.

**Evidence:** chosen from a four-option menu after the constraints were laid out,
against a recommendation for a different option (a log/text-analysis dashboard).
The learner overrode it in favour of lower backend risk and higher transfer to
the day job — a reasoned trade, not a default.

**Implications:**

1. **Phase 5 splits in two.** It previously assumed an existing JWT API to
   consume. Now 5A builds the API and 5B wires the halves. This costs ~60-80 h
   the 756-hour budget never contained; the calendar decision (extend to ~10
   months versus trim Phases 4-7) is deliberately left open in
   [[LEARNING-PLAN.md]] because it is a mission-level change.
2. **Owning both ends unlocks a real prize.** TypeScript types generated from
   FastAPI's OpenAPI schema means the wire contract is compiler-checked. That
   was not available when the backend was someone else's.
3. **`binding-python.txt` becomes live.** It was dead weight in the personal
   `coding-rules` install an hour before this decision, and absent from the
   vendored copy entirely. Phase 6 now reads both bindings.
4. **The subject deferral is a feature, not a gap.** Phases 1-3 are identical
   whatever the rows represent, so five months of building will name the subject
   better than today can. Phase 4 builds against a stand-in entity with varied
   field types, because field variety — not subject — is what forces real forms.
5. **Phone access is two problems, not one.** Reading lessons needs Pages over a
   public repo; doing work needs cloud sessions, which run in an isolated VM that
   cannot see local Docker. Phases 1-3 are phone-friendly precisely because they
   need no running stack; from 5A on, the desk matters.

Cross-links: [[MISSION.md]], [[LEARNING-PLAN.md]], [[0001-prior-knowledge-and-the-real-gap]]
