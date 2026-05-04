# Commands Directory

This directory contains reusable command docs for Go review workflows.

## Available Command

- `code-review.md`: detailed review workflow for PR/MR scope or full-source workspace scope

## Command Coverage

The code review command covers:

- validation execution (`go test`, `go vet`, `staticcheck`, `go test -race`)
- standards application across all `rules/go/*`
- severity-based decision output (`APPROVE`, `APPROVE WITH COMMENTS`, `REQUEST CHANGES`, `BLOCK`)
