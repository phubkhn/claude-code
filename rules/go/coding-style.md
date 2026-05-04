# Go Coding Style Standards

## Package and Module Design

- Use short lowercase package names without underscores.
- Keep package responsibility narrow and explicit.
- Avoid generic utility packages with mixed concerns.
- Keep dependency direction stable (domain packages must not import infra packages).

## Public API Design

- Export only types and functions required outside the package.
- Keep constructors explicit (`NewX`) for types with invariants.
- Prefer concrete return types for constructors and factory functions.
- Keep interfaces on the consumer side and as small as possible.

## Function and Method Design

- Keep functions single-purpose and readable.
- Prefer early returns to reduce nesting.
- Place `context.Context` as the first parameter for operations involving I/O or downstream calls.
- Avoid boolean parameter flags that change behavior mode; split into explicit methods.

## Error Handling

- Never ignore errors unless it is clearly best-effort cleanup.
- Wrap errors with operation context using `%w`.
- Use `errors.Is` and `errors.As` for classification.
- Keep error strings lowercase and without trailing punctuation.

## Data and Mutability

- Avoid mutable global state.
- Minimize shared mutable state across goroutines.
- Prefer immutable value flow for domain objects.
- Be explicit about pointer vs value semantics for structs.

## Concurrency Safety

- Do not hold locks across network or database calls.
- Ensure every goroutine has a stop condition and cancellation path.
- Document ownership for channels and close responsibility.
- Avoid unbounded worker creation without concurrency limits.
