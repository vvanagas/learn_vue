---
type: Pending
title: Verify the Claude plan supports cloud sessions
description: Cloud sessions are a research preview for Pro, Max and Team; the account plan has never been checked.
status: stable
state: open
trigger: Before phone hand-off becomes load-bearing — realistically Phase 5A, when the desk starts to matter.
owner: learn_vue
tags: [tooling, phone, unverified]
stale_after: 2026-12-31
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
verified: { by: human:vvanagas, at: 2026-07-31T13:30:00Z }
---

# Verify the Claude plan supports cloud sessions

## What

Per the docs, Claude Code on the web is "in research preview for Pro, Max, and
Team users, and for Enterprise users with premium seats". The GitHub account is
on the **Free** plan; the **Claude** plan was never checked.

## Why

`LEARNING-PLAN.md`'s "Working from a phone" section assumes cloud sessions are
available. If they are not, the phone story reduces to reading lessons over
GitHub Pages, which still works — but the plan currently promises more.

## Note

`stale_after` is set because "research preview" is a moving target: the
availability tiers may change independently of anything in this project.
