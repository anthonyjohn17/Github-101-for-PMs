---
name: codebase-inventory
description: Deep-scans any repository to build a complete, non-destructive inventory of structure, technologies, entry points, naming and branding traces, and operational risks. Use when a user asks to understand a codebase end-to-end before refactoring, cleanup, redesign, migration, or documentation work.
---

# Codebase Inventory

## Purpose

Deep-scan repositories to understand structure and everything about the codebase.

This skill is discovery-first and report-first. It does not modify files. It produces a thorough, meticulous, human-readable inventory that can guide downstream skills and implementation decisions.

## Key design principles

- Non-destructive scanning first: never modify files, only report.
- Context-aware analysis: understand project type (Node library, Python tool, React app, monorepo, and similar patterns) before suggesting any follow-up action.
- Evidence-based findings: each major conclusion should cite concrete files, symbols, or config artifacts.
- Explicit uncertainty: unknowns and low-confidence inferences are labeled, never hidden.

## Required inputs

- Path to repository root.
- Project type hint (optional; this skill can auto-detect).

## Optional smart inputs (recommended)

- Scan depth: `quick`, `standard`, or `thorough`.
- Scope filter: full repo or selected directories/packages.
- Exclusion overrides: paths to skip or include beyond defaults.
- Inventory focus: architecture, naming/branding, security posture, test readiness, release readiness.
- Intended downstream goal: cleanup, refactor, migration, docs rewrite, portfolio publication.

## Required output

A human-readable summary report that is thorough and meticulous, including:

- All instances of creator/project naming traces.
- Marketing language or boilerplate flagged for review.
- Project structure and entry points identified.

## Recommended output artifacts

- `CODEBASE_INVENTORY.md` (primary human-readable report).
- `.inventory-state.json` (structured machine-readable extraction for downstream skills).
- `INVENTORY_RISKS.md` (optional expanded risk and unknowns register for large repos).

## Non-destructive guarantee

This skill must not write, rename, delete, or auto-fix code. If follow-up changes are useful, list them as recommendations only.

## Default scan boundaries

Skip or deprioritize by default:

- `node_modules`, `.git`, package manager caches, build outputs, generated bundles.
- Large binaries and media unless they are relevant to branding, docs, runtime assets, or legal markers.
- Vendored dependencies unless explicitly in scope.

Always scan these high-signal zones when present:

- top-level docs and metadata (`README`, `LICENSE`, `NOTICE`, changelog, contribution guides)
- build and package manifests
- CI/CD and deployment configs
- source roots, app/package boundaries, entry points, and tests

## Inventory dimensions

### 1) Repository identity and metadata

- repository name and inferred domain
- legacy naming traces (project names, creator handles, org identifiers)
- branding markers in docs, code comments, UI text, and config
- license and notice presence (identify, do not interpret legally beyond explicit text)

### 2) Technology and runtime profile

- primary and secondary languages
- frameworks, runtimes, package managers, build systems
- workspace style (single project vs. monorepo)
- toolchain indicators (linters, formatters, test frameworks, type systems)

### 3) Structural topology

- directory and package/module layout
- dependency boundaries and cross-package references
- internal service/app relationships
- generated vs. hand-authored zones

### 4) Execution surfaces and entry points

- app start points, CLI entry points, server boot files
- build scripts, task runners, release scripts
- test entry points and smoke/integration harnesses
- deployment and environment bootstrap points

### 5) Quality and maintenance signals

- test presence and test density by area (high-level estimate)
- lint/type/format setup status
- stale docs or abandoned modules
- TODO/FIXME concentration and commented-out code hotspots

### 6) Naming and content cleanup candidates

- creator/project references with path frequency
- marketing or promotional boilerplate candidates
- inconsistent naming domains (packages, modules, env vars, identifiers)
- confidence-scored flags:
  - `high`: likely safe finding
  - `medium`: plausible, needs review
  - `low`: ambiguous, manual confirmation required

## Required workflow

1. **Read the repository holistically first**
   - Establish top-level map before deep detail extraction.
2. **Auto-detect project type and scale**
   - Identify language/framework/workspace signatures.
3. **Perform layered scan**
   - metadata and docs -> configs/tooling -> source topology -> execution surfaces -> quality signals.
4. **Extract findings with evidence**
   - Each section includes concrete paths and a concise rationale.
5. **Classify by certainty and impact**
   - certainty (`high/medium/low`) and impact (`high/medium/low`) for each major finding.
6. **Produce meticulous report**
   - prioritize readability, decision usefulness, and clear next-step readiness.

## Report template

Use this structure for `CODEBASE_INVENTORY.md`:

```markdown
# Codebase Inventory Report

## 1. Executive Snapshot
- Repository:
- Scan depth:
- Detected project type:
- Monorepo/single-project:
- Primary languages/frameworks:

## 2. Structure Overview
- Top-level layout summary
- Package/app boundaries
- Entry points and run surfaces

## 3. Identity and Branding Findings
- Creator/project naming traces (with representative paths)
- Marketing/boilerplate flags
- Notes requiring human review

## 4. Technology and Tooling
- Build/test/lint/type systems
- CI/CD and release tooling
- Environment/config patterns

## 5. Quality and Risk Signals
- Testing posture
- Maintenance hotspots
- Ambiguous or high-risk zones

## 6. Inventory Tables
- Key files and purpose
- Entrypoints matrix
- Optional package/module dependency map

## 7. Recommended Next Actions (non-destructive)
- Suggested cleanup candidates
- Suggested documentation updates
- Suggested refactor investigation targets

## 8. Unknowns and Assumptions
- Items requiring manual confirmation
```

## Quality bar

Before concluding, verify:

- [ ] No file modifications were performed.
- [ ] Project type inference is explicit and evidenced.
- [ ] Creator/project naming traces are listed with representative paths.
- [ ] Marketing/boilerplate candidates are clearly separated from required/legal text.
- [ ] Entry points and structural boundaries are documented.
- [ ] Unknowns are called out without overconfident claims.

## Escalation guidance

If the repository is very large or ambiguous:

- run a staged pass (topology first, deep scan second)
- declare coverage limits explicitly
- provide a prioritized follow-up scan plan rather than speculative conclusions
