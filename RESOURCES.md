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

### House ruleset

- `.claude/skills/coding-rules/` — vendored from
  [vvanagas/coding-rules](https://github.com/vvanagas/coding-rules) (CC BY 4.0).
  Use for: `coding-rules-master.txt` for the obligations, `binding-typescript.txt`
  for TypeScript mechanism. Phases in from Phase 6 per the mission's constraints.

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

- **Vue + JWT auth done properly.** Token storage, refresh flows, and route
  guards attract a lot of low-quality blog content with genuine security holes
  (localStorage advice especially). Nothing is listed here until a high-trust
  source is found. Your existing .NET JWT knowledge is currently the more
  trustworthy input.
- **coding-rules has no frontend binding.** Bindings ship for TypeScript, Go,
  Python and PHP; `binding-typescript.txt` is backend-shaped (Bun + Elysia,
  Drizzle, route schemas). Nothing there covers components, reactivity or CSS.
  Its CR-13.4 exemplar slot is also unfilled. Expect to write the frontend
  interpretation yourself as the project grows — a genuine contribution back.
- **Deployment.** Deliberately unresolved until the application is named; the
  target depends on what gets built.
