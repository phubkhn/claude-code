# Claude Plugin Notes

This plugin uses a minimal manifest format for compatibility:

- include `version`
- declare `skills` and `commands` as arrays
- avoid custom manifest fields not recognized by Claude validator

Before publishing, validate the manifest with your local Claude CLI.
