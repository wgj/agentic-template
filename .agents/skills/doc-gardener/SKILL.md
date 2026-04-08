---
name: doc-gardener
description: Maintain repository legibility by updating stale indexes, cross-links, placeholders, and source-of-truth docs. Use when a repository already has docs, but they have drifted and become harder for fresh-context agents to trust.
---

# Doc Gardener

Use this skill to keep an existing repository knowledge base healthy.

The goal is not a broad documentation rewrite. The goal is to leave the repository easier for the next fresh-context agent to navigate and trust.

## Workflow

1. Find stale indexes, missing links, orphaned docs, and placeholders that no longer reflect reality.
2. Repair routing from `AGENTS.md`, `README.md`, and the nearest relevant indexes.
3. Update indexes when docs are added, removed, or renamed.
4. Promote repeated chat-only explanations into durable repository docs when they will help future agents.
5. Make unresolved gaps explicit instead of leaving silent drift.

## What To Produce

Aim to leave behind some combination of:

- repaired indexes and cross-links
- updated entrypoint docs
- placeholder files that now say something truthful and useful
- concise notes about remaining gaps

## Rules

- Prefer small, high-signal doc fixes over broad rewrites.
- Keep the repository easier to scan after each pass.
- Do not add policy that the repository cannot actually support.
- If a placeholder cannot be filled yet, explain what is still missing.
