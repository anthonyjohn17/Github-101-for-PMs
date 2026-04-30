---
name: forge-polish
description: Validates that a transformed repository is technically clean, legally compliant, clearly documented, and genuinely differentiated enough for public publication. Use after cleanup and documentation work when preparing a repo for portfolio release, publication review, or final readiness scoring.
---

# Forge Polish

## Purpose

This skill performs the third phase of the repository transformation: `Polish`.

Its job is to decide whether the repository is ready for public publication and to explain why, using measurable checks rather than vibes.

This is the final gate before presenting the work as portfolio-grade.

## Preconditions

Use this skill after `forge-melt` and `forge-recast` have produced their outputs.

Expected inputs:

- `.refactor-manifest.json`
- `LICENSE_AUDIT.md`
- `README.md`
- `ARCHITECTURE.md` when applicable
- optional API or usage docs
- updated `.refactor-state.json`

## Primary Rule

Do not confuse cosmetic cleanup with meaningful transformation.

This skill must explicitly assess whether the repository demonstrates real differentiation through:
- feature originality
- abstraction changes
- architectural differentiation

If the work is mostly renaming and surface cleanup, say so clearly.

## Outcomes

Produce or propose:

- `PORTFOLIO_READY_CHECKLIST.md`
- `REMEDIATION_SUGGESTIONS.md`
- `.publish-readiness.json`
- a final readiness verdict:
  - `ready`
  - `ready-with-caveats`
  - `not-ready`

## Validation Areas

### 1. Legal readiness

Check that:

- license obligations identified in Melt are still satisfied
- required notices are present
- attribution has not been removed where required
- docs and repo metadata do not misrepresent provenance

### 2. Repository hygiene

Check for:

- stale branding remnants
- placeholder text
- dead docs
- obvious TODO/FIXME leakage in public-facing paths
- abandoned sample apps or broken examples
- inconsistent naming after refactor

### 3. Technical quality

Check whether the repository appears publishable by its own standards:

- linting or style conventions
- formatting consistency
- type checking when applicable
- tests or verification strategy
- dependency hygiene
- entry-point integrity
- setup clarity
- error-handling maturity

### 4. Documentation quality

Check whether docs are:

- accurate
- complete enough to onboard a reader
- consistent with the actual codebase
- explicit about limitations
- clear about installation, setup, and usage
- legally correct where attribution is required

### 5. Portfolio value

Evaluate whether the repository is interesting and differentiated enough to showcase.

This requires more than "looks cleaner now."

## Transformation Quality Rubric

Score each from `0` to `5`.

### Feature originality

- `0`: no meaningful feature change
- `1`: trivial parameter or naming changes
- `2`: small additions without product impact
- `3`: at least one clear new capability
- `4`: several meaningful new capabilities or workflows
- `5`: substantially expanded problem-solving scope

### Abstraction changes

- `0`: no abstraction change
- `1`: renamed files or symbols only
- `2`: minor wrapper or organizational changes
- `3`: improved module boundaries or API design
- `4`: materially improved domain model or extension points
- `5`: clearly stronger system abstractions than the source baseline

### Architectural differentiation

- `0`: same structure with cosmetic edits
- `1`: light file movement only
- `2`: modest restructuring without new operational shape
- `3`: changed component relationships or runtime flow
- `4`: major architectural improvements with clear rationale
- `5`: substantially different and more defensible architecture

### Publication clarity

- `0`: not understandable
- `1`: basic README only
- `2`: setup is present but thin
- `3`: docs are functional and credible
- `4`: docs are strong and reviewer-friendly
- `5`: docs and structure strongly signal craftsmanship

## Readiness Heuristic

Use the rubric with the validation areas to produce a verdict.

Suggested interpretation:

- `ready`: no legal blockers, no critical usability blockers, transformation quality is meaningfully above cosmetic
- `ready-with-caveats`: publishable, but there are notable gaps or weak differentiation
- `not-ready`: legal, technical, or originality concerns make public publication premature

## Required Workflow

### 1. Reconcile the handoff chain

Verify consistency across:
- manifest
- docs
- current repository state

Look for drift and unresolved items.

### 2. Run publication checks

Check:
- naming consistency
- setup plausibility
- artifact cleanliness
- doc completeness
- residual legacy references
- legal markers

### 3. Score transformation quality

Assess feature originality, abstraction changes, and architectural differentiation using the rubric above.

### 4. Separate blockers from improvements

Classify findings as:

- `blocker`
- `major`
- `minor`
- `nice-to-have`

### 5. Produce final outputs

`PORTFOLIO_READY_CHECKLIST.md` should include:
- pass/fail checklist
- blocker list
- caveats
- quality scores
- publication verdict

`REMEDIATION_SUGGESTIONS.md` should include:
- specific next fixes
- priority order
- ownership hints if relevant
- whether each fix is mandatory or optional

## Human Review Gate

Before final publication, require human confirmation on:

- legal sufficiency
- public narrative accuracy
- whether the project is genuinely differentiated enough to showcase
- whether caveats are acceptable for the intended audience

This is the final gate even if all automated checks look good.

## Rerun Strategy

This skill must support repeated use.

On rerun:

- preserve previous findings history where possible
- compare prior scores to new scores
- surface regressions
- mark resolved blockers
- avoid changing the verdict without explaining why

## Success Criteria

Polish succeeds when:

- there are no unresolved legal blockers
- the repo is clean and understandable
- docs match the codebase
- remaining issues are clearly classified
- the publication verdict is justified
- transformation quality is measured, not hand-waved

## Failure Conditions

Stop and return `not-ready` if:

- attribution obligations appear violated
- the repo does not run or cannot be reasoned about sufficiently
- documentation materially misstates capabilities
- the transformation remains mostly cosmetic
- major unresolved quality issues undermine portfolio credibility

## Example Triggers

Use this skill for prompts like:

- "Is this repo ready to publish?"
- "Run a final portfolio-readiness review."
- "Check whether this refactor is meaningfully different or just cosmetic."
- "Validate legal, technical, and documentation readiness before GitHub."
- "Score this transformed repo for showcase quality."
