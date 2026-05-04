description: Detailed Go code review workflow for PR/MR scope or full-source workspace scope
argument-hint: [pr-number | pr-url | mr-url | blank for full-source review]
---

# Go Code Review

## Input

`$ARGUMENTS`

## Mode Selection

- If input contains PR/MR identifier or URL: use **PR/MR Review Mode**.
- Otherwise: use **Full Source Review Mode** (entire workspace, not git diff).

## Full Source Review Mode

### Phase 1: Gather

```bash
rg --files -g '*.go' -g '!vendor/**' -g '!*_generated.go' -g '!**/*.pb.go'
```

If no Go source files are found, stop with `Nothing to review`.

### Phase 2: Validate

```bash
go test ./...
go vet ./...
staticcheck ./... 2>/dev/null || echo "staticcheck not installed"
go test -race ./... 2>/dev/null || echo "race test skipped"
```

### Phase 3: Review

Apply every file from `rules/go/`:

- `coding-style.md`
- `testing.md`
- `security.md`
- `api-and-contracts.md`
- `performance.md`
- `observability.md`
- `dependencies-and-config.md`
- `architecture.md`
- `review-checklist.md`

### Phase 4: Decide

- CRITICAL -> BLOCK
- HIGH -> REQUEST CHANGES
- MEDIUM/LOW -> APPROVE WITH COMMENTS
- no findings + checks pass -> APPROVE

## PR/MR Review Mode

### Phase 1: Fetch

```bash
gh pr view <NUMBER> --json number,title,body,author,baseRefName,headRefName,changedFiles,additions,deletions
gh pr diff <NUMBER>
```

### Phase 2: Context

- Read all `rules/go/*` standards.
- Read full changed `.go` files at PR head.
- Parse PR intent, scope, rollout notes, and test plan.

### Phase 3: Analyze

Report findings by severity with file and line references.
For architectural or cross-module changes, include explicit architecture findings.

### Phase 4: Publish

```bash
gh pr review <NUMBER> --approve --body "<summary>"
gh pr review <NUMBER> --request-changes --body "<required fixes>"
gh pr review <NUMBER> --comment --body "<comments>"
```
