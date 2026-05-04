# Go Review Checklist

## Mandatory Inputs

- changed file list and scope
- validation command results
- rollout or migration notes for non-trivial changes

## Block Immediately

- critical security vulnerability
- reproducible data corruption or loss path
- race/deadlock risk with production impact
- missing authz check on sensitive operation

## Must Fix Before Merge

- high-severity correctness bug
- public contract break without compatibility or migration plan
- missing timeout/cancellation in critical call paths
- missing regression test for bug fix
- mandatory validation failures in touched scope

## Can Merge With Comments

- medium maintainability or performance issue with documented mitigation
- low style/readability issue

## Required Finding Format

- severity
- file:line
- impact
- evidence
- required fix

## Final Decision Rules

- `BLOCK`: any critical issue
- `REQUEST CHANGES`: high-severity issue or failed mandatory checks
- `APPROVE WITH COMMENTS`: medium/low only
- `APPROVE`: no findings and required checks pass
