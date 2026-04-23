# Development Workflow

> This file extends [common/git-workflow.md](./git-workflow.md) with the full feature development process that happens before git operations.

The Feature Implementation Workflow describes the development pipeline: local discovery, implementation, verification, code review, and then committing to git.

## Feature Implementation Workflow

0. **Discover & Reuse** _(mandatory before new implementation)_
   - Search the current workspace for similar implementations before writing new code.
   - Read primary framework/library documentation for the APIs you will touch.
   - Prefer adapting an existing project pattern over introducing a brand-new structure.
   - Confirm the build tool and validation commands up front (`go`, `mvn`, or `gradle`).

1. **Plan First**
   - Define the scope, affected files, dependencies, and risks before editing.
   - Break the work into small, verifiable steps.
   - Prefer incremental changes that can be validated quickly.

2. **Test-First When Practical**
   - For bug fixes and new behavior, add or update tests as early as possible.
   - Keep the red -> green -> refactor loop small.
   - If tests cannot be added, document why and compensate with targeted verification.

3. **Code Review**
   - Use **go-reviewer** after writing Go code
   - Use **java-reviewer** after writing Java/Spring code
   - Address CRITICAL and HIGH issues
   - Fix MEDIUM issues when practical

4. **Verify Before Commit**
   - Run the relevant project checks for the affected stack
   - For Go: `go test ./...`, `go vet ./...`, `go build ./...`
   - For Maven: `./mvnw verify -q` or `mvn verify -q`
   - For Gradle: `./gradlew check` and `./gradlew build`

5. **Commit & Push**
   - Keep commit messages short and clear
   - Follow conventional commits format
   - See [git-workflow.md](./git-workflow.md) for commit message format and PR process

6. **Pre-Review Checks**
   - Verify all automated checks (CI/CD) are passing
   - Resolve any merge conflicts
   - Ensure branch is up to date with target branch
   - Only request review after these checks pass
