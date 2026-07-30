# Mission: Ship a Vue 3 + TypeScript application end-to-end

## Why

I have 20 years of Unix, Perl and regex behind me, a 5k-line Java GUI app
(long ago), and .NET CRUD services with JWT auth. The data and backend half of
a product is already within reach. What I cannot do is build the half a user
actually touches — the browser layer — and that gap is what stops me shipping
anything of my own. The goal is not to know Vue; it is to have a working
application of mine, live, that I built and can keep changing.

## Success looks like

- A deployed application, reachable at a URL, whose frontend I wrote.
- I can add a new screen — route, state, form, validation, API call, error and
  loading states — without copying an example.
- I can look at a page that renders wrong and fix the CSS by reasoning about
  the box model and the flex/grid algorithms, not by trial and error. This is
  the specific weakness the mission exists to close.
- The frontend consumes a JWT-authenticated API, handles token expiry and
  refresh, and never leaves a protected route readable once the token is gone.
- The code passes `tsc --strict` and its own test suite, written test-first.

## Constraints

- **Time:** ~4 hours per weekday for 9 months — on the order of 700-780 hours.
  Substantial. Enough to build foundations properly rather than route around
  them, which is why HTML/CSS gets a dedicated phase before any Vue.
- **Starting point:** strong on backend, data, shell and text processing;
  static-typing instincts from Java and C#. Weak on HTML, CSS and the visual
  layer generally. No modern-JS-ecosystem experience.
- **Language:** TypeScript from the first line. It matches the typing instincts
  already there, and `coding-rules` ships only a TypeScript binding — so the
  house ruleset can bind to this project rather than sitting unused.
- **Rules adoption:** `coding-rules` phases in after fundamentals, not at
  lesson one. Difficulty is the enemy while acquiring knowledge and the tool
  while drilling skills; three unfamiliar systems competing at once stalls.

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

---

## OWED: the application must be named

`## Why` above is concrete about the *reason* and still abstract about the
*thing*. Per `MISSION-FORMAT.md`, "ship my own app" is the same shape of
vagueness as "get fitter" — it cannot decide what to teach next, because every
Vue feature looks equally relevant when no real screen demands it.

This blank is left rather than guessed. Candidates that fit the existing
background, so the backend stays a known quantity and each hour lands on the
browser layer:

1. **Log / text-analysis dashboard** — load or tail a file, apply regex rules,
   render matches, filter and chart. Plays directly to 20 years of Perl and
   regex; the novel part is entirely visual.
2. **CRUD + JWT admin tool over a .NET backend** — the shape already known from
   work, rebuilt with a real frontend. Lowest backend risk, highest transfer to
   the day job.
3. **Self-hosted ops dashboard** — services, disk, certs, systemd units on
   machines already administered. Real daily-use software with a real user.

Once named: replace this section, update the title, and add a learning record
capturing the choice.
