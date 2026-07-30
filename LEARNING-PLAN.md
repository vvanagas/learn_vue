# Learning Plan — Vue 3 + TypeScript, 9 months

Derived from [MISSION.md](./MISSION.md). If the mission changes, this changes.

**Budget:** ~4 h/weekday × ~21 weekdays/month × 9 months ≈ **756 hours**.

The ordering is not arbitrary. Vue renders to the DOM and styles it with CSS;
a learner weak on that layer who starts at Vue cannot tell a Vue problem from a
CSS problem, and every layout bug becomes unattributable magic. The foundations
phase exists to make later bugs *diagnosable*. With 756 hours available, this is
affordable — it would not be on a 100-hour budget.

Each phase has an **exit criterion**: something demonstrable, not "felt ready".
A phase is not finished until its criterion is met; slipping a phase is normal
and expected, and is better than carrying a gap forward.

---

## Phase 1 — The browser layer · Weeks 1-6 · ~120 h

No Vue. No build tools. No framework. Hand-written HTML and CSS in a text
editor, opened in a browser.

- HTML semantics: what each element *means*, not just what it renders as.
- The box model, the cascade, specificity, inheritance.
- Flexbox in depth, then Grid in depth. Flex for components, Grid for pages.
- Positioning, stacking contexts, overflow.
- The DOM as an object graph — familiar territory dressed unfamiliarly, given
  a Java GUI background: nodes, a tree, an event model.
- Browser devtools as a first-class instrument, especially the element
  inspector and computed-styles pane.

**Exit criterion:** given a screenshot of a moderately complex layout, rebuild
it in static HTML/CSS without a framework, and explain aloud why each element
sits where it does. Fix a deliberately broken layout by reading computed styles
rather than by guessing.

**Watch for:** this is the phase most likely to feel like a detour from "learn
Vue". It is the phase the mission is actually about.

---

## Phase 2 — TypeScript and the JavaScript that surprises you · Weeks 7-10 · ~80 h

- TypeScript's type system: narrowing, unions, generics, utility types.
  **Structural** typing — the real departure from Java/C# nominal typing.
- `strict` mode from the first file. Never loosen it to make an error go away.
- JavaScript's genuinely different parts: closures, modules, `this`, the event
  loop, promises and `async`/`await`.
- The toolchain: Bun, `package.json`, Vite, ES modules.

**Skip:** classes, inheritance, interfaces-as-contracts. Java and C# already
taught these; re-teaching them wastes hours the CSS phase could use.

**Exit criterion:** write a small typed data-processing tool — a natural fit
for the existing regex and text-processing strength — that compiles clean under
`tsc --strict` with no `any` and no non-null assertions.

---

## Phase 3 — Vue core · Weeks 11-17 · ~140 h

Composition API with `<script setup>` throughout. Options API is read-only.

- Reactivity: `ref`, `reactive`, `computed`, `watch` — and *why* reactivity
  needs proxies, which the Java GUI listener experience makes easy to motivate.
- Components: props, emits, `v-model`, slots, provide/inject.
- Template syntax, directives, conditional and list rendering, keys.
- Lifecycle, and composables as the unit of reuse.
- Typing all of the above — `defineProps<T>()`, typed emits, generic components.

**Exit criterion:** build a multi-component interactive page from scratch,
fully typed, with no store and no router, and explain when a value should be
`ref` versus `computed` versus plain.

---

## Phase 4 — The shape of an application · Weeks 18-23 · ~120 h

The chosen application starts here and grows through Phase 7. Every subsequent
lesson lands in it.

- Vue Router: routes, nested routes, params, lazy loading, navigation guards.
- Pinia: stores, when state belongs in a store versus a component.
- Forms and validation — traditionally the hardest part of any real frontend.
- Loading, empty, and error states as first-class design concerns, not
  afterthoughts.
- Component library decision point: PrimeVue (its MCP server is already
  connected) versus hand-rolled. Make it deliberately, after Phase 1 means you
  *can* hand-roll — so the choice is convenience, not avoidance.

**Exit criterion:** the application has three or more real screens, navigable,
with shared state and at least one non-trivial validated form.

---

## Phase 5 — Backend integration and auth · Weeks 24-28 · ~100 h

The phase where existing strength pays off — the backend half is already known.

- HTTP from the browser: `fetch`, interceptors, error handling, CORS (expect
  to lose an afternoon to CORS; everyone does).
- Consuming the JWT-authenticated API. Login, token storage, refresh on expiry,
  logout, and route guards that actually protect.
- **Security caution:** this topic attracts poor blog content with real holes.
  `RESOURCES.md` records it as an open gap deliberately. Existing .NET JWT
  knowledge is the more trustworthy input here than anything a model recalls.
- Typed API clients — sharing types across the wire.

**Exit criterion:** log in against a real backend, hold a session across
reloads, get transparently refreshed on expiry, and be correctly bounced from a
protected route once the token is truly gone.

---

## Phase 6 — Testing, and `coding-rules` phases in · Weeks 29-33 · ~100 h

Rules arrive here by design, per the mission's constraints: difficulty is the
enemy while acquiring knowledge and the tool while drilling skills. By now
components are writable without conscious effort, so rigor has capacity to land.

- Vitest and Vue Test Utils. What is worth testing in a component, and what is
  just asserting that the framework works.
- Playwright for end-to-end flows.
- Then `coding-rules`, read properly: `coding-rules-master.txt` plus
  `binding-typescript.txt`.
  - The **Iron Law** (CR-3.1-3.4): no production code without a captured
    failing test first.
  - **Proof lines**: the captured failing run and passing run, not the claim.
  - **§13 generation density**: the anti-slop rules — no single-implementation
    interfaces, no one-caller helpers, no guards against type-proven
    impossibilities.
  - Fill the **CR-13.4 exemplar slot** with a real file from this codebase.
- Retrofit the existing application toward the rules; do not rewrite it wholesale.

**Exit criterion:** one new feature built entirely test-first, with the failing
and passing runs captured in a learning record. Lint and typecheck green.

---

## Phase 7 — Ship it · Weeks 34-39 · ~96 h

- Production builds, environment config, bundle size.
- Deployment to a real URL with a real domain.
- Accessibility: keyboard navigation, focus management, screen-reader basics.
  Phase 1's semantic HTML makes most of this nearly free — which is the point.
- Performance: what actually matters, measured rather than assumed.
- Then use the thing, find what is wrong, and fix it.

**Exit criterion:** the mission's first success line is true — a deployed
application, at a URL, whose frontend you wrote.

---

## How sessions run

Per `~/.claude/skills/teach/SKILL.md`, invoked as `/teach` from this directory:

- Lessons land in `lessons/` as numbered self-contained HTML, one tightly
  scoped idea each, short enough to fit in working memory.
- Compressed knowledge lands in `reference/` — the cheat sheets you return to.
  Lessons are rarely revisited; references are.
- `learning-records/` captures what was learned and what changed, and is what
  decides the next lesson's difficulty.
- `assets/` holds the shared stylesheet and reusable components, so the course
  looks like one course. Building it is itself Phase 1 CSS practice.
- Every claim in a lesson carries a citation to `RESOURCES.md`. Nothing is
  taught from model memory.

## Review points

Re-read `MISSION.md` at the end of each phase. Missions move as competence
grows — that is normal. When it moves, update the file and write a learning
record; a stale mission silently steers every session that follows.
