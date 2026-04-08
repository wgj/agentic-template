# Agent-First Repository Template

This repository is a greenfield template for making a project legible to coding agents, especially Codex.

It is intentionally minimal. The goal of this pass is not to define a full engineering handbook. The goal is to establish the repository structure and the key markdown entrypoints that an agent can rely on.

## What This Template Includes

- [AGENTS.md](AGENTS.md): the repository-local map for agents
- [GLOBAL_AGENTS.md](GLOBAL_AGENTS.md): a template for `~/.Codex/AGENTS.md`
- [ARCHITECTURE.md](ARCHITECTURE.md): the top-level architecture map
- [PLANS.md](PLANS.md): the root execution-plan standard
- `.agents/skills/`: optional repo-local bootstrap workflows for Codex
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
- Some parts of this template can be adopted immediately, especially `PLANS.md` and repository-local specs. Other patterns, such as observability-driven legibility and mechanical architecture enforcement, only become useful once the target repository has something concrete to run, inspect, or enforce.

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

Core pattern:

- define the architecture in repository terms
- list the allowed edges explicitly
- treat everything else as disallowed
- enforce the rule mechanically
- encode a small set of taste invariants
- make failures teach the agent how to recover

Use the repo-local skill [`bootstrap-architecture-enforcement`](./.agents/skills/bootstrap-architecture-enforcement/SKILL.md) to apply this workflow in a target repository.

That skill is responsible for:

- extracting real domains, layers, and boundaries from the target repository
- drafting the repository-local docs and `AGENTS.md` rule
- scaffolding or adding the first credible enforcement path
- leaving explicit next steps if the repository is not mature enough for full enforcement yet

The lasting source of truth should still end up in the target repository's own docs, checks, and CI rather than living only in the skill.

## Installing "Increasing Application Legibility" Into Another Project

Use this pattern when the target repository wants Codex or another coding agent to inspect, reproduce, validate, and reason about the application directly instead of relying on human interpretation.

Core pattern:

- make the app bootable per task
- make the UI inspectable
- make runtime signals queryable
- keep important context in the repository
- prefer systems the agent can understand end to end
- let the agent validate outcomes directly instead of relying on human translation

Use the repo-local skill [`bootstrap-application-legibility`](./.agents/skills/bootstrap-application-legibility/SKILL.md) to apply this workflow in a target repository.

That skill is responsible for:

- identifying the highest-leverage missing observability and validation surfaces
- documenting how the target app should be booted, inspected, and validated
- adding or scaffolding the first credible runtime hooks the repository can support
- leaving explicit next steps when the project is still too early-stage for full agent-operable observability

The lasting source of truth should still end up in the target repository's docs, local workflows, and observable runtime surfaces rather than living only in the skill.

## Installing "Knowledge-Base Enforcement" Into Another Project

Use this pattern when the target repository wants Codex or another coding agent to rely on durable, discoverable repository knowledge instead of chat-only explanations or tribal memory.

Core pattern:

- keep entrypoint docs short and navigational
- make source-of-truth docs easy to discover
- keep indexes current
- promote repeated explanations into repository artifacts
- add lightweight maintenance or drift checks where practical

Use the repo-local skill [`bootstrap-knowledge-base-enforcement`](./.agents/skills/bootstrap-knowledge-base-enforcement/SKILL.md) to apply this workflow in a target repository.

That skill is responsible for:

- identifying the repository's real knowledge entrypoints
- improving source-of-truth routing and index coverage
- scaffolding checks or maintenance points for doc drift
- leaving explicit next steps where the knowledge base is still incomplete

The lasting source of truth should still end up in the target repository's own docs and generated artifacts rather than living only in the skill.

## Installing "Documentation Gardening" Into Another Project

Use this pattern when the target repository already has docs, but they drift over time and become harder for fresh-context agents to trust.

Core pattern:

- repair stale indexes and cross-links
- keep placeholders honest
- promote repeated chat explanations into docs
- leave the repository easier to navigate after each pass

Use the repo-local skill [`doc-gardener`](./.agents/skills/doc-gardener/SKILL.md) to apply this workflow in a target repository.

That skill is responsible for:

- finding stale routing and missing cross-links
- updating indexes and entrypoint docs
- filling in durable gaps when enough context exists
- making remaining gaps explicit when they cannot be resolved yet

The lasting source of truth should still end up in the target repository's own docs and indexes rather than living only in the skill.

## Installing "Generated Reference Artifacts" Into Another Project

Use this pattern when the target repository needs concise, mechanically derived reference artifacts that agents can consult without rediscovering the same facts repeatedly.

Core pattern:

- identify facts the agent repeatedly needs
- derive them mechanically when possible
- store them in a generated-docs area
- document how they are refreshed
- link them from the nearest useful index

Use the repo-local skill [`generate-reference-artifacts`](./.agents/skills/generate-reference-artifacts/SKILL.md) to apply this workflow in a target repository.

That skill is responsible for:

- identifying high-value generated reference artifacts
- producing the first useful artifact set
- documenting regeneration steps
- linking those artifacts into the repository knowledge base

The lasting source of truth should still end up in the target repository's generated artifacts and index docs rather than living only in the skill.
