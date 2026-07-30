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
- Workspace is a git repository intended for `learn_vue` on GitHub (private).
- Connected MCP servers usable in lessons: PrimeVue, Playwright, Context7.
- `teach` skill installed at `~/.claude/skills/teach/`.

### `coding-rules` exists in two places — personal shadows vendored

| Copy | Path | Role |
|---|---|---|
| Personal | `~/.claude/skills/coding-rules/` | **The one that loads.** Global CLAUDE.md mandates the skill for every project, so it must live here. Carries `binding-{typescript,go,php,python}.txt`. |
| Vendored | `.claude/skills/coding-rules/` | Portability only — travels with the repo on clone or handoff, and carries the CC BY 4.0 attribution vendoring requires. TypeScript binding only. Inert on this machine. |

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
  Copy-Item "$src\coding-rules-master.txt", "$src\binding-typescript.txt" $dst -Force
}
```

Verify agreement afterwards; expect output only for the three extra bindings the
personal copy carries:

```powershell
diff -rq C:\Users\Vidma\.claude\skills\coding-rules C:\darbas4\learn_vue\.claude\skills\coding-rules
```

Upstream clones at `C:\darbas4\{coding-rules,mattpocock-skills}` are read-only
source, referenced by nothing. `mattpocock-skills` is disposable — one
`git clone --depth 1` restores it. Keep the `coding-rules` clone; it is the
update path above.

## Standing decisions

- Composition API with `<script setup>` only. Options API is read-only knowledge.
- Vue 3.5 stable. Vapor Mode (3.6 beta) is explicitly out of scope.
- Pinia, not Vuex.
- `coding-rules` phases in at Phase 6, not before.
