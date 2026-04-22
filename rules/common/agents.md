# Agent Orchestration

## Available Agents In This Repo

Located in `agents/`:

| Agent | Purpose | When to Use |
|-------|---------|-------------|
| go-reviewer | Go code review | After Go changes |
| go-build-resolver | Go build/vet/lint fixes | Go build or compile failures |
| java-reviewer | Java/Spring code review | After Java changes |
| java-build-resolver | Java/Maven/Gradle build fixes | Build or compile failures |
| security-reviewer | Security vulnerability review | Before merge/release, auth/input/payment changes |

## Immediate Usage

Use these proactively without waiting for explicit prompt:

1. Go code changed -> run `go-reviewer`
2. Java/Spring code changed -> run `java-reviewer`
3. Go build is failing -> run `go-build-resolver`
4. Java build is failing -> run `java-build-resolver`
5. Security-sensitive code changed -> run `security-reviewer`

## Parallel Execution

Run agents in parallel when tasks are independent.

Example:

1. Agent A reviews security-sensitive endpoints
2. Agent B reviews language-specific quality (Go or Java)
3. Agent C verifies build and tests

## Escalation Rule

If `go-reviewer` or `java-reviewer` finds CRITICAL security issues, escalate to `security-reviewer`.
