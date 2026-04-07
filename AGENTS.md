# AGENTS.md

This file is for a brand new Codex thread starting with fresh context.

Your job is to get up to speed quickly enough to create or implement product specs and ExecPlans without relying on unstated context.

Treat this file as the repository entrypoint. Read it first, then gather the rest of the context from the files it names.

This repository is a template for installing an agent-first documentation structure into a project. The immediate goal in this repository is usually one of these:

- create or improve a repository-local product spec
- create or improve an ExecPlan
- adapt this template so it can be installed into another project cleanly

## Read This First

When starting work:

1. Read this file.
2. Read [README.md](README.md).
3. Read [ARCHITECTURE.md](ARCHITECTURE.md).
4. Read [PLANS.md](PLANS.md).
5. Read the most relevant source-of-truth docs listed below.
6. Read the closest nested `AGENTS.md` only if one exists near the files you will change.

## Source-Of-Truth Docs

Start small, then drill down:

- [README.md](README.md): what this template is and what inspired it.
- [ARCHITECTURE.md](ARCHITECTURE.md): top-level architecture map.
- [PLANS.md](PLANS.md): the execution-plan standard.
- [docs/design-docs/index.md](docs/design-docs/index.md): design-doc catalog.
- [docs/product-specs/index.md](docs/product-specs/index.md): product-spec catalog.
- [docs/exec-plans/active/README.md](docs/exec-plans/active/README.md): active execution plans live here.
- [docs/exec-plans/completed/README.md](docs/exec-plans/completed/README.md): completed execution plans live here.
- [docs/exec-plans/tech-debt-tracker.md](docs/exec-plans/tech-debt-tracker.md): tracked debt.
- [docs/generated/README.md](docs/generated/README.md): generated reference artifacts.
- [docs/references/README.md](docs/references/README.md): local reference material for agents.

## Primary Outcomes

Use this repository structure to do two things well:

1. Create clear, repository-local product specs.
2. Create or implement ExecPlans that another fresh-context agent could resume from.

If you are changing the template itself, keep the entrypoint files coherent:

- `README.md` explains what the template is and how to install it.
- `AGENTS.md` gets a fresh-context repository agent oriented.
- `GLOBAL_AGENTS.md` stays abstract and cross-project.
- `PLANS.md` defines the ExecPlan standard used by the repository.
- `ARCHITECTURE.md` describes the top-level repository shape.

## Specs

When the task is to define behavior, read the relevant files under `docs/product-specs/` and either create a new spec or update an existing one.

Write specs so they are:

- repository-local
- user-facing
- testable
- specific enough to guide implementation

Prefer updating `docs/product-specs/index.md` when new specs are added or renamed.

## ExecPlans

When the task is a complex feature, significant refactor, or other multi-step implementation, use an ExecPlan as described in [PLANS.md](PLANS.md).

If you write an ExecPlan, make it self-contained enough that a new agent could continue from the plan alone.

Use `docs/exec-plans/active/` for in-progress ExecPlans and `docs/exec-plans/completed/` for completed ones.

## Documentation Layout

This repository follows a progressive-disclosure model:

- keep `AGENTS.md` short
- store durable detail in repository files
- use nested `AGENTS.md` files only where local guidance differs

In this repository, the main durable locations are:

- `docs/product-specs/` for specs
- `docs/design-docs/` for design and architecture notes
- `docs/exec-plans/` for execution plans
- `docs/generated/` for generated reference artifacts
- `docs/references/` for local reference material useful to agents

## Fresh-Context Rules

- Do not assume prior conversation history is available.
- Do not assume architecture that is not written down.
- Prefer reading the repository over asking for routine context.
- If important knowledge is missing, add it to the repository in the right place.
- When a repeated architecture or quality preference becomes clear, prefer recording it as a repository-local invariant and, when appropriate, adding a mechanical check so future agents inherit it.

## Nested AGENTS

The closest `AGENTS.md` wins for local conventions and validation steps. If instructions conflict:

1. Explicit user instructions win.
2. The nearest `AGENTS.md` wins over this repository root file.
3. Repository source-of-truth docs win over stale prose.

If a local area has no nested `AGENTS.md`, follow this file plus the relevant docs.
