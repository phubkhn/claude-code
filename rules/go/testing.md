# Go Testing Standards

## Coverage Policy

- Cover all critical domain rules and failure paths.
- Every bug fix must include a regression test.
- Add concurrency tests (or race-enabled tests) for shared-state paths.
- Cover contract behavior for public handlers and adapters.

## Test Design

- Prefer table-driven tests for behavior matrices.
- Use behavior-focused test names that describe expected outcomes.
- Keep unit tests deterministic with no external side effects.
- Prefer lightweight fakes over brittle, deep mocking setups.

## Layered Test Strategy

### Unit Tests

- Validate domain logic and pure transformations.
- Assert error classification and wrapped context.

### Integration Tests

- Validate repository behavior against real storage behavior when possible.
- Validate adapter contracts (HTTP/gRPC/queue) for serialization and status mapping.

### End-to-End Critical Flows

- Validate write-path idempotency.
- Validate retry/timeouts under dependency failures.
- Validate backward compatibility for public API changes.

## Required Validation Commands

```bash
go test ./...
go test -race ./...
go test -cover ./...
```
