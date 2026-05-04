---
name: golang-patterns
description: Idiomatic Go implementation patterns for maintainable, testable, reliable, and production-safe services.
origin: claude-code-go-reviewer-kit
---

# Go Patterns

## Goal

Provide implementation patterns that reduce correctness and operability risk in real Go services.

## Activate When

- writing or refactoring Go modules
- reviewing non-trivial behavior changes
- fixing defects in concurrent or I/O-heavy code

## Core Patterns

### Error and Context Patterns

- wrap errors with operation context using `%w`
- classify errors using `errors.Is` and `errors.As`
- preserve request context across call chains
- treat cancellation and deadline errors explicitly

### Package and Interface Patterns

- place interfaces at consumer boundaries
- keep package responsibilities narrow and explicit
- avoid speculative abstractions with one concrete use
- expose constructors for invariant-protected types

### Concurrency Patterns

- propagate cancellation to goroutines and workers
- bound fan-out and worker pool sizes
- define ownership for channel close responsibilities
- use idempotent handlers for retry-prone async processing

### Resilience Patterns

- apply timeout budgets per dependency
- use bounded retry with backoff and jitter
- define fallback or degradation behavior for critical dependencies
- guard write paths with idempotency semantics

## Anti-Patterns

- ignored errors in request or transaction flow
- fire-and-forget goroutines without lifecycle control
- global mutable state shared across request paths
- unbounded queue/memory growth paths
- SQL concatenation from user input

## Review Prompts

- Is this change safer under retries, delays, and partial failures?
- Does the error chain support fast production debugging?
- Is concurrency bounded and cancellation-aware?
- Does the package boundary stay clear and stable?
