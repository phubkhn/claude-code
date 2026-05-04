# Go API and Contract Standards

## Handler and Transport Rules

- Validate request schema before invoking business logic.
- Return consistent status code mappings for domain errors.
- Keep transport-specific objects out of domain logic.
- Include correlation identifiers in response headers when required by platform standards.

## Backward Compatibility

- Do not silently change public field meaning.
- For breaking changes, provide explicit versioning or migration plan.
- Keep response defaults stable to avoid consumer regressions.

## Error Contract

- Map domain errors to stable transport-level error codes.
- Avoid leaking internal details through client-facing error messages.
- Keep error response shape stable and documented.

## Idempotency and Retries

- Write endpoints exposed to retries must be idempotent.
- Use idempotency keys where duplicate submissions are possible.
- Protect side effects from replay within retry windows.

## Event and Queue Contracts

- Version event payloads for schema evolution.
- Handle unknown fields defensively.
- Ensure consumers tolerate out-of-order delivery where applicable.
