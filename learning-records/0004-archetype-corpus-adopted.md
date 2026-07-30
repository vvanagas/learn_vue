# The archetype/control corpus is adopted as the Phase 4-6 knowledge source

The learner has an existing private corpus (Box `shared/golden/`) that is a
rule system for structuring server and client code: **controls** (trigger-bound
obligations with floor, ceiling, required, forbidden, and named proof tests)
attached to **archetypes** (deployment shapes on the server, data-flow slices on
the client) via a map, with **fusion seams** covering the cases where two
archetypes meet. Seven files read this session; it is now in [[RESOURCES.md]].

**Evidence of standing:** this is not aspirational documentation. It enforces
its own constitution — one relation, one home ("if this doc and the map
disagree, the map wins and this doc has a bug"), inclusion bars that are
actually applied (`http_passthrough` demoted to a note, `cli_wrapper` and
`cli_status_checker` merged, all EIP archetypes rejected as "dataflow roles,
not deployment shapes", C45 rejected as deployment topology), and recorded
`catalog_gap` entries that are explicitly *not* promoted to controls until they
recur.

**Implications:**

1. **The JWT gap in `RESOURCES.md` is closed**, and closed precisely. CL12
   rejects localStorage by default; CL16 covers mid-session expiry; CL11 makes
   route guards rendering rather than enforcement; the server `auth_token` card
   covers refresh-token rotation as both a race and an attack signal. The gap
   had specifically named localStorage advice as the low-quality-content trap.
2. **The frontend-binding gap narrows into a work item.** The client catalog is
   deliberately framework-neutral and states that Vue-specific forbidden lists
   belong in `coding-rules` per stack — naming reactivity-loss-via-destructuring
   and gratuitous-deep-watchers as the expected content. Writing
   `binding-vue.txt` is now specified work, not an open question.
3. **The corpus supplies Phase 4's vocabulary in advance.** The client map's
   unit of classification is the *data-flow slice*, not the component —
   "components are pipeline stages". That reframing is worth teaching early, in
   Phase 3, because it contradicts how component-framework tutorials present the
   problem and is hard to unlearn later.
4. **`url_driven_data` is the Phase 4 seam.** The client fusion doc calls it
   "the majority of real pages", and its failure mode is always a second owner
   of one fact — a local copy of URL params, or a cache key built from stale
   props. That is a CL03 violation wearing routing clothes.
5. **Do not teach from the corpus as if it were finished.** It carries open
   issues of its own, one file could not be read at all, and three more remain
   unread. Cite what was read; do not extrapolate the rest.

Cross-links: [[RESOURCES.md]], [[LEARNING-PLAN.md]], [[0003-application-named-and-backend-adopted]]
