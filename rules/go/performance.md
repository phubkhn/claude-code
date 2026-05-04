# Go Performance Standards

## Hot Path Review

- Avoid repeated allocations in loops and request hot paths.
- Avoid unnecessary byte/string conversions and object copying.
- Pre-allocate slices and maps when expected size is known.

## I/O and External Calls

- Detect N+1 query or request patterns.
- Batch requests or leverage bulk APIs when safe.
- Ensure all outbound calls have bounded timeout.

## Concurrency and Throughput

- Bound worker pools and goroutine fan-out.
- Avoid lock contention and critical section inflation.
- Use backpressure mechanisms for queues and channels.

## Memory and Resource Management

- Close files, bodies, and network resources in all paths.
- Avoid unbounded in-memory buffering for large payloads.
- Validate queue and cache size limits.

## Performance Validation

- Add benchmarks for high-impact or high-traffic changes.
- Compare baseline before/after for latency and allocation-sensitive paths.
- Validate that optimizations do not reduce correctness or observability.
