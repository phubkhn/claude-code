---
name: go-architecture-review
description: Architecture-focused Go review skill covering boundaries, reliability, data correctness, scalability, and operability.
origin: claude-code-go-reviewer-kit
---

# Go Architecture Review

## Goal

Detect structural design risks that line-level review often misses.

## Trigger Conditions

Use this skill when a change introduces:

- new packages/modules or dependency direction changes
- queue, scheduler, worker, or async behavior changes
- storage model, transaction, or consistency model changes
- public API, schema, or event contract changes

## Review Workflow

1. Map module and dependency changes.
2. Map data flow and failure modes end to end.
3. Evaluate runtime behavior under retry, timeout, and degraded dependency scenarios.
4. Evaluate observability and operational safety.
5. Produce risks and required pre-merge fixes.

## Architecture Checklist

### Boundary Clarity

- Is module ownership explicit?
- Is dependency direction correct?
- Any layer leak or package cycle?

### Reliability

- Are timeouts explicit for each external call?
- Are retries bounded, jittered, and idempotent-safe?
- Are partial failures handled predictably?

### Data Correctness

- Any double-write/partial-write risk?
- Is consistency model explicit and justified?
- Is migration/rollback path safe?

### Scalability

- Any unbounded fan-out, queue growth, or memory growth?
- Any request-path O(n) operations on unbounded sets?
- Is backpressure explicit?

### Operability and Observability

- Are logs structured with correlation context?
- Are critical metrics and traces present?
- Is readiness/liveness behavior production-safe?
- Is graceful shutdown draining in-flight work?

## Output Format

- architecture strengths
- architecture risks (severity + impact)
- required pre-merge fixes
- post-merge hardening recommendations
