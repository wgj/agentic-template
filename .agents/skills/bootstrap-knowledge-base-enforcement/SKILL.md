---
name: bootstrap-knowledge-base-enforcement
description: Bootstrap repository knowledge-base enforcement. Use when the user wants Codex to make source-of-truth docs, indexes, generated reference artifacts, and repository entrypoints more discoverable, cross-linked, and mechanically maintained.
---

# Bootstrap Knowledge-Base Enforcement

Use this skill to install the "repository knowledge as the system of record" pattern into a repository that has partial docs but weak discoverability or maintenance.

The goal is to make the repository's durable knowledge usable by future agents without relying on chat history or tribal memory.

## Workflow

1. Inspect the repository's current entrypoints, source-of-truth docs, indexes, and generated artifacts.
2. Identify which files should orient a fresh-context agent first.
3. Update or add indexes so important docs are discoverable from those entrypoints.
4. Clarify what belongs in durable repository docs versus chat-only context.
5. Add or scaffold lightweight checks for stale indexes, missing links, missing source-of-truth files, or empty placeholders when practical.
6. Leave the repository with a clear knowledge map and explicit next steps for any unfinished maintenance automation.

## What To Produce

Aim to leave behind some combination of:

- updated repository entrypoints
- updated indexes and cross-links
- clarified source-of-truth routing
- generated reference artifact links where they exist
- lightweight checks or TODO scaffolding for doc drift

## Rules

- Prefer repository-local, versioned knowledge over chat-only explanations.
- Keep entrypoint docs short and navigational.
- Keep indexes current when important docs are added, renamed, or moved.
- If an explanation matters repeatedly to future work, move it into the repository.
- Do not add maintenance machinery the repository cannot realistically keep current.

## Recovery Guidance

If the repository is too early-stage for real checks:

- still improve the routing
- make placeholders honest about what is missing
- leave explicit enforcement hook points for later

The repository should still be more discoverable and less dependent on memory than it was before you started.
