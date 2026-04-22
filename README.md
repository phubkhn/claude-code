# Claude Code Dev Kit

Documentation and starter skeleton to standardize how your team uses **Claude Code**:
- Organize `skills`, `hooks`, and `commands` in a scalable structure.
- Prepare a clean base to package as a plugin later.
- Include local installation guidance from day one.

## Goals

- Use this repository as the source of truth for Claude Code workflows.
- Centralize best practices for prompts, skills, hooks, and commands.
- Evolve it into a team-maintained Claude Code plugin.

## Repository Structure

```text
.
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   └── README.md
├── hooks/
│   └── README.md
├── skills/
│   └── README.md
└── docs/
    └── INSTALL_PLUGIN.md
```

## Core Components

### 1) Skills

- Store focused workflows by use case:
  - feature delivery
  - code review
  - bug fixing
  - test authoring
- Each skill should contain:
  - `SKILL.md`
  - input/output examples
  - explicit quality gates

Details: `skills/README.md`

### 2) Hooks

- Automate checks before and after tasks:
  - format/lint
  - fast unit tests
  - policy checks
- Reduce errors during agent-driven code changes.

Details: `hooks/README.md`

### 3) Commands

- Standardize frequently used commands:
  - environment bootstrap
  - test execution
  - validation pipeline
- Map these to team command shortcuts when needed.

Details: `commands/README.md`

## Plugin Skeleton

This repository includes:

- `.claude-plugin/plugin.json`

This manifest is the minimum starting point for an internal plugin package. You can extend it with:
- metadata versioning
- public skill listings
- hook registration
- command aliases

## Local Plugin Installation

See:

- `docs/INSTALL_PLUGIN.md`

## Contribution Rules

- Keep content short, clear, and runnable.
- Every change should be tied to a practical use case.
- New skills must include goal, input/output contract, and verification checklist.

## Suggested Roadmap

- V1: standardize docs and skill templates.
- V2: standardize lint/test/policy hooks.
- V3: complete plugin packaging and release process.
