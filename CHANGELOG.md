# Changelog

Alle noemenswaardige wijzigingen aan deze marketplace worden hier gedocumenteerd.

Het formaat is gebaseerd op [Keep a Changelog](https://keepachangelog.com/nl/1.1.0/)
en dit project volgt [Semantic Versioning](https://semver.org/lang/nl/).

## [Unreleased]

### Toegevoegd

- CI workflow voor automatische plugin versie-checks (dagelijks, maakt PR bij versie-drift)
- Versie-vergelijking met normalisatie (v-prefix, trailing .0)
- Tests voor check-versions script
- **15 nieuwe skills** voor het bouwen van overheidssoftware (totaal: 16 skills)
  - algoritmekader: AI Act risicoklassen, Algoritmekader, Algoritmeregister, generatieve AI
  - avg-privacy: AVG/GDPR, Privacy by Design/Default, verwerkingsregister, rechten betrokkenen
  - digitoegankelijk: WCAG 2.1/2.2, EN 301 549, EAA, codepatronen, testtools, CI/CD
  - dpia-assessment: volledig DPIA (7 stappen, AP 9-criteria, risicomatrix kans x impact, rapporttemplate)
  - dso-omgevingswet: STOP/TPOD, IMOW, STTR toepasbare regels, LVBB publicatie, DSO API's
  - e-factureren: Peppol, SI-UBL 2.0, EN 16931, volledige factuur-XML, OIN, identifier-schemes
  - gemma-common-ground: GEMMA referentiearchitectuur, Common Ground, Open Zaak/Formulieren, Haven
  - iama-assessment: volledig IAMA (3 fasen, 33+ vragen, grondrechtentoets, fairness-metrics, 80%-regel)
  - mdto-archivering: MDTO, Archiefwet 2021, DUTO, e-depot, NEN 2082
  - nl-design-system: NL Design System design tokens, community componenten, Storybook, Rijkshuisstijl
  - nora-architectuur: NORA-principes, BIO informatiebeveiliging, GDI, verplichte open standaarden
  - open-data: DCAT-AP-NL 2.0, data.overheid.nl, high-value datasets, FAIR-principes
  - overheid-authenticatie: DigiD, eHerkenning, eIDAS 2.0, SAML/OIDC, BSN-verwerking
  - sociaal-domein: iWmo/iJw/iEb berichtenstandaarden, Suwinet, ketenintegratie
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
