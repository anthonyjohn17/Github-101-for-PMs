---
name: forge-recast
description: Reconstructs README and technical documentation from the actual refactored codebase and approved cleanup manifest. Use after repository cleanup planning or approved refactors when the user needs accurate docs, architecture notes, specs, or publication-ready project framing.
---

# Forge Recast

## Purpose

This skill performs the second phase of the repository transformation: `Recast`.

Its job is to interpret the cleaned codebase, rebuild the narrative around what the system actually does, and generate documentation that is accurate, useful, and publication-ready.

This is not marketing copy generation. It is code-driven documentation reconstruction.

## Preconditions

Use this skill only after `forge-melt` has produced and received review on:

- `.refactor-manifest.json`
- `.refactor-summary.md`
- `.refactor-state.json`
- `LICENSE_AUDIT.md`

If those do not exist, state that the documentation base is incomplete.

## Primary Rule

Document what the code does now, not what the old project claimed to be and not what the future roadmap might someday include.

If functional intent is unclear, say so and mark the uncertainty instead of inventing capability.

## Outcomes

Produce or propose:

- a fresh `README.md`
- supporting technical docs
- a documentation coverage report
- a documentation review summary for human approval

## Required Inputs

Gather or infer:

- repository root
- approved Melt outputs
- current source layout
- entry points and public APIs
- target audience:
  - developers
  - end users
  - evaluators
  - employers / portfolio reviewers
- documentation scope:
  - minimal
  - standard
  - comprehensive

## Required Outputs

Core outputs:

- `README.md`
- `ARCHITECTURE.md`
- `DOCS_REVIEW.md`

Optional outputs by repo type:

- `API.md`
- `USAGE.md`
- `DECISIONS.md`
- `ROADMAP.md`
- `.docs-coverage.json`

## What This Skill Must Understand

Before drafting docs, determine:

- the repository type:
  - library
  - CLI
  - web app
  - API service
  - full-stack app
  - monorepo
  - template or starter
- the primary user journey
- the main executable or import surface
- the core modules and boundaries
- the setup path
- the current maturity level
- any legal attribution that must remain visible

## README Requirements

A strong generated `README.md` should usually contain:

1. Project name
2. Short overview
3. Why the project exists
4. Key features that are actually present
5. Architecture or component summary
6. Setup instructions
7. Usage examples
8. Development workflow
9. Repository structure for larger projects
10. Roadmap or next-step direction, clearly marked if aspirational
11. Attribution and notice section when required

## Documentation Rules

### Accuracy first

Every major claim should be traceable to the current codebase, configuration, or approved plan.

### Present tense over aspiration

Prefer:
- "The API exposes..."
- "The CLI supports..."

Avoid:
- "This platform revolutionizes..."
- "This project aims to maybe..."

### Preserve legal visibility

If `forge-melt` marked attribution as required, include it in the README or linked notice path.

### Match documentation to project type

Examples:

- libraries need installation, API surface, and examples
- apps need setup, env vars, architecture, and screenshots if available
- monorepos need package map, workspace relationships, and per-package entry points
- CLIs need command synopsis and examples

### Distinguish current vs planned

Separate:
- implemented features
- planned improvements
- known gaps

## Recommended Workflow

### 1. Read the handoff artifacts

Extract from Melt:

- approved renames
- preserved legal notices
- risky areas
- project identity decisions
- unresolved questions

### 2. Reverse-engineer the codebase

Identify:

- entry points
- exported modules
- routes, commands, or UI flows
- configuration surfaces
- major dependencies
- package relationships

### 3. Reframe the system

Define:

- what the cleaned project is now
- what problem it solves
- what architectural story is real and defensible
- where it differs from the prior source identity

### 4. Draft the docs set

At minimum:
- `README.md`
- `ARCHITECTURE.md`

For larger or API-heavy repos:
- `API.md`
- `USAGE.md`
- `DECISIONS.md`

### 5. Produce a review summary

State:

- what was documented directly from code
- what was inferred with moderate confidence
- what remains ambiguous
- what needs human tone review
- what legal attribution was carried forward

## Human Review Gate

Before final publication or write approval, require human review for:

- tone and positioning
- claim accuracy
- public-facing naming
- roadmap statements
- attribution wording
- whether the system is framed as a library, tool, app, or platform

This gate should happen before docs overwrite user-edited public docs.

## Handoff To Next Skill

This skill hands off:

- `README.md`
- `ARCHITECTURE.md`
- optional technical docs
- `DOCS_REVIEW.md`
- `.docs-coverage.json` if generated
- updated `.refactor-state.json`

`forge-polish` should validate these outputs against the manifest and current codebase.

## Rerun Strategy

This skill should be rerunnable without flattening human edits.

On rerun:

- compare docs to current code and prior docs
- preserve human-reviewed sections where possible
- update only stale or unsupported claims
- flag drift instead of silently rewriting approved narrative
- record unresolved diffs in `DOCS_REVIEW.md`

## Quality Bar

This skill succeeds when the docs are:

- code-grounded
- legally compliant
- readable by a public audience
- appropriately scoped to the project type
- specific about setup and usage
- honest about maturity and limits

## Failure Conditions

Stop and escalate if:

- the codebase intent cannot be inferred with acceptable confidence
- the public API is unstable and undocumented
- setup instructions cannot be validated even at a high level
- legal attribution requirements conflict with the proposed public framing
- the code and manifest disagree in ways that affect core claims

## Example Triggers

Use this skill for prompts like:

- "Generate a fresh README from the cleaned codebase."
- "Write architecture docs after the repo cleanup pass."
- "Rebuild the docs for this refactored monorepo."
- "Document this project accurately for public publication."
- "Create portfolio-grade docs without inventing capabilities."
