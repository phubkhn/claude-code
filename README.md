# Claude Code Go Reviewer Kit

This repository is a Go-only Claude Code plugin/workspace for deep code and architecture reviews.

## Scope

The kit is built for reviewing production Golang projects across these dimensions:

- correctness and API behavior
- security and dependency risk
- concurrency and reliability
- performance and scalability
- observability and operability
- architecture and module boundaries

## Structure

```text
.
├── .claude-plugin/
│   └── plugin.json
├── agents/
│   └── go-reviewer.md
├── commands/
│   ├── README.md
│   └── code-review.md
├── docs/
│   └── INSTALL_PLUGIN.md
├── hooks/
│   └── README.md
├── rules/
│   └── go/
│       ├── api-and-contracts.md
│       ├── architecture.md
│       ├── coding-style.md
│       ├── dependencies-and-config.md
│       ├── observability.md
│       ├── performance.md
│       ├── review-checklist.md
│       ├── security.md
│       └── testing.md
└── skills/
    ├── golang-patterns/
    ├── go-review-standards/
    ├── go-architecture-review/
    ├── go-project-review/
    └── README.md
```

## Review Stack

- Agent: `go-reviewer`
- Command workflow: `commands/code-review.md`
- Detailed standards: `rules/go/*`
- Skills:
  - `go-review-standards` for severity and merge decisions
  - `go-architecture-review` for structural risk analysis
  - `go-project-review` for end-to-end project review
  - `golang-patterns` for idiomatic implementation patterns

## How to Use

1. Run `go-reviewer` for every Go change.
2. Execute validation commands from `code-review.md`.
3. Evaluate findings against `rules/go/review-checklist.md`.
4. Trigger architecture or project-level skills for non-trivial system changes.

## Installation

Install directly from GitHub (without Marketplace): `docs/INSTALL_PLUGIN.md`.
