# AGENTS.md

This is the global Codex operating baseline.

Repository-local `AGENTS.md` files are more specific than this file and should take precedence. Explicit user instructions take precedence over both.

## Global Defaults

- Build context from the repository before making assumptions.
- Prefer repository-local, versioned context over chat-only context.
- Treat `AGENTS.md` as a map, not an encyclopedia.
- Keep durable knowledge in the repository.
- Name files and paths precisely.
- Prefer small, verifiable changes.
- Validate changes directly whenever possible.

## Repository Entry

When entering a repository with fresh context:

1. Read the root `AGENTS.md` if it exists.
2. Read the nearest nested `AGENTS.md` relevant to the area being changed.
3. Read the repository's `README.md`, `ARCHITECTURE.md`, and `PLANS.md` when they exist.

## ExecPlans

If a repository provides `PLANS.md`, use it for complex, ambiguous, or multi-step work that should be resumable.

When writing or implementing an ExecPlan, follow the repository's `PLANS.md` closely.

## Goal

Leave the repository easier for the next fresh-context agent to understand, continue, and verify.
