---
name: forge-melt
description: Audits repositories for branding noise, legal attribution obligations, naming normalization opportunities, and safe cleanup planning. Use when preparing an internal or open-source repository for refactoring, publication, identity reset, or portfolio reuse, especially before any write operations.
---

# Forge Melt

## Purpose

This skill performs the first phase of a repository transformation: `Melt`.

Its job is to strip noise, expose structure, and produce a controlled cleanup plan without erasing legal obligations or making cosmetic-only changes.

Use it before documentation regeneration, architectural repositioning, or publication-readiness review.

## Core Rule

This skill is scan-first and review-gated.

It must not treat open-source provenance as disposable. Required licenses, notices, headers, and attribution obligations are a hard gate, not an optional cleanup item.

## Outcomes

Produce four things:

1. A legal and attribution audit.
2. A cleanup and rename manifest.
3. A human-readable review summary.
4. A state record that downstream skills can reuse.

## Required Inputs

Gather or infer:

- Repository root
- Repository type hint, if available
- Desired project identity, if provided
- Scope constraints:
  - full repo vs selected packages
  - rename-only vs cleanup-only vs full Melt pass
- Publication goal:
  - internal cleanup
  - portfolio publication
  - public open-source release

## Required Outputs

Generate or propose these artifacts:

- `.refactor-manifest.json`
- `.refactor-summary.md`
- `.refactor-state.json`
- `LICENSE_AUDIT.md`

Optional supporting outputs for larger repos:

- `.rename-map.json`
- `.removal-log.md`
- `.risk-register.md`

## Hard Gate: License And Notice Audit

Before proposing any write:

1. Detect license files, notice files, copyright headers, and attribution statements.
2. Classify each discovered legal marker:
   - `must-preserve`
   - `must-update`
   - `may-relocate`
   - `manual-review`
3. Identify obligations implied by the repository's license posture:
   - attribution retention
   - notice retention
   - modification notice requirements
   - source distribution obligations
4. Flag uncertainty explicitly. Do not guess on ambiguous licensing.
5. Stop and require human review if:
   - the repo contains multiple licenses
   - licensing is missing or contradictory
   - copied third-party code appears without clear provenance
   - notices are embedded in source headers or generated assets

If this gate is not complete, the Melt phase is incomplete.

## What To Scan

Inspect the repository for:

- Legacy branding and marketing language
- Old project names, author handles, company identifiers, and vanity domains
- Non-essential badges, screenshots, demo links, sponsorship links, and stale announcements
- Legacy CI, release, deployment, and template files
- Orphaned docs, unused scripts, abandoned experiments, and dead example apps
- Symbol and package naming that should be normalized
- Entry points, packages, apps, services, and dependency boundaries
- Signs of monorepo structure or workspace relationships

## What To Ignore By Default

Skip or deprioritize:

- `node_modules`
- build artifacts
- package manager caches
- generated docs
- vendored dependencies
- minified bundles
- lockfiles unless they contain naming or publication issues
- binary assets unless they contain branding or legal markers

## Rename Rules

Renaming must be deliberate and confidence-scored.

Classify rename candidates:

- `safe-global`
- `safe-scoped`
- `risky-semantic`
- `do-not-rename-yet`

Use these principles:

- Prefer semantic preservation over surface consistency.
- Do not rename symbols that are not understood.
- Do not collapse domain distinctions just to make names shorter.
- Do not rename public APIs without marking the compatibility risk.
- In monorepos, account for package boundaries and cross-package imports.

For each rename candidate, record:

- old name
- proposed new name
- scope
- confidence
- rationale
- compatibility risk
- affected files count

## Cleanup Rules

Flag removals in categories:

- `safe-remove`
- `safe-archive`
- `manual-review`
- `must-preserve`

Examples of likely `safe-remove` items:

- stale screenshots
- dead badges
- outdated demo links
- abandoned launch copy
- obsolete migration notes superseded by current architecture

Examples of likely `manual-review` items:

- `.github` workflows
- deployment configs
- benchmark results
- historical docs with architectural value
- examples that double as tests
- old files that may encode legal attribution

## Required Workflow

### 1. Profile the repository

Determine:

- language set
- framework(s)
- package structure
- monorepo vs single-project
- primary entry points
- likely public APIs
- generated vs hand-authored areas

### 2. Run legal audit first

Complete the license and notice classification before proposing removals.

### 3. Build the manifest

Capture:

- branding findings
- legal findings
- rename candidates
- removal candidates
- risky areas
- unknowns
- repo topology
- suggested execution order

### 4. Separate cosmetic from substantive transformation

Call out whether the current plan is only cosmetic.

If the proposed transformation is mostly renames, README rewrites, or branding removal, say so directly and recommend deeper changes later:
- new features
- new abstractions
- architectural differentiation
- improved developer workflows

### 5. Produce review materials

Create a short human-readable summary that answers:

- What can be safely removed?
- What must be preserved?
- What must be reviewed by a human?
- Which renames are safe now?
- Which renames should wait?
- What downstream docs need to be regenerated?

## Review Gate

No writes should happen until a human approves:

- legal classifications
- rename map
- removal list
- risky public API changes
- package or module identity changes

The skill should explicitly ask for approval if it is being used in a write-capable workflow.

## Handoff To Next Skill

This skill hands off:

- `.refactor-manifest.json`
- `.refactor-summary.md`
- `.refactor-state.json`
- `LICENSE_AUDIT.md`

`forge-recast` should consume these directly.

## Rerun Strategy

This skill must be idempotent.

On rerun:

- reuse prior state when valid
- append new findings rather than losing review history
- mark already-approved items separately from newly-detected items
- preserve human decisions
- do not silently widen scope

## Success Criteria

Melt is successful when:

- legal obligations are identified and preserved in the plan
- the repository's real structure is visible
- cleanup candidates are categorized by risk
- rename recommendations are confidence-scored
- the manifest is specific enough for human approval
- downstream documentation work has a stable factual base

## Failure Conditions

Stop and escalate if:

- licensing is unclear
- the repo appears to contain copied code without provenance
- a rename could break external consumers and compatibility is unknown
- the repo topology is too unclear to safely normalize identity
- build output and source are mixed in ways that hide authorship or legal markers

## Example Triggers

Use this skill for prompts like:

- "Audit this repo before I refactor it for portfolio use."
- "Remove old branding but keep anything legally required."
- "Build a cleanup manifest for this monorepo."
- "Find renames that are safe before we rewrite the docs."
- "Prepare this open-source codebase for a legitimate public-facing fork."
