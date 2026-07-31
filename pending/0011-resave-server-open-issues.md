---
type: Pending
title: Re-save server-corpus-open-issues.txt in Box so it becomes readable
description: The file has no text representation and cannot be read through the Box connector.
status: stable
state: open
trigger: Whenever its contents matter — it is the server-side ledger and has never been read.
owner: Box shared/golden
tags: [corpus, box, tooling]
generated: { by: claude/opus-5, at: 2026-07-31T13:30:00Z }
---

# Re-save server-corpus-open-issues.txt

## What

`get_file_content` on file id `2321105658174` returns "Markdown or text
representation is not available for this file", twice, and this Box connector
has no AI-extraction fallback. The file is 18 KB and was last modified
2026-07-05.

## Why it matters

It is the **server-side** open-issues ledger — the counterpart to the client one
created on 2026-07-31. The archetype map cites it (`see
server-corpus-open-issues.txt OI-01`), so there are known outstanding findings
in it that have never been read.

## Fix

Open and re-save it in Box, which normally triggers representation generation.
Then read it and fold anything live into this backlog.
