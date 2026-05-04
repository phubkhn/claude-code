---
name: go-project-review
description: End-to-end Golang project review skill for architecture, code quality, security, testing, performance, and operability.
origin: claude-code-go-reviewer-kit
---

# Go Project Review

## Goal

Provide a structured end-to-end review for a Golang project, not just individual diffs.

## Activation Criteria

Use this skill when you need one of the following:

- baseline quality assessment for a repository
- release-readiness review
- architecture and operational risk review
- deep review after major refactor or incident

## Required Inputs

- repository structure and key modules
- build/test command results
- deployment/runtime assumptions when available

## Review Workflow

### Phase 1: Repository Mapping

- map modules, package boundaries, and dependency direction
- identify critical paths (write path, auth path, async processing path)
- identify external dependencies and failure-sensitive integrations

### Phase 2: Quality and Correctness

- evaluate error handling consistency
- evaluate contract behavior and compatibility
- evaluate concurrency safety and cancellation behavior

### Phase 3: Security and Dependency Risk

- evaluate authn/authz boundaries
- evaluate input validation and injection resistance
- evaluate secret handling and dependency CVE risk

### Phase 4: Testing and Validation Depth

- evaluate unit/integration/e2e coverage of critical paths
- evaluate regression testing for known bug classes
- evaluate race and reliability test coverage for concurrent components

### Phase 5: Performance and Operability

- evaluate hot-path allocation and I/O patterns
- evaluate observability (logs, metrics, traces)
- evaluate readiness/liveness and graceful shutdown behavior

### Phase 6: Architecture and Evolution Risk

- evaluate module cohesion and coupling
- evaluate migration and rollout safety
- evaluate resilience under retries, delays, and dependency degradation

## Required Standards References

Apply all files in `rules/go/` during this review.

## Output Format

### Executive Summary

- project quality snapshot
- top risks by severity

### Findings

For each finding include:

- severity
- location (file/module)
- impact
- evidence
- required action

### Readiness Decision

- release-ready / conditionally ready / not ready
- blocking issues
- hardening backlog (post-release)
