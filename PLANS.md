# Codex Execution Plans (ExecPlans)

This file defines the standard for an execution plan, or "ExecPlan". An ExecPlan is a design-and-implementation document that a coding agent can follow to deliver a working feature or system change.

Treat the reader as a complete beginner to this repository. They have only the current working tree and the single ExecPlan file in front of them. Assume no memory of earlier work and no external context.

## How to use ExecPlans and PLANS.md

When authoring an ExecPlan, follow this file closely. Re-read it before writing or revising a plan.

When implementing an ExecPlan:

- continue from milestone to milestone without asking the user for routine "next steps"
- keep the plan up to date at every stopping point
- resolve ambiguities inside the plan and record the decision
- make it possible for another contributor to restart from the ExecPlan alone

When research is still needed, use milestones to validate feasibility with prototypes, toy implementations, or other focused experiments. Record what was learned and how it changed the plan.

## Requirements

These requirements are non-negotiable:

- Every ExecPlan must be fully self-contained.
- Every ExecPlan must be a living document.
- Every ExecPlan must enable a complete novice to complete the work end to end.
- Every ExecPlan must aim at demonstrably working behavior, not just code edits.
- Every ExecPlan must define non-obvious terms in plain language.

Start by explaining why the work matters from a user or operator point of view. Describe what becomes possible after the change and how a contributor can see it working.

Do not assume the reader can infer missing context. Repeat assumptions that matter. If knowledge is required, place it in the plan in your own words. If the plan builds on an earlier checked-in ExecPlan, incorporate that earlier plan by reference and restate any details the reader needs.

## Formatting

The formatting rules are intentionally strict:

- An ExecPlan should be one Markdown document.
- If you are presenting an ExecPlan inline, wrap it in a single fenced code block labeled `md`.
- If the ExecPlan is itself stored as a `.md` file, do not add outer triple backticks.
- Do not nest triple-backtick fences inside an ExecPlan. Use indented blocks for commands, transcripts, diffs, and snippets.
- Use normal Markdown headings and leave two blank lines after each heading.

Write in plain prose. Narrative sections should stay prose-first. Use lists only where they help clarity. The `Progress` section is the one place where a checkbox list is mandatory.

## Guidelines

Self-containment and plain language matter more than brevity.

If you introduce a term that is not ordinary English, define it immediately and tie it to this repository by naming the relevant files, modules, commands, or runtime behavior.

Do not rely on external blogs or architecture docs to fill in essential context. Bring the required explanation into the plan itself.

Anchor the plan in observable outcomes. State what the user or operator will be able to do, what commands to run, and what outputs or behavior to expect.

Name repository paths precisely. When describing edits, say exactly which files, modules, or functions are involved and where new files should be created.

Write steps so they are safe to repeat. If a step can fail halfway, explain how to retry, recover, or roll back safely.

Validation is required. Include tests, startup steps, direct system exercise when applicable, and the expected observations that prove the change works.

When terminal output, logs, diffs, or short transcripts help prove progress, include concise examples as indented blocks.

## Milestones

Milestones should read like a story, not bureaucracy.

If the work is broken into milestones, each milestone should explain:

- the scope of the milestone
- what will exist afterward that does not exist yet
- what commands should be run
- what acceptance the reader should observe

Milestones and progress are different. Milestones describe the narrative shape of the work. Progress tracks the granular current state. Both must exist.

Each milestone should be independently verifiable and should move the overall plan toward a working outcome.

## Living Plans and Design Decisions

Every ExecPlan must contain and maintain these sections:

- `Progress`
- `Surprises & Discoveries`
- `Decision Log`
- `Outcomes & Retrospective`

When design decisions are made, record both the decision and the reasoning behind it.

When unexpected behavior, performance tradeoffs, bugs, or implementation constraints shape the work, capture them in `Surprises & Discoveries` with short evidence.

If the implementation changes direction, update the plan and explain why.

At major milestones and at the end of the work, write an `Outcomes & Retrospective` entry describing what was achieved, what remains, and what was learned.

## Prototyping Milestones and Parallel Implementations

Explicit prototyping milestones are acceptable when they reduce risk or answer key feasibility questions.

Keep prototypes additive, testable, and clearly labeled as prototypes. Explain how to run them, what to observe, and what result would justify promoting or discarding them.

Parallel implementations can also be acceptable during a migration when they reduce risk. If so, explain how both paths are validated and how one path will be retired safely.

## Skeleton of a Good ExecPlan

# <Short, action-oriented description>

This ExecPlan is a living document. The sections `Progress`, `Surprises & Discoveries`, `Decision Log`, and `Outcomes & Retrospective` must be kept current as work proceeds.

This document must be maintained in accordance with `/PLANS.md`.

## Purpose / Big Picture

Explain what someone gains after this change and how they can see it working. State the user-visible or operator-visible behavior that will exist when the work is complete.

## Progress

Use a checkbox list for granular current state. Every stopping point must be reflected here.

- [x] (YYYY-MM-DD HH:MMZ) Example completed step.
- [ ] Example incomplete step.
- [ ] Example partial step (completed: X; remaining: Y).

Use timestamps so a later contributor can understand the pace and sequence of work.

## Surprises & Discoveries

Document important unexpected findings and include concise evidence.

- Observation: ...
  Evidence: ...

## Decision Log

Record meaningful design or implementation decisions in this form:

- Decision: ...
  Rationale: ...
  Date/Author: ...

## Outcomes & Retrospective

Summarize outcomes, remaining gaps, and lessons learned. Compare the result against the original purpose.

## Context and Orientation

Describe the current state relevant to this task as if the reader knows nothing. Name the key files and modules by full repository-relative path. Define any non-obvious terms used in the rest of the plan.

## Plan of Work

Describe, in prose, the sequence of edits and additions. For each change, name the file and location and explain what will change there.

## Concrete Steps

List the exact commands to run and the working directory for each command. When a command should produce visible output, include a short expected transcript as an indented example.

## Validation and Acceptance

Explain how to start or exercise the system and what to observe. Phrase acceptance as behavior with specific inputs and outputs. If tests are involved, state the exact test command and what result should be expected.

## Idempotence and Recovery

Explain which steps are safe to repeat. If any step is risky, provide a safe retry, rollback, or cleanup path.

## Artifacts and Notes

Include the most important concise transcripts, diffs, or notes that help a future contributor understand and verify the work.

## Interfaces and Dependencies

Be explicit about libraries, modules, services, types, interfaces, and function signatures that must exist or be used at the end of the work.

## Revision Rule

When an ExecPlan is revised, update all affected sections so the document remains internally consistent. Add a short note at the bottom describing what changed and why.
