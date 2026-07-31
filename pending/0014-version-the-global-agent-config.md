---
type: Pending
title: Put the global agent config under version control
description: ~/.claude/CLAUDE.md is 13 KB of load-bearing rules with no git, no backup, and no rollback.
status: stable
state: open
trigger: Now-ish. It has no history, and it is edited by agents — including today.
owner: workstation (C:\Users\Vidma\.claude)
tags: [config, git, risk]
generated: { by: claude/opus-5, at: 2026-07-31T16:45:00Z }
verified: { by: human:vvanagas, at: 2026-07-31T16:45:00Z }
---

# Version the global agent config

## What

`C:\Users\Vidma\.claude\CLAUDE.md` is 13 KB and contains the Iron Law of TDD,
the secrets invariant, the workflow protocol, the OKF rule, and the memory
protocol. There is **no git repository at `~/.claude`**, no backup file, and
therefore no diff and no rollback.

It was edited by an agent on 2026-07-31. The rollback note in `history.txt` #20
reads "manual — the pre-edit file was 11504 bytes", because that is genuinely
all the recovery information that exists.

## Why it is sharper than it looks

The file's own **workflow protocol §1 is "Git first"**, and §6 is "verify
canonical source before migration tasks". The rules file does not follow its own
rules. That is not irony for its own sake — it is the single point where a bad
edit silently changes the behaviour of every future session on this machine,
with nothing to compare against.

## Options

- `git init` in `~/.claude`, with a `.gitignore` for the noisy parts
  (`projects/`, `todos/`, caches, `settings.local.json`, anything holding
  credentials) and commit `CLAUDE.md`, `skills/`, `keybindings.json`.
- Or a small dotfiles repo elsewhere with symlinks, if the rest of `~/.claude`
  is too noisy to live in a repo.

**Check what is in there before committing anything** — `.claude` holds session
transcripts and may hold tokens. That inspection is the first step, not the
commit.
