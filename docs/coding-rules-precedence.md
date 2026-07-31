---
type: Reference
title: coding-rules exists in two places — personal shadows vendored
description: Which copy of the ruleset actually loads, why the other is inert, and the two-target update procedure that keeps them from disagreeing silently.
status: stable
tags: [coding-rules, skills, precedence, drift]
generated: { by: claude/opus-5, at: 2026-07-31T13:00:00Z }
verified:
  - { by: claude/opus-5, at: 2026-07-31T13:00:00Z }
  - { by: human:vvanagas, at: 2026-07-31T13:00:00Z }
stale_after: 2027-01-31
---

# coding-rules exists in two places

| Copy | Path | Role |
|---|---|---|
| Personal | `~/.claude/skills/coding-rules/` | **The one that loads.** The global `CLAUDE.md` mandates the skill for every project, so it must live here. Carries `binding-{typescript,vue,go,php,python}.txt`. |
| Vendored | `.claude/skills/coding-rules/` | Portability only — it travels with the repo on clone or handoff and carries the CC BY 4.0 attribution vendoring requires. Carries `binding-{typescript,vue}.txt`. **Inert on this machine.** |

## Precedence

Per [the skills docs](https://code.claude.com/docs/en/skills): *"When skills
share the same name across levels, enterprise overrides personal, and personal
overrides project."*

Personal wins — so inside this workspace the vendored copy **never loads**. Do
not read it to find out which rules are in force; read
`~/.claude/skills/coding-rules/`.

This was verified against the documentation and the filesystem, not assumed. The
first reading of it was backwards, and the correction is the reason this document
exists.

## The hazard: shadowing is silent

Nothing errors when the two copies disagree. A stale vendored copy leaves the
repository advertising rules that are not the ones being enforced — and the
error surface is zero, so it can persist indefinitely.

## Any upstream update copies to BOTH targets

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

Verify afterwards. The copies should differ only by the three bindings the
personal copy carries:

```powershell
diff -rq C:\Users\Vidma\.claude\skills\coding-rules C:\darbas4\learn_vue\.claude\skills\coding-rules
```

Re-run the master's own projection check after any binding edit — mechanical, and
it catches a stale binding immediately:

```bash
cd .claude/skills/coding-rules
grep -oE 'CR-[0-9]+\.[0-9]+' coding-rules-master.txt | sort -u > /tmp/m
grep -oE 'CR-[0-9]+\.[0-9]+' binding-vue.txt          | sort -u > /tmp/b
diff /tmp/m /tmp/b   # must be empty; 101 tokens as of master v0.4
```

## No local delta remains

`binding-vue.txt`, its `SKILL.md` router entry, and the V-4 a11y split were all
upstreamed and merged (`vvanagas/coding-rules` PR #1 `af609fe`, PR #2 `aea1df6`),
so both local copies are byte-identical to upstream and a re-copy is safe.

That was deliberate. The alternative was a permanent local divergence that every
future pull would silently clobber. **If a local-only rule is ever needed again,
upstream it instead — a fork of one file is a drift generator.**

## Upstream clones

`C:\darbas4\{coding-rules,mattpocock-skills}` are read-only source, referenced by
nothing. `mattpocock-skills` is disposable — one `git clone --depth 1` restores
it. Keep the `coding-rules` clone; it is the update path above.
