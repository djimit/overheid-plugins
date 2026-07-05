---
name: developer-overheid
version: 1.0.0
description: >
  Richtlijnen van developer.overheid.nl voor overheidssoftware-ontwikkeling.
  API's, data, frontend, infrastructuur, security, en open source.
  Gebruik bij software-ontwikkeling voor de Nederlandse overheid.
triggers:
  keywords:
    - developer.overheid.nl
    - overheid developer
    - richtlijnen
    - standaarden
    - API richtlijnen
    - frontend richtlijnen
    - security richtlijnen
    - open source richtlijnen
    - data richtlijnen
    - infrastructuur richtlijnen
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# Developer Overheid

Richtlijnen en standaarden van developer.overheid.nl voor
software-ontwikkeling binnen de Nederlandse overheid.

## Wanneer deze skill gebruiken

- API-ontwikkeling voor overheidsorganisaties
- Frontend-ontwikkeling voor gemeentelijke websites
- Security-implementatie voor overheidssoftware
- Open source keuzes maken
- Data-ontwikkeling en -publicatie
- Infrastructuur-keuzes voor overheids-IT

## API Richtlijnen

### REST API Design Rules

- **OpenAPI 3.0**: Specificatie in OpenAPI 3.0 formaat
- **Versionering**: Semantische versionering (v1, v2)
- **Paginatie**: Offset-based of cursor-based
- **Foutmeldingen**: RFC 7807 Problem Details
- **Content negotiation**: Accept header
- **CORS**: Cross-Origin Resource Sharing
- **Rate limiting**: X-Rate-Limit headers

### OAuth 2.0 / OpenID Connect

- **Client Credentials**: Voor service-to-service
- **Authorization Code**: Voor user-facing apps
- **PKCE**: Voor public clients
- **Token lifetime**: Korte access tokens, lange refresh tokens
- **Scopes**: Fijne granulatie van permissies

### Haal Centraal

- **BRP**: Persoonsgegevens
- **BAG**: Adressen en gebouwen
- **HR**: Handelsregister
- **BRK**: Kadaster
- **WOZ**: Waardering onroerende zaken

## Frontend Richtlijnen

### NL Design System

- **Design tokens**: Kleuren, typografie, spacing
- **Componenten**: Herbruikbare UI-componenten
- **Toegankelijkheid**: WCAG 2.2 AA
- **Rijkshuisstijl**: Huisstijl elementen
- **Community**: Open source community

### Toegankelijkheid

- **WCAG 2.2 AA**: Verplicht voor overheidswebsites
- **EN 301 549**: Europese standaard
- **EAA**: European Accessibility Act
- **Screen reader**: Compatibiliteit
- **Keyboard navigation**: Volledig toetsenbordtoegankelijk
- **Kleurcontrast**: Minimum 4.5:1

### Performance

- **Core Web Vitals**: LCP, INP, CLS
- **LCP**: < 2.5s
- **INP**: < 200ms
- **CLS**: < 0.1
- **Lighthouse**: Score > 90

## Security Richtlijnen

### OWASP Top 10

1. **Broken Access Control**
2. **Cryptographic Failures**
3. **Injection**
4. **Insecure Design**
5. **Security Misconfiguration**
6. **Vulnerable Components**
7. **Authentication Failures**
8. **Data Integrity Failures**
9. **Logging Failures**
10. **Server-Side Request Forgery**

### BIO2 Security

- **Domein 1**: Informatiebeveiligingsbeleid
- **Domein 2**: Toegangsbeheer
- **Domein 3**: Cryptografie
- **Domein 4**: Fysieke beveiliging
- **Domein 5**: Incidentmanagement
- **Domein 6**: Business continuity
- **Domein 7**: Persoonsgegevens
- **Domein 8**: Logboek Dataverwerkingen

### NCSC Richtlijnen

- **TLS**: NCSC richtlijnen voor TLS 1.3
- **Webapplicaties**: NCSC richtlijnen voor webapplicaties
- **Basisprincipes**: NCSC basisprincipes voor cybersecurity
- **Supply chain**: Leveranciersbeoordeling

## Data Richtlijnen

### DCAT-AP-NL

- **Dataset**: Metadata voor datasets
- **Catalogus**: Metadata voor catalogi
- **Distributie**: Toegangsgegevens
- **Publisher**: Verantwoordelijke organisatie
- **Licentie**: Gebruiksrechten

### FAIR Principes

- **Findable**: Vindbaar via identifiers
- **Accessible**: Toegankelijk via protocollen
- **Interoperable**: Interoperabele formaten
- **Reusable**: Herbruikbaar via licenties

### Open Data

- **5 sterrenmodel**: Open data ladder
- **CC-BY / CC-0**: Aanbevolen licenties
- **data.overheid.nl**: Publicatieplatform
- **High Value Datasets**: EU verplichting

## Infrastructuur Richtlijnen

### Cloud

- **Rijkscloudbeleid**: Beleid voor cloud-gebruik
- **Haven**: Gedeelde cloud-diensten
- **Exit-strategie**: Uitstap-mogelijkheid
- **SaaS-beoordeling**: Beoordeling van SaaS-diensten
- **BIO2 cloud**: Cloud-specifieke beveiligingsmaatregelen

### Containerisatie

- **Docker**: Containerisatie
- **Kubernetes**: Orchestratie
- **Helm**: Package management
- **GitOps**: Deployment-strategie

### CI/CD

- **GitHub Actions**: CI/CD platform
- **GitLab CI**: Alternatief
- **Automated testing**: Unit, integration, E2E
- **Security scanning**: SAST, DAST, SCA

## Open Source Richtlijnen

### Standard for Public Code

- **Code of Conduct**: Gedragscode
- **CONTRIBUTING**: Bijdragerichtlijnen
- **Publiccode.yml**: Metadata
- **REUSE**: Licentie-informatie
- **EUPL-1.2**: Aanbevolen licentie

### Open Source by Default

- **Wettelijke plicht**: Open source bij voorkeur
- **Documentatie**: Publieke documentatie
- **Community**: Open community
- **Hergebruik**: Anderen kunnen hergebruiken

## Gerelateerde skills

- [zgw-apis](../zgw-apis/SKILL.md) — ZGW API-standaarden
- [digikoppeling](../digikoppeling/SKILL.md) — Digikoppeling
- [nl-design-system](../nl-design-system/SKILL.md) — Design system
- [digitoegankelijk](../digitoegankelijk/SKILL.md) — Toegankelijkheid
- [bio-security-baseline](../bio-security-baseline/SKILL.md) — Beveiliging
- [llm-security](../llm-security/SKILL.md) — LLM security
- [open-data](../open-data/SKILL.md) — Open data
- [publieke-code](../publieke-code/SKILL.md) — Open source
- [cloud-overheid](../cloud-overheid/SKILL.md) — Cloud

## Bronnen

- developer.overheid.nl: developer.overheid.nl
- API Design Rules: developer.overheid.nl/api
- NL Design System: nldesignsystem.nl
- NCSC: ncsc.nl
- OWASP: owasp.org
- Standard for Public Code: publiccode.net
