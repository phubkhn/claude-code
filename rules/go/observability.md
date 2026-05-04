# Go Observability Standards

## Logging

- Use structured logs (key-value fields), not free-form-only logs.
- Include correlation context (request ID, trace ID, tenant ID when applicable).
- Log at appropriate levels with actionable messages.
- Avoid logging sensitive data.

## Metrics

- Expose latency, throughput, and error-rate metrics on critical paths.
- Use stable metric names and bounded-cardinality labels.
- Track dependency call health separately for major downstream services.

## Tracing

- Propagate trace context across service and queue boundaries.
- Create spans around critical external calls and expensive operations.
- Annotate spans with error outcomes and retry metadata.

## Health and Operability

- Liveness should indicate process health only.
- Readiness should include dependency readiness needed for safe traffic.
- Surface degraded dependency mode explicitly when partial service is still available.

## Incident Readiness

- Ensure logs and metrics can answer: what failed, where, for whom, and since when.
- Ensure alerting thresholds exist for sustained error-rate and latency spikes.
