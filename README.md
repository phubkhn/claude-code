# Claude Code Backend Plugin Kit

This repository is a Claude Code plugin workspace for backend teams working on Java/Spring Boot and Go services.

## Goals

- Keep reusable Java/Spring Boot, Go, and security workflows in one place.
- Provide a plugin-ready structure for local install and future publishing.
- Standardize review, build-fix, and security workflows for Java/Go codebases.

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

- `rules/common/`: guardrails shared across Java/Go workflows.
- `rules/java/`: Java/Spring Boot conventions and checks.

### Skills

- Go development patterns via `golang-patterns`.
- Framework and architecture skills for Spring Boot.
- Dedicated `security-review` skill for security triage and checklists.

### Commands

- Reusable command documents for Java/Go review and build workflows.

## Plugin Manifest Notes

Plugin config lives in `.claude-plugin/plugin.json`.
It follows a minimal array-based component layout compatible with Claude plugin validation.

## Scope

This kit is intentionally focused on:

- Java and Spring Boot services
- Go services and libraries
- Security review for Java/Go backend code

It does not aim to provide Node.js, Rust, or Python workflows.

## Installation

Use [docs/INSTALL_PLUGIN.md](docs/INSTALL_PLUGIN.md).

## How To Use

Use the repo as a shared operating guide for Claude Code:

- pick a language-specific reviewer from `agents/`
- apply `rules/common/` plus `rules/java/` when working on Spring Boot code
- reuse `skills/` for implementation patterns and verification checklists
- run `commands/` as repeatable review/build workflows

The repo currently documents agents, rules, and hooks as workspace conventions. The plugin manifest currently exposes `skills` and `commands`.

## Contribution Rules

- Keep docs and instructions concrete and runnable.
- Prefer small, task-specific skills and agents.
- Keep commit messages short.
