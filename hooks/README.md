# Hooks Directory

## Recommended Hooks

Recommended hooks for Go review workflows:

- `pre-commit`: run `go test ./...` and `go vet ./...`
- `pre-push`: run `go test -race ./...` when feasible
- `post-task`: summarize findings by severity

## Guidelines

Guidelines:
- Keep hooks fast and deterministic.
- On failure, provide direct remediation steps.
