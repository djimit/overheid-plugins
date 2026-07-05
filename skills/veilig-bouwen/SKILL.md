---
name: veilig-bouwen
version: 1.0.0
description: >
  Secure development lifecycle voor overheidssoftware. OWASP Top 10 preventie,
  SAST/DAST/SCA tooling, supply chain security, pentest procedures.
  Gebruik bij software-ontwikkeling voor de Nederlandse overheid.
triggers:
  keywords: [veilig bouwen, secure development, OWASP, SAST, DAST, SCA, supply chain, pentest, security review, vulnerability, CVD, security.txt]
tools: [Read, Glob, Grep, Bash]
---

# Veilig Bouwen (Secure Development)

Secure development lifecycle voor overheidssoftware.

## Wanneer deze skill gebruiken

- Security code review
- SAST/DAST/SCA tooling configureren
- Supply chain security check
- Pentest voorbereiden
- CVD opzetten
- Security.txt implementeren

## OWASP Top 10 Preventie

| Risico | Preventie | Tooling |
|--------|-----------|---------|
| A01: Broken Access Control | RBAC, ABAC | ZAP, Burp |
| A02: Crypto Failures | TLS 1.3, AES-256 | testssl.sh |
| A03: Injection | Parameterized queries | sqlmap, Semgrep |
| A04: Insecure Design | Threat modeling | Microsoft TMT |
| A05: Security Misconfig | Hardening, CIS | kube-bench |
| A06: Vuln Components | SCA | Snyk, Trivy |
| A07: Auth Failures | MFA, session mgmt | OWASP ASVS |
| A08: Data Integrity | Signing, checksums | Sigstore |
| A09: Logging Failures | Structured logging | ELK, Grafana |
| A10: SSRF | Allowlists | Semgrep |

## SAST Tooling

| Tool | Taal | Integratie |
|------|------|-----------|
| Semgrep | Multi | GitHub Actions |
| SonarQube | Multi | CI/CD |
| Bandit | Python | pre-commit |
| ESLint Security | JS/TS | pre-commit |
| Trivy | Multi | GitHub Actions |

## DAST Tooling

| Tool | Type | Gebruik |
|------|------|---------|
| OWASP ZAP | Proxy | Automated + manual |
| Burp Suite | Proxy | Manual |
| Nikto | Scanner | Web server |
| testssl.sh | Scanner | TLS |
| nuclei | Scanner | Templates |

## SCA Tooling

| Tool | Functie | Integratie |
|------|---------|-----------|
| Snyk | Vuln + license | GitHub Actions |
| Trivy | Container + FS | GitHub Actions |
| Dependabot | GitHub native | GitHub native |
| OSV-Scanner | Vuln database | CLI |

## Supply Chain Security

| Maatregel | Implementatie |
|-----------|--------------|
| Dependency pinning | Lock files |
| Checksum verification | --require-hashes |
| Signed commits | GPG signing |
| SLSA provenance | Sigstore, in-toto |
| SBOM generation | Syft, CycloneDX |
| Container signing | Cosign, Notary |

## Pentest Procedures

| Fase | Activiteit |
|------|-----------|
| 1. Voorbereiding | Scope, RoE, contactpersonen |
| 2. Uitvoering | Recon, scanning, exploitatie |
| 3. Rapportage | Bevindingen, risico's, maatregelen |

## CVD Procedure

1. Ontvang melding
2. Bevestig ontvangst (24u)
3. Valideer kwetsbaarheid
4. Ontwikkel fix
5. Test en deploy
6. Publiceer advisory

## Security.txt

```
Contact: mailto:security@mijnorganisatie.nl
Expires: 2027-01-01T00:00:00.000Z
Encryption: https://mijnorganisatie.nl/pgp-key.txt
Preferred-Languages: nl, en
Canonical: https://mijnorganisatie.nl/.well-known/security.txt
```

## Gerelateerde skills

- bio-security-baseline: BIO2
- llm-security: LLM security
- developer-overheid: Developer richtlijnen
- cloud-overheid: Cloud security
- nis2-compliance: NIS2
- privacy-cookies: Privacy

## Bronnen

- OWASP: owasp.org
- NCSC: ncsc.nl
- CVD: first.org/cvss
- Security.txt: securitytxt.org
- SLSA: slsa.dev
