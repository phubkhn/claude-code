# Go Architecture Review Standards

## Module Boundaries

- Keep domain ownership explicit and cohesive.
- Prevent cyclic dependencies between packages/modules.
- Keep dependency direction stable: transport -> application -> domain -> infrastructure.
- Avoid leaking infra concerns into domain core.

## Contract Management

- Document compatibility impact for API or event changes.
- Provide migration strategy for breaking contract changes.
- Keep request/response DTOs isolated from persistence models.

## Reliability Model

- Define timeout budgets per external dependency.
- Use retry with bounded attempts, jitter, and clear stop conditions.
- Define fallback behavior for dependency degradation.
- Ensure async workflows include DLQ, compensation, or deterministic replay.

## Data Correctness

- Guard against double-write and partial-write failure modes.
- Make consistency model explicit (strong vs eventual) by use case.
- Ensure idempotency for write operations exposed to retries.
- Keep schema changes rollout-safe and backward compatible.

## Scalability

- Bound fan-out, queue growth, and worker concurrency.
- Avoid O(n) request-time operations on unbounded datasets.
- Ensure backpressure strategy is explicit across async boundaries.

## Operability and Observability

- Emit structured logs with correlation IDs.
- Track latency, error-rate, and throughput metrics on critical paths.
- Ensure readiness/liveness checks reflect true dependency health.
- Support graceful shutdown and safe draining of in-flight work.
