# Plugin Schema Notes

These conventions are derived from real-world Claude plugin validation behavior.

## Required

- `version` must be present
- `skills` and `commands` should be arrays

## Avoid

- unsupported custom fields in `plugin.json`
- ambiguous path values

## Safe Minimal Shape

```json
{
  "name": "example-plugin",
  "version": "1.0.0",
  "skills": ["./skills/"],
  "commands": ["./commands/"]
}
```
