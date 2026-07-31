# Vue 3 + TypeScript Resources

Curated per `RESOURCES-FORMAT.md`. Every entry is annotated with when to reach
for it — a bare link is useless in three months. Community links below were
verified against the [official Vue community guide](https://vuejs.org/about/community-guide)
on 2026-07-30 rather than recalled, because community links rot fastest.

## Knowledge

### Phase 1 — the browser layer (HTML/CSS, before any Vue)

- [MDN Web Docs — Learn web development](https://developer.mozilla.org/en-US/docs/Learn)
  The reference standard, maintained by Mozilla. Use for: HTML semantics, what
  an element actually *means*, and as the lookup you return to for the rest of
  your career. Not a course — a reference to read alongside one.
- [web.dev — Learn CSS](https://web.dev/learn/css)
  Google's structured CSS course, written by browser engineers. Use for: the
  box model, the cascade, specificity, and *why* a rule applied. This is the
  course that closes the stated weakness; treat it as the spine of Phase 1.
- [web.dev — Learn HTML](https://web.dev/learn/html)
  Companion to the above. Use for: document structure, forms, and the
  accessibility semantics you get for free by picking the right element.
- [CSS-Tricks — A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
  Use for: the one-page flexbox lookup. Bookmark it; you will open it weekly.
- [CSS-Tricks — A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
  Use for: the same, for grid. Grid for page-level layout, flex for
  component-level — that split is the practical rule.
- [Flexbox Froggy](https://flexboxfroggy.com/) and [Grid Garden](https://cssgridgarden.com/)
  Use for: retrieval practice on the two layout algorithms. Games, not reading
  — exactly the tight feedback loop skills acquisition needs.
- [Josh W. Comeau — CSS articles](https://www.joshwcomeau.com/css/)
  Use for: the deep "why does this happen" explanations (stacking contexts,
  centering, margin collapse). Free articles; his paid course is optional.

### Phase 2 — TypeScript and modern JavaScript

- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
  Official. Use for: the type system proper. Skim the OO chapters — Java and C#
  already cover that ground. Read narrowing, unions, and generics closely;
  structural typing is the genuine departure from what you know.
- [MDN — JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
  Use for: closures, modules, `this`, and the event loop. These, not syntax,
  are where a Java/Perl background actually mispredicts.

### Phase 3+ — Vue and its ecosystem

- [Vue.js official documentation](https://vuejs.org/guide/introduction.html)
  The primary source for this mission. Widely held to be among the best docs in
  the industry. Set the toggles to **Composition API** and **TypeScript** on
  first visit — the docs rewrite themselves and every later snippet follows.
- [Vue.js interactive tutorial](https://vuejs.org/tutorial/)
  In-browser, no setup. Use for: the first contact with reactivity, before any
  toolchain exists to go wrong.
- [Vue Router documentation](https://router.vuejs.org/)
  Official. Use for: routes, nested routes, and navigation guards — the guards
  are where JWT route protection lives.
- [Pinia documentation](https://pinia.vuejs.org/)
  Official, and the recommended store since Vuex was retired. Use for: shared
  state across screens. Ignore Vuex material entirely; it is the older answer.
- [Vite documentation](https://vite.dev/)
  Use for: the build tool underneath every modern Vue project. Read the config
  and env-var pages; skip the plugin-authoring material.
- [Vitest](https://vitest.dev/) and [Vue Test Utils](https://test-utils.vuejs.org/)
  Use for: the test layer that makes the Iron Law of TDD executable on
  components. Needed from Phase 6 onward.
- [Playwright](https://playwright.dev/)
  Use for: end-to-end tests over a real browser. A Playwright MCP server is
  already connected in this workspace's Claude Code session.
- [Vue.js official blog](https://blog.vuejs.org/) and
  [vuejs/core releases](https://github.com/vuejs/core/releases)
  Use for: checking what actually shipped, rather than trusting a model or a
  blog post. Relevant during this course because 3.6 and Vapor Mode are moving.

### The CI thread — GitHub Actions (Phases 2-7)

- [GitHub Actions documentation](https://docs.github.com/en/actions)
  Official and the only source that stays current with the runner images and
  the YAML schema. Use for: workflow syntax, contexts and expressions, caching,
  service containers, environments. Blog posts about Actions rot fast because
  the platform moves; check here before trusting one.
- [Secure use reference](https://docs.github.com/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions)
  Read this **before** writing a workflow that reacts to pull requests, not
  after. Use for: script injection through `${{ }}` with untrusted context and
  the intermediate-`env:` mitigation, `pull_request_target` hazards, and
  `GITHUB_TOKEN` permission scoping. Verified 2026-07-31; note the page is
  titled "Secure use reference" rather than the older hardening-guide name.
- [Workflow syntax reference](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax-for-github-actions)
  Use for: the lookup you keep open while writing YAML — `on:`, `jobs:`,
  `needs:`, `if:`, `permissions:`, `services:`.
- This repository's own Actions tab
  Use for: the first lesson. `pages build and deployment` has been running
  since Pages was enabled and nobody wrote it — reading a real run beats
  reading a tutorial's imaginary one.

### Operational practice (Phases 5A-7)

- [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) (MIT)
  A catalog of agent skills; useful here as domain reference rather than as
  skills to install. Verified: 2026-07-31.
  - `skills/deprecation-and-migration/` — **expand/contract schema migrations**.
    Use for: Phase 5A. The framing to keep is that the data is the one thing a
    deploy rollback cannot undo, so a column is never changed in place. Contains
    a worked five-step column rename, batched backfill, and
    `CREATE INDEX CONCURRENTLY`.
  - `references/accessibility-checklist.md` — criteria and tools for Phase 7.
    Names the ground; it does not verify a package for you.
  - `references/definition-of-done.md` — the acceptance-criteria vs
    definition-of-done split, adopted into [LEARNING-PLAN.md](./LEARNING-PLAN.md).
  - `references/performance-checklist.md` and `skills/performance-optimization/`
    — **unread as of 2026-07-31**, deferred to Phase 7. Note it is anchored on
    Core Web Vitals, which is Google's ranking-signal framing and not
    automatically the right metric set for an internal admin tool.

### Accessibility tooling (Phases 6-7)

- [eslint-plugin-vuejs-accessibility](https://github.com/vue-a11y/eslint-plugin-vuejs-accessibility)
  2.5.0, MIT, published 2026-02-13. Verified against the npm registry
  2026-07-31. Use for: the **static** half of `binding-vue`'s V-4 — alt text,
  accessible names, ARIA validity, real interactive elements.
- [@axe-core/playwright](https://github.com/dequelabs/axe-core-npm)
  4.12.1, MPL-2.0, published 2026-06-23. Verified 2026-07-31. A dev dependency,
  so its file-level copyleft does not reach application code. Use for: the
  **behavioural** half of V-4, which no linter can see — focus movement, focus
  restoration, live-region announcement. Pair it with explicit focus assertions;
  axe alone does not check that focus went somewhere sensible.

### House ruleset

- `.claude/skills/coding-rules/` — vendored from
  [vvanagas/coding-rules](https://github.com/vvanagas/coding-rules) (CC BY 4.0).
  Use for: `coding-rules-master.txt` for the obligations, `binding-typescript.txt`
  for TypeScript mechanism. Phases in from Phase 6 per the mission's constraints.

### Archetype / control corpus — private, Box `shared/golden/`

Own work, not a published source. A rule system, not prose: each **control**
is a trigger-bound obligation with a `floor` (when it is overkill), a `ceiling`
(when to reach for a real system instead), `required`, `forbidden`, and named
`proof` tests. Each **archetype** carries default / conditional / forbidden
control sets. Read the catalog for the obligation and the map for the
attachment — the corpus is strict that each relation has exactly one home.

Highest-trust material available for Phases 4-6, because it was written against
recurrence in real systems (a control earns inclusion at "seen more than twice,
not merely conceivable") and it records its own rejections and gaps.

**Client side — Phases 3-4:**

- `client-controls.txt` (CL01-CL18)
  Use for: the obligations of a Vue slice. CL03 derive-don't-synchronize,
  CL04 typed-async-state, CL05 latest-wins cancellation, CL13 route-as-state.
  Its governing inversion is the thing to internalise first: the client runs on
  hardware the adversary controls, so every client check is UX, never
  enforcement (CL11).
- `client-archetype-control-map.txt`
  Use for: classifying a feature. The unit is the **data-flow slice**, not the
  component — "components are pipeline stages". Seven archetypes:
  `server_state_mirror`, `form_commander`, `derived_view`, `route_state`,
  `realtime_subscriber`, `ui_local`, `client_long_task`.
- `client-web-archetype-fusions.txt`
  Use for: the three seams where slices meet — `optimistic_mutation`,
  `live_overlay`, `url_driven_data`. That last one is "the majority of real
  pages" and is exactly Phase 4's list-and-detail work.

**Server side — Phases 5A/5B:**

- `server-controls.txt` (C01-C58) and `server-archetype-control-map.txt`
  Use for: the FastAPI half. Your app is `http_crud` + `http_command` +
  `auth_token`, and the map hands you each card's default set outright. C15
  ownership-authz-on-fresh-state is the one to read twice.
- `server-web-archetype-fusions.txt` (Part C) and
  `server-async-archetype-fusions.txt` (Part D)
  Use for: endpoints that fuse two archetypes. Four web seams (time, trust,
  read_write, fan_out) and two async (correlation, compensation). The **trust**
  seam is Phase 5B's spine.

- `client-corpus-open-issues.txt` — **written 2026-07-31**, the client-side
  ledger the corpus lacked. OI-01 (now **APPLIED**) recorded that the corpus's
  "reactivity loss via destructuring" predates Vue 3.5 and would forbid correct
  code if copied into a binding verbatim; OI-02 (open) records that
  `binding-vue.txt` now restates several CL cards in CR grammar, so those
  obligations have a second home and the corpus's own one-relation-one-home rule
  needs a deliberate call.

**Version note:** `client-controls.txt` is at **v0.2** as of 2026-07-31 — the
Vue clause is corrected and now names the version it was written against. The
rest of the corpus still carries undated version-dependent claims, so treat any
framework-specific statement in it as needing re-verification before it becomes
a rule.

**Unread, and possibly load-bearing:** `archetype-stage-dissection.txt` (the
12-stage pipeline the whole corpus is expressed against), `Web-archetype-master.txt`,
`design_pipeline.txt`. `server-corpus-open-issues.txt` has no text
representation in Box and could not be read at all — re-save it there if its
contents matter.

## Wisdom (Communities)

- [Vue Land — official Discord](https://discord.com/invite/vue)
  The Vue team's real-time chat. Use for: getting unstuck in minutes on a
  concrete error, and for reading how experienced people phrase problems.
- [forum.vuejs.org](https://forum.vuejs.org/)
  Official forum, still active as of July 2026. Use for: longer questions that
  deserve a considered answer and a durable URL.
- [r/vuejs](https://www.reddit.com/r/vuejs/)
  Use for: ecosystem opinions, library comparisons, and knowing what people
  actually use in production.
- [GitHub Discussions — vuejs/core](https://github.com/vuejs/core/discussions)
  Use for: questions about Vue's own behaviour, near the people who wrote it.

No community preference has been recorded yet. If you would rather not join
any, say so and this section gets an opt-out note instead of new suggestions.

## Gaps

Areas this mission needs where no vetted resource is recorded yet. This list
drives the next search — it is not decoration.

- ~~**Vue + JWT auth done properly.**~~ **CLOSED 2026-07-31** by the archetype
  corpus above, which answers the exact questions the gap named:
  - *Token storage* — CL12 `no-secret-in-client` forbids
    `token_in_localStorage_without_recorded_justification`. localStorage is
    rejected by default; httpOnly cookie or in-memory, and the choice is a
    recorded decision. Its ceiling is a BFF holding tokens server-side so the
    token never reaches the browser at all.
  - *Expiry and refresh* — CL16 `stale-session-reauth`, whose forbidden list
    names the failures directly: `reauth_losing_unsaved_user_input`,
    `background_refetch_loop_hammering_with_dead_token`.
  - *Route guards* — CL11 `client-authz-is-ux` forbids
    `hiding_the_button_as_enforcement` and
    `privileged_route_guard_without_server_side_check`. The guard is rendering,
    never protection.
  - *Server side* — the `auth_token` card, whose
    `refresh_token_rotation_or_reuse_detection` trigger attaches C09+C10+C20
    because two concurrent refreshes with one token is both the canonical race
    and an attack signal. Plus C15 for authorization on fresh state.

  Existing .NET JWT knowledge stays the sanity check, but it is no longer the
  *only* trustworthy input.
- ~~**coding-rules has no frontend binding.**~~ **CLOSED 2026-07-31** —
  `binding-vue.txt` v0.1 written, and **merged upstream** into
  [vvanagas/coding-rules](https://github.com/vvanagas/coding-rules) as PR #1
  (`af609fe`). It is no longer a local addition: it ships with the ruleset for
  everyone, and the local copies are byte-identical to upstream. Passes the
  master's projection check (101 CR tokens, empty diff). Splits from
  `binding-typescript.txt` by *runtime* rather than language: browser-side Vue
  loads it, server-side TypeScript keeps the original, a change touching both
  loads both.

  Two residuals remain, tracked in the binding's own `Floor deviations` block
  rather than here: its **CR-13.4 exemplar slot is OWED** (no codebase yet to
  point at), and **V-4 reads `[review]` where part should be `[auto]`** because
  no accessibility linter is named — the package identity was not verified at
  authoring time and citing it wrongly would be worse than recording the gap.
  Both are Phase 6 work; see [LEARNING-PLAN.md](./LEARNING-PLAN.md).

  A correction it embeds, worth knowing before you read older advice: the
  corpus's *"reactivity loss via destructuring"* predates Vue 3.5. Destructuring
  `defineProps()` **is** reactive in 3.5+ — the compiler rewrites the access.
  The loss now happens when a destructured prop is passed *into* a function
  (`watch(foo, …)` needs `watch(() => foo, …)`), when a `reactive()` object is
  destructured, or when `.value` is read into a local. V-2 states it in 3.5
  terms and carries a version note to revisit on a major bump.
- **Python binding not vendored.** `binding-python.txt` exists in the personal
  `coding-rules` install but not in this repo's vendored copy. Needed at Phase
  5A; see `NOTES.md`.
- **Deployment.** Deliberately unresolved until the application is named; the
  target depends on what gets built.
