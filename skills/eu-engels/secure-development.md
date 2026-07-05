---
name: secure-development
version: 1.0.0
language: en
description: >
  Secure development lifecycle for government software. OWASP Top 10,
  SAST/DAST/SCA, supply chain security.
triggers:
  keywords: [secure development, OWASP, SAST, DAST, supply chain]
tools: [Read, Glob, Grep]
---

# Secure Development

## OWASP Top 10

Broken Access Control, Crypto Failures, Injection, Insecure Design,
Security Misconfig, Vuln Components, Auth Failures, Data Integrity,
Logging Failures, SSRF.

## Tooling

| Type | Tools |
|------|-------|
| SAST | Semgrep, SonarQube |
| DAST | OWASP ZAP |
| SCA | Snyk, Trivy |

## Related: bio2-baseline, llm-security, privacy-cookies
