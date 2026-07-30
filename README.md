# learn_vue

A stateful teaching workspace for learning Vue 3 + TypeScript over 9 months,
driven by the [`teach`](https://github.com/mattpocock/skills/tree/main/skills/productivity/teach)
skill from [mattpocock/skills](https://github.com/mattpocock/skills).

This repository is not a Vue project. It is the *course* — the mission, the
plan, the vetted sources, the lessons, and the record of what was actually
learned. The application itself gets built inside it from Phase 4 onward.

## Start here

| File | What it is |
|------|------------|
| [MISSION.md](./MISSION.md) | Why this is being learned. Everything derives from it. |
| [LEARNING-PLAN.md](./LEARNING-PLAN.md) | The 7 phases, hour budgets, and exit criteria. |
| [RESOURCES.md](./RESOURCES.md) | Vetted sources. Lessons cite these, never model memory. |
| [NOTES.md](./NOTES.md) | Background, environment, standing decisions. |

## Directories

- `lessons/` — numbered self-contained HTML lessons, the primary unit of teaching.
- `reference/` — compressed cheat sheets, the documents actually revisited.
- `learning-records/` — ADR-style records of what was learned and what changed.
- `assets/` — shared stylesheet and reusable components across lessons.
- `.claude/skills/coding-rules/` — vendored house ruleset (CC BY 4.0), phases in at Phase 6.

## Running a session

The `teach` skill must be installed at `~/.claude/skills/teach/`, then:

```bash
cd C:\darbas4\learn_vue
```

Open Claude Code in that directory and run `/teach`. The skill treats the
current directory as the workspace, so launching from anywhere else scatters
lessons into the wrong tree.

## Open item

The application to be built is **not yet named** — see the OWED section at the
bottom of [MISSION.md](./MISSION.md). The plan holds without it through Phase 3;
Phase 4 cannot start until it is chosen.

## Attribution

- `teach` skill — [mattpocock/skills](https://github.com/mattpocock/skills), MIT.
- `coding-rules` — [vvanagas/coding-rules](https://github.com/vvanagas/coding-rules), CC BY 4.0.
