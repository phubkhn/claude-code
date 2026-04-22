# Install This Plugin Locally (Claude Code)

This guide explains how to install this repository as a local plugin for Claude Code.

## 1) Clone The Repository

```bash
git clone https://github.com/phubkhn/claude-code.git
cd claude-code
```

## 2) Verify The Plugin Manifest

Make sure this file exists:

```text
.claude-plugin/plugin.json
```

## 3) Link It Into Your Claude Code Plugin Path

Depending on your local setup, you can:
- register this repository in your Claude Code local plugin list
- or create a symlink into the plugin directory Claude Code scans

Example symlink (Linux/macOS):

```bash
mkdir -p "$HOME/.claude/plugins/local"
ln -s "$(pwd)" "$HOME/.claude/plugins/local/claude-code-dev-kit"
```

If your Claude Code installation uses a different plugin directory, adjust the path accordingly.

## 4) Restart Claude Code

- Restart the app/CLI so the new plugin is loaded.
- Confirm that skills/hooks/commands from this repo are visible.

## 5) Smoke Test

- Open `skills/`, `hooks/`, and `commands/`
- Add one sample skill
- Reload Claude Code and verify the skill appears

## Recommended Next Steps

- Split skills by domain: backend/frontend/devops
- Add a `pre-commit` hook for lint/test
- Build command templates by stack (Python/Node/Go)
