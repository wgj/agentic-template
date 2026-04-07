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
