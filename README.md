# Agent-First Repository Template

This repository is a greenfield template for making a project legible to coding agents, especially Codex.

It is intentionally minimal. The goal of this pass is not to define a full engineering handbook. The goal is to establish the repository structure and the key markdown entrypoints that an agent can rely on.

## What This Template Includes

- [AGENTS.md](AGENTS.md): the repository-local map for agents
- [GLOBAL_AGENTS.md](GLOBAL_AGENTS.md): a template for `~/.Codex/AGENTS.md`
- [ARCHITECTURE.md](ARCHITECTURE.md): the top-level architecture map
- [PLANS.md](PLANS.md): the root execution-plan standard
- `docs/`: source-of-truth folders and placeholders for durable repository knowledge

## What Inspired It

This template is based primarily on:

- OpenAI, [Harness engineering: leveraging Codex in an agent-first world](https://openai.com/index/harness-engineering/)
- The open [`AGENTS.md`](https://agents.md/) format
- OpenAI Cookbook, [Using PLANS.md for multi-hour problem solving](https://developers.openai.com/cookbook/articles/codex_exec_plans)

## Design Intent

The main ideas carried into this template are:

- keep `AGENTS.md` short and navigational
- make repository knowledge the system of record
- use progressive disclosure instead of one giant instruction file
- keep complex work resumable through checked-in execution plans
- encode architecture and stable quality preferences as repository-local invariants
- prefer enforcing important invariants mechanically instead of relying on repeated review comments

## Template Notes

- `PLANS.md` lives at the project root.
- The supporting files under `docs/` are placeholders unless otherwise stated.
- This pass avoids expanding into project-specific policy that is not directly supported by the sources above.

## Installing Into Another Project

An agent working in another repository can use this template as a starting point.

Recommended approach:

1. Inspect the target repository first.
2. Add only the files and directories that fit the target repository.
3. Place the core files at the target project root:
   - `AGENTS.md`
   - `README.md`
   - `ARCHITECTURE.md`
   - `PLANS.md`
4. Add the `docs/` directories and placeholder files if the target repository does not already have better source-of-truth locations.
5. Merge carefully with existing project docs rather than overwriting them blindly.
6. Rewrite copied files so they describe the target repository, not this template repository.
7. If the user also wants a Codex home-level default, install `GLOBAL_AGENTS.md` separately as `~/.codex/AGENTS.md`.

When installing this template into another project, the agent should preserve:

- existing repository-specific conventions
- stronger existing documentation
- real architecture and product language already present in the target project

The agent should replace:

- placeholder text
- template-specific references
- paths or examples that only make sense in this repository

## Installing "Enforcing Architecture and Taste" Into Another Project

Use this pattern when the target repository wants Codex or another coding agent to preserve architecture boundaries and quality expectations mechanically instead of learning them only through repeated review comments.

Apply the pattern in this order:

1. Inspect the target repository and identify the real architecture it should preserve: business domains, layers inside each domain, runtime boundaries, and cross-cutting interfaces.
2. Write a short repository-local architecture document that defines those units in repository terms.
3. Declare the allowed dependency directions explicitly.
4. Treat the architecture as a closed world: once the allowed edges are listed, anything else is disallowed until the docs are updated.
5. Require validation or parsing at important system boundaries without over-prescribing the exact library unless the repository already standardizes on one.
6. Add mechanical enforcement immediately using a linter rule, dependency-boundary check, structural test, or CI script.
7. Add a small set of high-value taste invariants that protect legibility and reliability, such as structured logging, naming rules, or file-size limits.
8. Make every enforcement failure explain the violated invariant and the expected remediation so the next agent can recover quickly.
9. Feed repeated review comments back into the repository as documentation updates, checks, or both.

When doing this work in another repository, do not start by copying example boundaries from this template. Derive the actual rules from the target repository's real modules, layers, and runtime entrypoints.

Use wording like this in the target repository's architecture docs:

    Architecture units:
    - Each business domain contains `types -> repo -> service -> runtime -> ui`.
    - Cross-cutting concerns enter through `providers`.

    Allowed dependency directions:
    - `types -> repo`
    - `repo -> service`
    - `service -> runtime`
    - `runtime -> ui`
    - `providers -> runtime`

    Any dependency edge not listed here is disallowed until the architecture docs and enforcement are updated together.

Use wording like this for a boundary-validation invariant:

    Data entering the system at network, storage, or third-party boundaries must be validated or parsed at the boundary before deeper layers depend on it.

Use wording like this in the target repository's `AGENTS.md`:

    If the repository defines allowed dependency directions, layering rules, domain boundaries, or boundary-validation requirements, treat all other approaches as disallowed. Do not introduce a new dependency edge or bypass a declared boundary invariant unless the repository docs and enforcement are updated together.

When choosing what to enforce, prefer small, high-value invariants such as:

- forbidden layer crossings
- domain boundary violations
- required validation at system boundaries
- naming or file-layout rules that protect navigation and readability
- structured logging requirements
- file-size or complexity limits in areas that agents repeatedly overgrow

The important pattern is:

- define the architecture in repository terms
- list the allowed edges explicitly
- treat everything else as disallowed
- enforce the rule mechanically
- encode a small set of taste invariants
- make failures teach the agent how to recover

Avoid turning the target repository into a giant style guide. Enforce invariants, not implementations. Leave local implementation freedom inside safe and documented boundaries.
