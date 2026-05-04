# Go Security Standards

## Input and Validation

- Validate all input from HTTP, queues, and CLI boundaries.
- Enforce strict schema and type checks before business logic.
- Reject unexpected fields for security-sensitive payloads.

## Blocker Patterns

- SQL query concatenation with user input.
- Shell command execution with raw user input.
- User-controlled file path access without canonicalization and root allowlisting.
- Hardcoded secrets in code, tests, or fixtures committed to repository.
- TLS configuration with `InsecureSkipVerify: true` without approved exception.

## Authentication and Authorization

- Enforce authn/authz checks on all sensitive operations.
- Distinguish between authentication failures and authorization failures.
- Avoid information leakage through detailed auth error messages.

## Sensitive Data Handling

- Never log passwords, tokens, or sensitive PII.
- Redact sensitive fields in logs and metrics labels.
- Encrypt sensitive at-rest data when regulatory or business requirements apply.

## Dependency and Supply Chain

- Run `govulncheck ./...` regularly.
- Pin and review high-risk dependencies.
- Patch high/critical CVEs before release, or apply documented compensating controls.

## Transport and Network

- Enforce TLS for external traffic.
- Use request timeouts to limit abuse windows.
- Apply rate limiting to authentication and expensive endpoints.
