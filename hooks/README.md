# Hooks Directory

This directory describes hooks used for quality control in Claude Code workflows.

## Common Use Cases

- `pre-task`: validate context before execution
- `pre-commit`: run format + lint + fast tests
- `post-task`: summarize outcome and risks

## Recommendations

- Hooks should be fast and deterministic.
- On failure, return clear messages with direct remediation steps.
