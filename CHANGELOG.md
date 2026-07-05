# Changelog

Alle noemenswaardige wijzigingen aan deze marketplace worden hier gedocumenteerd.

Het formaat is gebaseerd op [Keep a Changelog](https://keepachangelog.com/nl/1.1.0/)
en dit project volgt [Semantic Versioning](https://semver.org/lang/nl/).

## [Unreleased]

### Toegevoegd

- **Agentic Government Framework** — Multi-agent orchestration voor overheidsprocessen
- **10 nieuwe skills** (totaal: 34 skills):
  - agentic-governance: Multi-agent orchestration, workflow patronen, Rule Maturity Model, agent configuraties
  - kwiv-agent-personas: KWIV-profielen → AI agent configuraties (unieke differentiatie, 28 profielen)
- **8 extra skills** (totaal: 42 skills):
  - ai-governance: EU AI Act compliance, FRIA, risicoclassificatie, conformiteitsbeoordeling
  - common-ground: Open Zaak, Open Formulieren, Open Notificaties implementatie
  - nis2-compliance: NIS2/Cyberbeveiligingswet, incidentrapportage, risicomanagement
  - juraregel-integratie: JuraRegel Rule Service integratie, JREM, Rule Extraction Sprint
  - functiehuis-rijk: FGR salarisschalen, functiebeschrijvingen, IT-carrièrepaden
  - provincies: IV voor 12 provincies (omgevingsvisie, wegen, MER, waterbeheer)
  - waterschappen: IV voor 21 waterschappen (waterkeringen, kwaliteit, overlast)
  - developer-overheid: developer.overheid.nl richtlijnen (API, frontend, security, data)
- **Sprint 2** (totaal: 54 skills):
  - fsc: Federated Service Connect, PKIoverheid, mTLS, Digikoppeling migratie
  - haven: Rijkscloud Haven platform, Cloud Service Broker, exit-strategie
  - privacy-cookies: AVG privacybeleid, ePrivacy cookiebeleid, consent
  - veilig-bouwen: OWASP Top 10, SAST/DAST/SCA, supply chain, CVD
  - algoritmeregister-aangifte: Algoritmeregister procedure, Woo Art. 2.1
  - eu-engels: 10 Engelstalige kernskills voor EU-adoptie
  - Reusable GitHub Actions workflow voor skill validatie
  - Issue templates (skill-voorstel, bug-report) en CODE_OF_CONDUCT
  - cross-reference-matrix: Volledige NORA/BIO2/e-CF/wetten mapping van alle skills
  - agentic-government-starter-kit: Templates, scaffolds, CI/CD pipelines, monitoring setup
  - gemeentelijke-iv: IV voor 342+ gemeenten (burgerzaken, OZB, APV, Wmo, archivering, ruimtelijke ordening)
  - uitvoeringsorganisaties: UWV, Belastingdienst, IND, SVB, DJI (algoritme-compliance op schaal)
  - geo-ruimtelijke-iv: BAG, BRK, IMGeo, 3D Basisvoorziening, INSPIRE, OGC API
  - eu-interoperability: EIF, EUDI Wallet, Once-Only Principle, cross-border dienstverlening
- AGENTS.md met volledig agentic government framework
- CI workflow voor automatische plugin versie-checks (dagelijks, maakt PR bij versie-drift)
- Versie-vergelijking met normalisatie (v-prefix, trailing .0)
- Tests voor check-versions script
- **23 nieuwe skills** voor het bouwen van overheidssoftware (totaal: 24 skills)
  - algoritmekader: AI Act risicoklassen, Algoritmekader, Algoritmeregister, generatieve AI
  - avg-privacy: AVG/GDPR, Privacy by Design/Default, verwerkingsregister, rechten betrokkenen
  - cloud-overheid: rijkscloudbeleid, BIO cloud controls, SaaS-beoordeling, Haven, exit-strategie
  - digikoppeling: Digikoppeling REST/WUS/ebMS2 profielen, PKIoverheid, MSH, OIN, Diginetwerk
  - digitale-soevereiniteit: CLOUD Act risicoanalyse, soevereine hosting, BIV-classificatie, on-prem LLM
  - digitoegankelijk: WCAG 2.1/2.2, EN 301 549, EAA, codepatronen, testtools, CI/CD
  - dpia-assessment: volledig DPIA (7 stappen, AP 9-criteria, risicomatrix kans x impact, rapporttemplate)
  - dso-omgevingswet: STOP/TPOD, IMOW, STTR toepasbare regels, LVBB publicatie, DSO API's
  - e-factureren: Peppol, SI-UBL 2.0, EN 16931, volledige factuur-XML, OIN, identifier-schemes
  - gemma-common-ground: GEMMA referentiearchitectuur, Common Ground, Open Zaak/Formulieren, Haven
  - genai-governance: EU AI Act governance (model card, audit trail, HITL, conformiteitsbeoordeling, model registry)
  - iama-assessment: volledig IAMA (3 fasen, 33+ vragen, grondrechtentoets, fairness-metrics, 80%-regel)
  - llm-security: OWASP LLM Top 10 (prompt injection, output sanitization, DLP, PII-filtering, rate limiting)
  - logboek-dataverwerkingen: Logboek Dataverwerkingen API, verwerkingsactiviteiten, AVG-transparantie
  - mdto-archivering: MDTO, Archiefwet 2021, DUTO, e-depot, NEN 2082
  - nl-design-system: NL Design System design tokens, community componenten, Storybook, Rijkshuisstijl
  - nora-architectuur: NORA-principes, BIO informatiebeveiliging, GDI, verplichte open standaarden
  - open-data: DCAT-AP-NL 2.0, data.overheid.nl, high-value datasets, FAIR-principes
  - overheid-authenticatie: DigiD, eHerkenning, eIDAS 2.0, SAML/OIDC, BSN-verwerking
  - publieke-code: Standard for Public Code, publiccode.yml, REUSE-compliance, EUPL-1.2
  - sociaal-domein: iWmo/iJw/iEb berichtenstandaarden, Suwinet, ketenintegratie
  - stuf-migratie: StUF-BG/ZKN naar ZGW API's, vertaallaag, veldmapping, coexistentiepatronen
  - tooi-metadata: TOOI thesauri, Woo publicatie, KOOP, overheids-URI's
- Onderlinge cross-references tussen gerelateerde skills
- README bijgewerkt met volledig skills-overzicht per domein

## [1.1.0] - 2026-02-22

### Toegevoegd

- Plugin: bio-security-baseline v0.2.0 (1 skill voor BIO2 informatiebeveiliging)
  - BIO2-overheidsmaatregelen over 13 domeinen (governance, toegangsbeheer, logging, cryptografie, etc.)
  - Implementatie-checklist voor ontwikkelaars
  - Forum Standaardisatie verplichte standaarden (HTTPS/HSTS, TLS, DNSSEC, DMARC, DKIM, SPF, etc.)
  - NCSC-richtlijnen (TLS 2025-05, webapplicaties, basisprincipes)
  - Cyberbeveiligingswet (NIS2-implementatie)
  - EU-regelgeving: Cyber Resilience Act, AI Act, Data Act, eIDAS 2.0
  - DigiToegankelijk (WCAG), authenticatie- en API-standaarden
  - Audit en compliance (ENSIA, DigiD Normenkader, internet.nl)
  - Codevoorbeelden (logging, security headers, security.txt)

## [1.0.0] - 2026-02-16

### Toegevoegd

- Marketplace opgezet als centrale catalogus voor overheids-Claude Code plugins
- Plugin: logius-standaarden v1.0.0 (10 skills voor 88 Logius standaarden repositories)
- Plugin: zad-actions v1.0.0 (3 skills voor ZAD deployment)
- Documentatie: plugin-maken.md handleiding
- Documentatie: plugin-toevoegen.md handleiding
- CI workflow voor validatie van marketplace.json
- Issue template voor plugin-aanmeldingen
- PR template

[Unreleased]: https://github.com/MinBZK/overheid-claude-plugins/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/MinBZK/overheid-claude-plugins/releases/tag/v1.0.0
