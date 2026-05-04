---
name: go-review-standards
description: Detailed Go review rubric with severity model, mandatory validation, and decision policy.
origin: claude-code-go-reviewer-kit
---

# Go Review Standards

## Goal

Standardize review decisions and reduce subjective variance across reviewers.

## Activation Criteria

Use this skill for any Go review where merge approval or change rejection is required.

## Severity Rubric

### CRITICAL

- exploitable security vulnerability
- data corruption or irreversible data loss risk
- race/deadlock path likely in production

### HIGH

- correctness bug in business logic
- contract break without compatibility or migration strategy
- missing timeout/cancellation in critical call chain
- missing authz check for sensitive operation

### MEDIUM

- test gap with real regression risk
- maintainability issue likely to increase defect rate
- performance risk with measurable production impact

### LOW

- readability or style issue with minimal behavior risk

## Mandatory Validation

Run and record results for:

```bash
go test ./...
go vet ./...
staticcheck ./... 2>/dev/null || echo "staticcheck not installed"
go test -race ./... 2>/dev/null || echo "race test skipped"
```

If scope includes performance-critical paths, include benchmark evidence when available.

## Review Workflow

1. Identify review scope and impacted boundaries.
2. Review changed `.go` files in full context.
3. Apply all standards in `rules/go/*`.
4. Classify findings by severity.
5. Decide merge outcome using policy below.

## Decision Policy

- `BLOCK`: any CRITICAL finding
- `REQUEST CHANGES`: any HIGH finding or mandatory validation failure
- `APPROVE WITH COMMENTS`: only MEDIUM/LOW findings
- `APPROVE`: no findings and mandatory checks pass

## Required Output Format

For each finding:

- severity
- file:line
- impact
- evidence
- required fix

Final section:

- validation summary
- merge decision
- follow-up actions (if any)
