---
name: bootstrap-architecture-enforcement
description: Bootstrap architecture-and-taste enforcement in a repository. Use when the user wants Codex to add explicit architectural boundaries, closed-world dependency rules, boundary-validation invariants, or mechanical enforcement such as lint, structural tests, or CI checks.
---

# Bootstrap Architecture Enforcement

Use this skill to install the "enforcing architecture and taste" pattern into a repository that does not fully have it yet.

The goal is not to invent a rigid architecture from thin air. The goal is to extract the real structure of the repository, document the important invariants, and scaffold enforcement so future agents inherit the rule.

## Workflow

1. Inspect the repository before proposing rules.
2. Identify the real architecture units that matter: domains, layers, boundaries, and cross-cutting interfaces.
3. Draft or update repository-local docs that define those units in repository terms.
4. Define the allowed dependency directions explicitly.
5. State that once allowed edges are listed, undeclared edges are disallowed until the docs and enforcement are updated together.
6. Add or update `AGENTS.md` so future agents know not to bypass those invariants.
7. Add the cheapest credible enforcement path the repository can support now.
8. Prefer a small set of high-value taste invariants over a giant style guide.
9. Leave the repository with clear next steps if full enforcement is not possible yet.

## What To Produce

Aim to leave behind some combination of:

- a short architecture or design doc naming the units and allowed edges
- a short `AGENTS.md` rule pointing future agents at those invariants
- a lint rule, dependency-boundary check, structural test, CI script, or explicit TODO scaffold
- remediation-oriented failure messages or comments explaining how to recover

## Rules

- Enforce invariants, not implementations.
- Do not copy architecture examples blindly; derive rules from the target repository.
- Prefer closed-world wording once the allowed edges are known.
- Require validation or parsing at important system boundaries when that invariant matters.
- Keep the invariant set small and high-value.
- If the repository is too early-stage for real enforcement, still create the docs and the enforcement hook point so something durable exists.

## Good First Invariants

- forbidden layer crossings
- domain boundary violations
- required validation at system boundaries
- naming or file-layout rules that protect readability
- structured logging requirements
- file-size or complexity limits in areas that agents repeatedly overgrow

## Recovery Guidance

If you cannot add real enforcement yet, do not pretend it exists. Instead:

- document the intended invariant
- add a clear placeholder for the future check
- explain what concrete runtime, module structure, or tool support is still missing

The repository should still be more explicit and more enforceable than it was before you started.
