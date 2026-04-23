---
name: security-review
description: Cross-cutting security checklist and review workflow for code that handles authentication, user input, secrets, APIs, files, payments, and sensitive data.
---

# Security Review

Use this skill to run a practical security pass before merge or release.

## When To Use

- New API endpoints
- Authentication or authorization changes
- Database query changes
- File upload/download features
- Payment or transaction flows
- External API integrations
- Secret management changes

## Security Checklist

### 1) Secrets

- Never hardcode API keys, tokens, passwords, or private keys
- Read secrets from environment or secret manager
- Ensure `.env` and local secret files are ignored by Git
- Rotate secrets immediately if exposed

### 2) Input Validation

- Validate all request payloads with explicit schema rules
- Enforce length/type/range constraints
- Use allowlists over blocklists
- Return safe errors without internal details

### 3) Injection Defense

- Use parameterized queries only
- Never concatenate SQL/JPQL/HQL with user input
- Validate and normalize path/file input
- Avoid shell execution from user input

### 4) AuthN / AuthZ

- Protect sensitive endpoints with authentication middleware
- Enforce authorization checks before state-changing actions
- Apply least-privilege roles
- Use secure session/token handling and expiration

### 5) Output / Logging Safety

- Never log credentials, tokens, or sensitive PII
- Sanitize user-controlled content before rendering
- Keep stack traces and internals out of API responses

### 6) Dependency Security

- Review Maven/Gradle or Go module dependencies for known CVEs
- Patch critical/high vulnerabilities before release
- Remove unused or unmaintained packages

## Java / Spring Boot Focus

- Add `@Valid` for `@RequestBody` and validate DTOs
- Use `@PreAuthorize` / method security for restricted operations
- Keep CSRF/CORS/security config explicit and justified
- Ensure `@Transactional` boundaries avoid partial state updates

## Output Template

```text
Security Status: PASS | FAIL
Critical Issues: N
High Issues: N
Medium Issues: N
Files Reviewed: ...
Required Fixes: ...
```

If any CRITICAL issue is found, block merge until fixed.
