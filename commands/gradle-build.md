---
description: Fix Gradle build errors for Java and Spring Boot backend projects
---

# Gradle Build Fix

Incrementally fix Gradle build, test, and compilation errors for Java and Spring Boot backend projects.

## Step 1: Detect Build Configuration

Identify the project type and run the appropriate build:

| Indicator | Build Command |
|-----------|---------------|
| Spring Boot plugin present | `./gradlew build 2>&1` |
| Java plugin only | `./gradlew test classes 2>&1` |
| Multi-module backend build | `./gradlew build 2>&1` |
| Need faster compile-only feedback | `./gradlew compileJava 2>&1` |

Also check `gradle.properties`, `settings.gradle`, `settings.gradle.kts`, and dependency/plugin declarations in `build.gradle` or `build.gradle.kts`.

## Step 2: Parse and Group Errors

1. Run the build command and capture output
2. Separate Gradle configuration errors from Java compilation and test failures
3. Group by module and file path
4. Sort: configuration errors first, then dependency issues, then compilation/test failures

## Step 3: Fix Loop

For each error:

1. **Read the file** — Full context around the error line
2. **Diagnose** — Common categories:
   - Missing import or unresolved reference
   - Type mismatch or incompatible types
   - Missing or incorrect dependency in `build.gradle` / `build.gradle.kts`
   - Annotation processor issue (Lombok, MapStruct, configuration metadata)
   - Test configuration failure
   - Spring Boot context or bean wiring error
   - Java toolchain or source/target mismatch
3. **Fix minimally** — Smallest change that resolves the error
4. **Re-run build** — Verify fix and check for new errors
5. **Continue** — Move to next error

## Step 4: Guardrails

Stop and ask the user if:
- Fix introduces more errors than it resolves
- Same error persists after 3 attempts
- Error requires adding new dependencies or changing module structure
- Gradle configuration phase itself fails repeatedly
- Error is in generated code or requires regeneration tooling the project does not document
- Fix needs repository credentials, private dependencies, or environment-specific secrets

## Step 5: Summary

Report:
- Errors fixed (module, file, description)
- Errors remaining
- New errors introduced (should be zero)
- Suggested next steps

## Common Gradle Backend Fixes

| Error | Fix |
|-------|-----|
| `package ... does not exist` | Add the missing dependency or fix the import |
| `cannot find symbol` | Add import, fix typo, or restore missing type |
| Lombok or MapStruct types not generated | Verify annotation processor configuration |
| `Unsupported class file major version` | Align Java toolchain and Gradle JVM version |
| Spring bean creation failure in tests | Fix missing config, mock, profile, or bean wiring |
| Duplicate class or dependency conflict | Inspect `./gradlew dependencies` or `dependencyInsight` |
| `Could not resolve ...` | Fix repository or dependency version |
| Checkstyle/SpotBugs task failure | Apply the smallest code fix that satisfies the rule |
