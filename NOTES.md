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

### Phone access — two separate problems

**Reading lessons:** lessons are HTML, and github.com shows HTML as source.
GitHub Pages over a public repo is the chosen route. Fallbacks if public becomes
unwelcome: Tailscale to a static server on the Docker box, or a public
mirror repo holding only `lessons/` and `assets/`.

**Doing the work:** Claude Code cloud sessions (`claude --cloud`, steer from the
phone app, `claude --teleport` to pull back to the terminal). Per
[the docs](https://code.claude.com/docs/en/claude-code-on-the-web): each session
is an isolated Anthropic-managed VM that clones from **GitHub, not this
machine** — so push before handing off. It cannot reach local Docker or
Postgres, and egress is limited by default. It is a research preview for **Pro,
Max and Team**; the Claude plan has not been checked and this is unverified.

### `coding-rules` exists in two places — personal shadows vendored

| Copy | Path | Role |
|---|---|---|
| Personal | `~/.claude/skills/coding-rules/` | **The one that loads.** Global CLAUDE.md mandates the skill for every project, so it must live here. Carries `binding-{typescript,vue,go,php,python}.txt`. |
| Vendored | `.claude/skills/coding-rules/` | Portability only — travels with the repo on clone or handoff, and carries the CC BY 4.0 attribution vendoring requires. Carries `binding-{typescript,vue}.txt`. Inert on this machine. |

Precedence, per [the skills docs](https://code.claude.com/docs/en/skills): "enterprise
overrides personal, and personal overrides project." Personal wins — so inside
this workspace the vendored copy never loads. Do not read it to find out which
rules are in force; read `~/.claude/skills/coding-rules/`.

This shadowing is silent. Nothing errors when the two disagree, so a stale
vendored copy would leave the repo advertising rules that are not the ones being
enforced. **Any upstream update copies to both targets:**

```powershell
git -C C:\darbas4\coding-rules pull
$src = 'C:\darbas4\coding-rules'
foreach ($dst in 'C:\Users\Vidma\.claude\skills\coding-rules',
                 'C:\darbas4\learn_vue\.claude\skills\coding-rules') {
  Copy-Item "$src\skills\claude-code\SKILL.md" "$dst\SKILL.md" -Force
  Copy-Item "$src\coding-rules-master.txt", "$src\binding-typescript.txt",
            "$src\binding-vue.txt" $dst -Force
}
```

**No local delta remains.** `binding-vue.txt` and its `SKILL.md` router entry
were upstreamed and merged (`vvanagas/coding-rules` PR #1, commit `af609fe`,
2026-07-31), so both local copies are now byte-identical to upstream and a
re-copy is safe. This was deliberate: the alternative was maintaining a
permanent local divergence that every future pull would silently clobber. If a
local-only rule is ever needed again, upstream it instead — a fork of one file
is a drift generator.

Verify agreement afterwards. Both copies should now be identical except for the
three bindings only the personal copy carries:

```powershell
diff -rq C:\Users\Vidma\.claude\skills\coding-rules C:\darbas4\learn_vue\.claude\skills\coding-rules
```

Also re-run the master's own projection check after any binding edit — it is
mechanical and catches a stale binding immediately:

```bash
cd .claude/skills/coding-rules
grep -oE 'CR-[0-9]+\.[0-9]+' coding-rules-master.txt | sort -u > /tmp/m
grep -oE 'CR-[0-9]+\.[0-9]+' binding-vue.txt          | sort -u > /tmp/b
diff /tmp/m /tmp/b   # must be empty; 101 tokens as of master v0.4
```

Upstream clones at `C:\darbas4\{coding-rules,mattpocock-skills}` are read-only
source, referenced by nothing. `mattpocock-skills` is disposable — one
`git clone --depth 1` restores it. Keep the `coding-rules` clone; it is the
update path above.

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

NEXT: Author lesson `0001` — Phase 1, the browser layer. Hand-written HTML and
CSS, no Vue, no build tools. Nothing is blocking it: mission, plan, resources
and the `Deferred` list above are all settled. `lessons/`, `reference/` and
`assets/` are empty, so this session also earns the workspace its shared
stylesheet (`assets/`), which is itself Phase 1 CSS practice. There is no older
material to retrieve yet — spacing starts at lesson `0002`.
