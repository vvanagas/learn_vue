---
type: Reference
title: Phone access — two separate problems
description: Reading lessons and doing the work are different problems with different answers; conflating them is why the phone story looked simpler than it is.
status: stable
tags: [phone, github-pages, cloud-sessions]
generated: { by: claude/opus-5, at: 2026-07-31T13:00:00Z }
verified:
  - { by: claude/opus-5, at: 2026-07-31T13:00:00Z }
  - { by: human:vvanagas, at: 2026-07-31T13:00:00Z }
stale_after: 2026-12-31
---

# Phone access — two separate problems

## 1. Reading lessons

Lessons are `.html`, and github.com renders HTML as **source**, not as a page.
"It's in the repo" therefore does not produce readable lessons on a phone.

The chosen route is **GitHub Pages over a public repo** — live at
<https://vvanagas.github.io/learn_vue/>. The account is on the **Free** plan and
private Pages requires Enterprise Cloud, which is why the repository is public.

`.nojekyll` is load-bearing rather than incidental: Pages runs Jekyll by default,
Jekyll parses `{{ }}` as Liquid, and every Vue lesson will contain Vue mustaches.
Without it the build eats them. Disabling Jekyll also means Markdown stops
rendering at the site root, which is why `index.html` exists instead of relying
on `README.md`.

Fallbacks if public ever becomes unwelcome: a Tailscale-reachable static server
on the Docker box, or a separate public repo mirroring only `lessons/` and
`assets/`.

## 2. Doing the work

Claude Code cloud sessions — `claude --cloud` to start one, steer from the phone
app, `claude --teleport` to pull it back to the terminal.

Per [the docs](https://code.claude.com/docs/en/claude-code-on-the-web), three
constraints shape what this is good for:

- **Each session is an isolated, Anthropic-managed VM** that clones from
  **GitHub, not this machine**. Push before handing off, or the cloud session
  works from stale code.
- **It cannot reach local Docker or Postgres**, and network egress is limited by
  default. Phone work means code, tests and commits — not driving the running
  stack.
- **It is a research preview for Pro, Max and Team plans.** The Claude plan on
  this account has **never been checked** — see
  [pending/0006](../pending/0006-verify-claude-plan.md). This is the one claim in
  this document that is unverified, and it is the one the rest depends on.

## The practical consequence

Phases 1-3 are almost entirely phone-compatible, because HTML, CSS, TypeScript
and Vue components need no running database. From Phase 5A onward the stack
matters and so does the desk.

`stale_after` is set to 2026-12-31 because "research preview" is a moving
target: availability tiers can change independently of anything in this project.
