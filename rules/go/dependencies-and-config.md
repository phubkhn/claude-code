# Go Dependency and Configuration Standards

## Dependency Hygiene

- Keep dependencies minimal and actively maintained.
- Prefer stable versions with clear update history.
- Remove unused dependencies after refactors.

## Vulnerability Management

- Run vulnerability scans as part of regular review cadence.
- Escalate high/critical CVEs with explicit mitigation timeline.
- Document temporary compensating controls when immediate patching is not possible.

## Configuration Management

- Keep runtime configuration explicit and validated at startup.
- Fail fast for missing required configuration.
- Keep environment-variable names stable and documented.

## Secrets Management

- Load secrets from secure environment or secret manager.
- Do not commit secrets to repository.
- Avoid printing secrets in startup logs and diagnostics.

## Deployment Safety

- Keep default values safe for production where possible.
- Document config changes required by new features.
- Validate backward compatibility for config migrations.
