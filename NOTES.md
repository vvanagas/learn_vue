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
- `coding-rules` vendored to `.claude/skills/coding-rules/`.
- Connected MCP servers usable in lessons: PrimeVue, Playwright, Context7.
- `teach` skill installed at `~/.claude/skills/teach/`.

## Standing decisions

- Composition API with `<script setup>` only. Options API is read-only knowledge.
- Vue 3.5 stable. Vapor Mode (3.6 beta) is explicitly out of scope.
- Pinia, not Vuex.
- `coding-rules` phases in at Phase 6, not before.
