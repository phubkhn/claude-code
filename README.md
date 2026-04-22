# Claude Code Backend Plugin Kit

This repository is a focused Claude Code plugin workspace for backend teams using Java/Spring and Go.

## Goals

- Keep reusable Java/Spring, Go, and security workflows in one place.
- Provide a plugin-ready structure for local install and future publishing.
- Standardize review, build-fix, and security workflows.

## Current Structure

```text
.
├── .claude-plugin/
│   └── plugin.json
├── agents/
│   ├── go-build-resolver.md
│   ├── go-reviewer.md
│   ├── java-build-resolver.md
│   ├── java-reviewer.md
│   └── security-reviewer.md
├── commands/
│   ├── README.md
│   ├── code-review.md
│   └── gradle-build.md
├── docs/
│   └── INSTALL_PLUGIN.md
├── hooks/
│   └── README.md
├── rules/
│   ├── common/
│   └── java/
├── skills/
│   ├── golang-patterns/
│   ├── java-coding-standards/
│   ├── jpa-patterns/
│   ├── security-review/
│   ├── springboot-patterns/
│   ├── springboot-security/
│   ├── springboot-tdd/
│   ├── springboot-verification/
│   └── README.md
└── README.md
```

## Key Components

### Agents

- `go-reviewer`: Go code review gate.
- `go-build-resolver`: Go build/vet/lint issue fixer.
- `java-reviewer`: Java and Spring Boot review gate.
- `java-build-resolver`: Maven/Gradle build issue fixer.
- `security-reviewer`: vulnerability-focused reviewer.

### Rules

- `rules/common/`: cross-project guardrails (workflow, security, hooks, code review).
- `rules/java/`: Java/Spring conventions and checks.

### Skills

- Go development patterns via `golang-patterns`.
- Framework and architecture skills for Spring Boot.
- Dedicated `security-review` skill for security triage and checklists.

### Commands

- Reusable command documents for review and build workflows.

## Plugin Manifest Notes

Plugin config lives in `.claude-plugin/plugin.json`.
It follows an array-based component layout compatible with Claude plugin validation.

## Installation

Use [docs/INSTALL_PLUGIN.md](/Users/dirak/Documents/AI/POC_MAKER/claude_code/claude-code/docs/INSTALL_PLUGIN.md).

## Contribution Rules

- Keep docs and instructions concrete and runnable.
- Prefer small, task-specific skills and agents.
- Keep commit messages short.
