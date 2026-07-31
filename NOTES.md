# Teaching Notes

Preferences and working notes, so future sessions don't re-ask.

## Learner background (2026-07-30)

- ~20 years Unix, Perl, regex. Text processing and the shell are native ground.
- Java: one ~5k-line GUI application, long ago.
- .NET: CRUD services with JWT and auth. Comfortable with the backend shape.
- Static-typing instincts from both. Structural typing will be the surprise.
- **Weak:** HTML, CSS, the visual/GUI layer generally. Self-identified, and the
  reason Phase 1 exists.
- No modern-JS-ecosystem exposure (npm/Vite/bundlers all new).

## Budget

~4 hours per weekday, 9 months. ≈756 hours. Unusually large — the plan spends
it on foundations rather than compressing them, because the mission's stated
weakness is *below* Vue, not in it.

## Teaching preferences

- Not yet stated by the learner. Fill in as they emerge.
- Provisional, inferred from background — revise on contact with reality:
  - Analogies to Perl/Unix/.NET will land; analogies to React will not.
  - Explanations of *mechanism* ("what the browser does with this") will land
    better than explanations of *convention* ("this is how it's done"), given
    20 years of reading systems rather than following recipes.

## Environment

- Windows 11, PowerShell primary, Bun installed and preferred over npm/npx.
- Workspace is a git repository, `vvanagas/learn_vue` on GitHub. Currently
  **private**; slated to go public so Pages can serve lessons to a phone.
- Backend stack: FastAPI + Postgres under Docker (natively or via WSL).
- Connected MCP servers usable in lessons: PrimeVue, Playwright, Context7.
- `teach` skill installed at `~/.claude/skills/teach/`.
- GitHub account plan is **Free** (`gh api user --jq .plan.name`). Pages
  therefore needs a public repo; private Pages is Enterprise Cloud only.

### Phone access

Two different problems with different answers — reading lessons (GitHub Pages
over a public repo; `.nojekyll` is load-bearing) and doing the work (cloud
sessions run in an isolated VM that clones from GitHub and cannot reach local
Docker). Full detail, with sources and the one unverified claim, in
[docs/phone-access.md](./docs/phone-access.md).

### `coding-rules` loads from the personal copy, not the vendored one

Personal overrides project, so `~/.claude/skills/coding-rules/` is the copy that
is actually in force and the vendored copy in this repo is inert. Do not read
the vendored one to find out which rules apply. The precedence citation, the
silent-shadowing hazard, and the two-target update procedure are in
[docs/coding-rules-precedence.md](./docs/coding-rules-precedence.md).

## Deferred — see `pending/`

Open work lives in [pending/](./pending/), an
[OKF](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
bundle: one file per item, `type: Pending`, with `state` / `trigger` / `owner`
as producer extensions. Start at [pending/index.md](./pending/index.md).

It moved out of this file on purpose. `NOTES.md` is read at the **start of every
session**, so a 130-line backlog of mostly-dormant items was a tax paid every
time, forever. The index is a dozen lines; the detail is one click away and
enters context only when someone opens it.

Thirteen items, none of them blocking a lesson. The ones that fire soonest:
`0002` (a Tier-2 enforcement tier — build it in the Phase 2 CI thread), `0005`
and `0008` (Phase 5A), `0007` (needs real code from Phase 4).

Closing an item sets `state: done` and names the commit that closed it. Files
are never deleted — the same reason learning records are superseded rather than
removed.

## Standing decisions

- Composition API with `<script setup>` only. Options API is read-only knowledge.
- Vue 3.5 stable. Vapor Mode (3.6 beta) is explicitly out of scope.
- Pinia, not Vuex.
- `coding-rules` phases in at Phase 6, not before — now **both** bindings,
  TypeScript and Python, since FastAPI makes the latter live. The vendored
  copy carries only `binding-typescript.txt` and needs `binding-python.txt`
  added when Phase 5A starts.
- Application: a **CRUD admin tool with JWT auth**. Subject still unnamed and
  deliberately deferred to Phase 4 — see `OWED` in `MISSION.md`.
- FastAPI and Postgres are a **secondary** goal, time-boxed to ~80 h in Phase 5A.
  When the two goals compete, the browser layer wins.
- Calendar: **~10 months, ~816 h**, settled 2026-07-31. Extended rather than
  trimming Phases 4-7, so the CSS foundations stay whole.
- `history.txt` is **git-ignored** and stays local. It is a desk artifact —
  it records what ran on this PC, in this PC's paths; phones and tablets have
  no use for it, and the repo is public. Keep updating it at the desk. A cloud
  session clones from GitHub and so cannot see or append to it: phone work
  lands in git, and its ledger entry gets written on the next PC session.

---

Session handover (2026-07-31): [handover.md](./handover.md) — repo SHAs, the
traps a fresh session hits, and the findings that generalise. Read it before
re-deriving anything.

NEXT: Author lesson `0001` — Phase 1, the browser layer. Hand-written HTML and
CSS, no Vue, no build tools. Nothing is blocking it: mission, plan, resources
and the `Deferred` list above are all settled. `lessons/`, `reference/` and
`assets/` are empty, so this session also earns the workspace its shared
stylesheet (`assets/`), which is itself Phase 1 CSS practice. There is no older
material to retrieve yet — spacing starts at lesson `0002`.
