# Install from GitHub (Without Marketplace)

Use this flow when the plugin is not published to Marketplace yet.

## Step 1: Clone from GitHub

```bash
git clone https://github.com/phubkhn/claude-code.git "$HOME/.claude/plugins/src/claude-code-go-reviewer-kit"
cd "$HOME/.claude/plugins/src/claude-code-go-reviewer-kit"
```

## Step 2: Verify Plugin Manifest

Ensure this file exists:

```text
.claude-plugin/plugin.json
```

## Step 3: Register as Local Plugin

```bash
mkdir -p "$HOME/.claude/plugins/local"
ln -sfn "$HOME/.claude/plugins/src/claude-code-go-reviewer-kit" \
  "$HOME/.claude/plugins/local/claude-code-go-reviewer-kit"
```

`ln -sfn` allows re-running the command safely if the link already exists.

## Step 4: Reload Claude Code

Restart Claude Code, then verify:

- `go-reviewer` is available
- skills from `skills/` are available
- `code-review` command is available

## Update to Latest from GitHub

```bash
cd "$HOME/.claude/plugins/src/claude-code-go-reviewer-kit"
git pull --ff-only
```

Reload Claude Code after updating.

## Uninstall

```bash
rm "$HOME/.claude/plugins/local/claude-code-go-reviewer-kit"
rm -rf "$HOME/.claude/plugins/src/claude-code-go-reviewer-kit"
```
