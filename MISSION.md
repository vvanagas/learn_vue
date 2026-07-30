# Mission: Ship a Vue 3 + TypeScript admin application, end-to-end

## Why

I have 20 years of Unix, Perl and regex behind me, a 5k-line Java GUI app
(long ago), and .NET CRUD services with JWT auth. The data and backend half of
a product is already within reach. What I cannot do is build the half a user
actually touches — the browser layer — and that gap is what stops me shipping
anything of my own. The goal is not to know Vue; it is to have a working
application of mine, live, that I built and can keep changing.

The application is a **CRUD admin tool with JWT auth**, on a FastAPI + Postgres
backend I write myself, running under Docker. The shape is deliberately one I
already know from .NET work: when the backend is a known quantity, every hour
of novelty lands on the browser layer, which is where the deficit is. FastAPI
and Postgres are a **secondary** goal — worth learning, never at the expense of
the primary one.

## Success looks like

- A deployed application, reachable at a URL, whose frontend I wrote.
- I can add a new screen — route, state, form, validation, API call, error and
  loading states — without copying an example.
- I can look at a page that renders wrong and fix the CSS by reasoning about
  the box model and the flex/grid algorithms, not by trial and error. This is
  the specific weakness the mission exists to close.
- The frontend consumes a JWT-authenticated API, handles token expiry and
  refresh, and never leaves a protected route readable once the token is gone.
- That API is mine: FastAPI + Postgres, issuing the tokens the frontend spends,
  brought up with a single `docker compose up` on a machine that has never seen
  it before.
- The code passes `tsc --strict` and its own test suite, written test-first.
- I can pick the work up from a phone — read a lesson, and hand a task to a
  cloud session — without needing to be at the desk.

## Constraints

- **Time:** ~4 hours per weekday for **~10 months** — on the order of 800-830
  hours. Substantial. Enough to build foundations properly rather than route
  around them, which is why HTML/CSS gets a dedicated phase before any Vue.
  The tenth month was added deliberately when the backend was adopted: the
  alternative was trimming the CSS foundations to fund a secondary goal, which
  would invert the priority this mission exists to set.
- **Starting point:** strong on backend, data, shell and text processing;
  static-typing instincts from Java and C#. Weak on HTML, CSS and the visual
  layer generally. No modern-JS-ecosystem experience.
- **Language:** TypeScript from the first line. It matches the typing instincts
  already there, and `coding-rules` ships only a TypeScript binding — so the
  house ruleset can bind to this project rather than sitting unused.
- **Rules adoption:** `coding-rules` phases in after fundamentals, not at
  lesson one. Difficulty is the enemy while acquiring knowledge and the tool
  while drilling skills; three unfamiliar systems competing at once stalls.
- **Backend stack:** FastAPI + Postgres, in Docker (natively or under WSL).
  Learning FastAPI is a real but **secondary** goal. When the two compete, the
  browser layer wins — a backend that is merely adequate still serves the
  mission, whereas an elegant backend behind a frontend I cannot build does not.
- **Everything in git, everything recoverable.** Progress, lessons and code all
  live in the GitHub repo, so a session can resume from any machine or a phone.

## Out of scope

- **Vapor Mode.** Vue 3.6 is in beta as of mid-2026 and Vapor is opt-in and
  still stabilising. Learn on stable 3.5 with the Composition API and
  `<script setup>`. Chasing a beta compiler mode teaches nothing transferable
  and shifts under you mid-course.
- **The Options API.** Legacy-facing. Read it well enough to decode old Stack
  Overflow answers; do not write it.
- **Nuxt / SSR.** A second framework stacked on the one being learned. Revisit
  only if the chosen app genuinely needs SSR or SEO.
- **Other frameworks.** No React or Svelte comparisons. They cost working
  memory and buy nothing toward shipping.
- **Design skill.** Making layouts *work* is in scope. Making them *beautiful*
  is a different mission.
- **Orchestration beyond `docker compose`.** No Kubernetes, no service mesh.
  The stack is a frontend, an API and a database; anything more is infra
  practice wearing the costume of this mission.
- **Deep FastAPI.** Background workers, async SQLAlchemy tuning, custom
  middleware. Secondary goal means secondary: enough API to feed the frontend
  honestly, no more.

---

## OWED: what does the admin tool administer?

The *shape* is settled — CRUD screens over a JWT-protected FastAPI + Postgres
API. The *subject* is not, and the subject is what decides which screens exist.
"An admin tool" cannot tell you whether you need a date picker, a file upload,
or a tree view.

This blank is left rather than guessed. It does not block Phases 1-3: the
browser layer, TypeScript and Vue core are identical whatever the rows turn out
to represent. Phase 4 is where it binds, which is roughly month 5 — so there is
time, and a subject chosen from experience will beat one chosen today.

What makes a good subject here: **data you already have or already care about**,
with enough field variety to force real forms, and a reason to open it after the
course ends.

Once named: replace this section and add a learning record capturing the choice.
