---
name: bootstrap-application-legibility
description: Bootstrap application legibility for Codex in a repository. Use when the user wants an agent to make a project easier to inspect, run, validate, and reason about through repo-local docs, bootable workflows, inspectable UI, and queryable runtime signals.
---

# Bootstrap Application Legibility

Use this skill to install the "increasing application legibility" pattern into a repository that does not fully have it yet.

The goal is to make the application more legible to an agent while it works. From the agent's point of view, anything it cannot access in-context while running effectively does not exist.

## Workflow

1. Inspect the repository and identify what the agent cannot currently see or exercise directly.
2. Find the highest-leverage missing surfaces first: startup, health, primary user journeys, UI state, logs, metrics, traces, or key background work.
3. Add or update repository-local docs that explain how to boot the app, inspect it, and validate the important flows.
4. Prefer per-task or isolated workflows when the repository can support them.
5. Expose the UI through direct inspection surfaces when possible: browser automation, DOM snapshots, screenshots, or equivalent helpers.
6. Expose queryable runtime signals when possible: logs, metrics, traces, health endpoints, or focused debug output.
7. Prefer repository-local, versioned artifacts over chat-only explanations.
8. Leave explicit validation steps the next agent can run.
9. If the application is too early-stage for full observability, leave durable scaffolding and the clearest next step.

## What To Produce

Aim to leave behind some combination of:

- startup or local-environment instructions
- health-check or smoke-test instructions
- docs for how to inspect UI or runtime behavior
- generated or checked-in reference artifacts the agent can read later
- task-focused observability hooks or TODO scaffolding for them

## Rules

- Legibility is about the running system, not only the source tree.
- Prefer tools and dependencies the agent can understand and modify in-repo.
- Keep important operating knowledge in versioned repository artifacts.
- Favor the smallest set of observability improvements that let an agent reproduce bugs and validate fixes directly.
- Do not claim the repository is observable if the agent still has no concrete way to inspect the behavior.

## Good First Targets

- application startup and health checks
- the primary UI flow or API route involved in common issues
- structured logs for the subsystem being changed
- latency or error metrics for important paths
- concise reference docs for local tools, external systems, or workflows the agent repeatedly needs

## Recovery Guidance

If the repository does not yet have enough of a running application to support full legibility work:

- document the intended operating surface
- add the smallest runnable or inspectable hook the repository can support now
- record what is still missing for full agent-operable validation

Leave behind something concrete the next agent can discover and build on.
