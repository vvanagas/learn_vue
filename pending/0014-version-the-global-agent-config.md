---
type: Pending
title: Put the global agent config under version control
description: ~/.claude/CLAUDE.md is 13 KB of load-bearing rules with no git, no backup, and no rollback.
status: stable
state: done
trigger: Closed 2026-07-31 by 78abd9a in vvanagas/claude-config (private).
owner: workstation (C:\Users\Vidma\.claude)
tags: [config, git, risk]
generated: { by: claude/opus-5, at: 2026-07-31T16:45:00Z }
verified: { by: human:vvanagas, at: 2026-07-31T16:45:00Z }
---

# Version the global agent config

> **DONE 2026-07-31.** Private repo `vvanagas/claude-config`, three commits:
> `fcadd0d` (2026-02-19), `8590e2a` (2026-03-12), `78abd9a` (today) — the first
> two recovered from the stray `CLAUDE - Copy` files and committed at their
> original mtimes, so the log shows when the rules actually changed. Separate
> repo rather than `git init` in `~/.claude`, because that directory holds
> `.credentials.json` and in-place tracking is a denylist that must stay correct
> forever; a separate repo is an allowlist. `~/.claude/CLAUDE.md` is now a
> **symlink** into the repo — verified bidirectional, so drift is impossible
> rather than discouraged. `skills/` deliberately excluded: already downstream
> of two upstream repos, so a third copy would be drift, not backup.

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
