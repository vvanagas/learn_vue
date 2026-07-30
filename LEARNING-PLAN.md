# Learning Plan — Vue 3 + TypeScript, 9 months

Derived from [MISSION.md](./MISSION.md). If the mission changes, this changes.

**Budget:** ~4 h/weekday × ~21 weekdays/month × **10 months** ≈ **816 hours**.

**The backend was not free, and the tenth month is how it was paid for.** The
mission originally assumed an existing JWT API to consume. Writing it — FastAPI,
Postgres, Docker, token issuance — costs roughly 60 h the original 756 did not
contain. The alternative was trimming Phases 4-7, which would have squeezed
Phase 7 (deploy, accessibility, performance) to around 70 h. Extending won:
foundations stay whole, and shipping keeps its hours.

| Phase | Hours | Weeks |
|---|---|---|
| 1 — The browser layer | 120 | 1-6 |
| 2 — TypeScript | 80 | 7-10 |
| 3 — Vue core | 140 | 11-17 |
| 4 — Shape of an application | 120 | 18-23 |
| 5A — The backend I own | 80 | 24-27 |
| 5B — Wiring the two halves | 80 | 28-30 |
| 6 — Testing + `coding-rules` | 100 | 31-35 |
| 7 — Ship it | 96 | 36-42 |
| **Total** | **816** | **~42 weeks** |

Slipping a phase is still normal. The table is a budget, not a schedule.

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
- **The unit of design is the data-flow slice, not the component.** From the
  client archetype map (`RESOURCES.md`): components are *pipeline stages*; what
  you classify is a feature's state-ownership shape — who owns this data, where
  it lives, what may mutate it. Introduced here rather than at Phase 4 because
  it contradicts how component-framework tutorials frame the problem, and the
  component-first habit is expensive to unlearn once drilled.
- CL03 `derive-don't-synchronize` alongside `computed`: if a value is computable
  from existing state, it is derived, never copied. Its forbidden list —
  `effect_or_watcher_synchronizing_two_state_containers`, `storing_a_derived_value`
  — names the single most common Vue mistake, and naming it while `watch` is
  first being learned is cheaper than correcting it in Phase 4.

**Exit criterion:** build a multi-component interactive page from scratch,
fully typed, with no store and no router; explain when a value should be `ref`
versus `computed` versus plain; and name which slice archetype each part of the
page belongs to.

---

## Phase 4 — The shape of an application · Weeks 18-23 · ~120 h

The application — a **CRUD admin tool with JWT auth** — starts here and grows
through Phase 7. Every subsequent lesson lands in it. Its *subject* (what the
rows represent) is still open; see the `OWED` section of [MISSION.md](./MISSION.md).
It binds here and not before, which is the point of leaving it open: five months
of building will name it better than today can.

Until it is named, screens are built against a stand-in entity with deliberately
varied fields — text, date, enum, foreign key, optional — because that variety is
what forces real form work regardless of subject.

- Vue Router: routes, nested routes, params, lazy loading, navigation guards.
- Pinia: stores, when state belongs in a store versus a component.
- Forms and validation — traditionally the hardest part of any real frontend.
- Loading, empty, and error states as first-class design concerns, not
  afterthoughts. CL04 makes this mechanical: model async status as a
  discriminated union, and require that *every* variant renders — no infinite
  spinner, no error swallowed to console.
- Component library decision point: PrimeVue (its MCP server is already
  connected) versus hand-rolled. Make it deliberately, after Phase 1 means you
  *can* hand-roll — so the choice is convenience, not avoidance.

**The corpus supplies this phase's vocabulary** (`RESOURCES.md`). Each screen
gets classified before it gets built:

- The seven client slice archetypes — `server_state_mirror`, `form_commander`,
  `derived_view`, `route_state`, `realtime_subscriber`, `ui_local`,
  `client_long_task`. `ui_local` exists to give the floor a name: its forbidden
  list *is* its content, and the recurring failure is promotion — ephemeral
  state hoisted into a global store.
- **`url_driven_data` is this phase's seam.** The client fusion doc calls it
  "the majority of real pages": route params select which server data renders.
  Every bug in it is a second owner of one fact — a component-local copy of the
  params, or a cache key built from stale props. Learn it as the default shape
  of a list-and-detail screen, not as an advanced topic.
- `form_commander` forbids CL05 by default: latest-wins is a *read* policy, and
  applying it to submits is lost writes. That distinction is worth a lesson.

**Exit criterion:** the application has three or more real screens, navigable,
with shared state and at least one non-trivial validated form — and each screen
can be named as a slice archetype, with any seam between two slices identified.

---

## Phase 5A — The backend I own · Weeks 24-27 · ~80 h

The secondary goal, taken deliberately and time-boxed. This is a *translation*
exercise, not a from-zero one: the CRUD-plus-JWT shape is already known from
.NET, so what is genuinely new is Python's idiom, FastAPI's dependency
injection, and Postgres — not the architecture.

- FastAPI: path operations, Pydantic models as the request/response contract,
  dependency injection, automatic OpenAPI.
- Postgres: schema, migrations, indexes. SQL is not new; the ORM layer is.
- Docker Compose: API + database + volumes, brought up with one command on a
  machine that has never seen the project.
- Issuing JWTs: hashing, signing, expiry, refresh. **The API side of the auth
  contract**, so Phase 5B integrates against something whose internals are known.
- Python typing and `coding-rules`' `binding-python.txt` read for orientation,
  not yet enforced — rules still phase in at Phase 6.

**The corpus gives this phase its control sets outright** (`RESOURCES.md`). The
app is three server archetypes — `http_crud` (store/retrieve, no invariants),
`http_command` (mutation with invariants), `auth_token` (issue the credential).
Pull each card's default set from the map rather than inventing one. Two that
earn early attention:

- **C15 `ownership-authz-on-fresh-state`** — load the resource, then authorize
  against the loaded state, inside the transaction if a mutation follows. Its
  forbidden list is a FastAPI trap list: `route_model_binding_for_command_authz`
  and `final_ownership_check_in_pre_handler` are exactly what dependency
  injection makes elegant to write and wrong to rely on.
- **`auth_token`'s `refresh_token_rotation_or_reuse_detection` trigger** —
  attaches C09 + C10 + C20, because two concurrent refreshes with one token is
  simultaneously the canonical race and an attack signal.

**Time-box this.** Every hour past ~80 is an hour stolen from the primary goal.
An adequate backend serves the mission; an elegant one behind a frontend that
cannot be built does not.

**Exit criterion:** `docker compose up` on a clean machine yields a running API
with a browsable OpenAPI page, a migrated database, and a login endpoint that
returns a token you can decode and see expire.

---

## Phase 5B — Wiring the two halves · Weeks 28-30 · ~80 h

- HTTP from the browser: `fetch`, interceptors, error handling, CORS (expect
  to lose an afternoon to CORS; everyone does — and now you own both sides of
  it, which makes it diagnosable rather than mystifying).
- Spending the JWT: login, token storage, refresh on expiry, logout, and route
  guards that actually protect.
- **Security:** this topic attracts poor blog content with real holes. The gap
  `RESOURCES.md` used to record here is now **closed** by the corpus, which
  answers it in the same vocabulary the gap was written in — CL12 rejects
  localStorage by default and names the BFF ceiling; CL16 covers mid-session
  expiry without losing unsaved input; CL11 makes a route guard *rendering*,
  never protection, so every privileged action still needs its server check.
  This whole phase is the corpus's **trust seam** — verify-then-act — whose
  translation line is the one to memorise: authentication is not authorization.
- Typed API clients — and the genuine prize of owning both ends: generating
  TypeScript types from FastAPI's OpenAPI schema, so the wire contract is
  checked by the compiler instead of by hope.

**Exit criterion:** log in against your own backend, hold a session across
reloads, get transparently refreshed on expiry, and be correctly bounced from a
protected route once the token is truly gone — with the frontend's types
generated from the backend's schema rather than hand-written.

---

## Phase 6 — Testing, and `coding-rules` phases in · Weeks 31-35 · ~100 h

Rules arrive here by design, per the mission's constraints: difficulty is the
enemy while acquiring knowledge and the tool while drilling skills. By now
components are writable without conscious effort, so rigor has capacity to land.

- Vitest and Vue Test Utils. What is worth testing in a component, and what is
  just asserting that the framework works.
- Playwright for end-to-end flows.
- Then `coding-rules`, read properly: `coding-rules-master.txt` plus
  `binding-typescript.txt` — and `binding-python.txt`, which the FastAPI half
  now makes live. Both bindings, one master.
  - The **Iron Law** (CR-3.1-3.4): no production code without a captured
    failing test first.
  - **Proof lines**: the captured failing run and passing run, not the claim.
  - **§13 generation density**: the anti-slop rules — no single-implementation
    interfaces, no one-caller helpers, no guards against type-proven
    impossibilities.
  - Fill the **CR-13.4 exemplar slot** with a real file from this codebase.
- Retrofit the existing application toward the rules; do not rewrite it wholesale.
- **Write `binding-vue.txt`** — a defined work item, not an aspiration. The
  client catalog is framework-neutral *by design* and states that Vue-specific
  forbidden lists belong in `coding-rules` per stack, naming the two it expects:
  reactivity loss via destructuring, and gratuitous deep watchers. By this phase
  you will have hit both. This is the contribution back that `RESOURCES.md`
  flagged, now with a specification.
- **The control cards hand you test names.** Each carries `proof.tests` — C15's
  are `forbidden_actor_rejected` and `ownership_changed_before_write_rejected`;
  CL10's include `retry_does_not_double_apply`. Test-first is easier when the
  test list was written before the code, by someone who had seen the failure.

**Exit criterion:** one new feature built entirely test-first, with the failing
and passing runs captured in a learning record. Lint and typecheck green.

---

## Phase 7 — Ship it · Weeks 36-42 · ~96 h

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

## Working from a phone

Two different problems, often confused:

**Reading lessons.** Lessons are `.html`; github.com renders HTML as source, not
as a page. The chosen answer is **GitHub Pages over a public `learn_vue`** —
which works on the Free plan and needs the repo's visibility flipped. Until that
happens, lessons are desk-only. Alternatives, if public turns out to be
unwelcome: a Tailscale-reachable static server on the WSL/Docker box, or a
separate public repo mirroring `lessons/` and `assets/`.

**Doing the work.** Claude Code cloud sessions run on Anthropic-managed
infrastructure, persist across devices, and are steerable from the phone app —
`claude --cloud` starts one, `claude --teleport` pulls it back to the terminal.
Two limits shape what that is good for:

- Each session is an isolated VM that clones from **GitHub, not your machine**.
  Push before handing off, or the cloud session works from stale code.
- It cannot reach your local Docker or Postgres. Phone work means code, tests
  and commits — not driving the running stack. Once the app is deployed
  (Phase 7), the *running* app is reachable from the phone by ordinary means.
- Cloud sessions are a research preview for Pro, Max and Team plans. **Verify
  the account plan before this becomes load-bearing.**

The practical consequence for the plan: phases 1-3 are almost entirely
phone-compatible, because HTML, CSS, TypeScript and Vue components need no
running database. From Phase 5A on, the stack matters and the desk matters.

## Review points

Re-read `MISSION.md` at the end of each phase. Missions move as competence
grows — that is normal. When it moves, update the file and write a learning
record; a stale mission silently steers every session that follows.
