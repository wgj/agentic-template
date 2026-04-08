---
name: generate-reference-artifacts
description: Generate durable repository reference artifacts such as schema summaries, dependency summaries, route inventories, or command inventories. Use when agents repeatedly need mechanically derivable facts that should live under docs/generated or an equivalent repository-local location.
---

# Generate Reference Artifacts

Use this skill when a repository would benefit from concise, mechanically derived artifacts that future agents can consult without rediscovering the same facts repeatedly.

The goal is to create generated reference material that supports the repository knowledge base, not to replace the source code or hand-written design docs.

## Workflow

1. Identify facts the agent repeatedly needs but currently has to rediscover.
2. Prefer facts that can be derived mechanically from the repository or runtime.
3. Generate concise artifacts and place them under `docs/generated/` or the target repository's equivalent.
4. Record how the artifacts were generated and how to refresh them.
5. Link the generated artifacts from the nearest useful index or entrypoint.

## Good Candidates

- schema summaries
- route or endpoint inventories
- dependency summaries
- command or runbook inventories
- ownership or module maps

## Rules

- Prefer generated artifacts over hand-maintained copies when the facts can be derived mechanically.
- Keep generated artifacts concise and navigable.
- Document regeneration steps or the generating command when practical.
- Do not generate artifacts that are expensive to maintain but rarely used.

## Recovery Guidance

If a full generator is not warranted yet:

- create the smallest useful artifact by hand
- explain how a future generator could replace it
- link it from the repository knowledge base so it is discoverable now
