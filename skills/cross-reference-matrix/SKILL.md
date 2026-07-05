---
name: cross-reference-matrix
version: 1.0.0
description: >
  Volledige cross-reference matrix van alle overheid-plugins skills.
  Koppelt skills aan NORA principes, BIO2 maatregelen, e-CF competenties
  en wettelijke bronnen. Gebruik bij architectuur-review, compliance-check,
  of skill-discovery.
triggers:
  keywords:
    - cross-reference
    - matrix
    - skill mapping
    - NORA mapping
    - BIO2 mapping
    - competentie matrix
    - skill discovery
    - dependency graph
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# Cross-Reference Matrix

Volledige mapping van alle skills in de overheid-plugins marketplace.
Dit is het "neuronale netwerk" van het platform — elke skill is verbonden
met andere skills via gedeelde standaarden, wetten en principes.

## Wanneer deze skill gebruiken

- Architectuur-review: welke skills raken dit domein?
- Compliance-check: welke standaarden zijn relevant?
- Skill-discovery: welke skills heb ik nodig voor mijn project?
- Impact-analyse: wat gebeurt er als deze standaard wijzigt?

## NORA Principes → Skills Mapping

| NORA Principe | Skills |
|---------------|--------|
| Dienstverlening is burgergericht | nl-design-system, digitoegankelijk, zgw-apis |
| Hergebruik voor bouwen | gemma-common-ground, zgw-apis, digikoppeling |
| Data bij de bron | zgw-apis, open-data, logboek-dataverwerkingen |
| Informatiebeveiliging | bio-security-baseline, llm-security, overheid-authenticatie |
| Open waar mogelijk | publieke-code, open-data, genai-governance |
| Privacy by Design | avg-privacy, dpia-assessment, logboek-dataverwerkingen |
| Interoperabiliteit | digikoppeling, stuf-migratie, zgw-apis |
| Standaarden volgen | nora-architectuur, bio-security-baseline, zgw-apis |

## BIO2 Maatregelen → Skills Mapping

| BIO2 Domein | Skills |
|-------------|--------|
| Informatiebeveiligingsbeleid | bio-security-baseline, nora-architectuur |
| Toegangsbeheer | bio-security-baseline, overheid-authenticatie |
| Cryptografie | bio-security-baseline, overheid-authenticatie |
| Fysieke beveiliging | bio-security-baseline |
| Incidentmanagement | bio-security-baseline, llm-security |
| Business continuity | bio-security-baseline, cloud-overheid |
| Persoonsgegevens | avg-privacy, dpia-assessment, logboek-dataverwerkingen |
| Logboek Dataverwerkingen | logboek-dataverwerkingen, avg-privacy |

## e-CF Competenties → Skills Mapping

| e-CF Competentie | Skills |
|------------------|--------|
| A.1 IT Strategie & Planning | nora-architectuur, gemma-common-ground |
| A.3 Architectuur | nora-architectuur, gemma-common-ground, zgw-apis |
| A.5 Technologie | bio-security-baseline, cloud-overheid |
| B.1 Ontwikkeling | zgw-apis, digikoppeling, publieke-code |
| B.2 Testen | publieke-code, digitoegankelijk |
| D.7 Regulering | algoritmekader, avg-privacy, dpia-assessment |
| E.1 Innovatie | genai-governance, llm-security |
| E.3 Risicomanagement | bio-security-baseline, dpia-assessment |

## Wettelijke Bronnen → Skills Mapping

| Wet/Regeling | Skills |
|--------------|--------|
| AVG/GDPR | avg-privacy, dpia-assessment, logboek-dataverwerkingen |
| EU AI Act | genai-governance, algoritmekader, iama-assessment |
| Algoritmekader | algoritmekader, iama-assessment |
| Omgevingswet | dso-omgevingswet, geo-ruimtelijke-iv |
| Archiefwet 2021 | mdto-archivering |
| Woo | open-data, tooi-metadata |
| Wmo 2015 | sociaal-domein, gemeentelijke-iv |
| Gemeentewet | gemeentelijke-iv |
| DigiD/eHerkenning | overheid-authenticatie |
| BIO2 | bio-security-baseline |
| NORA | nora-architectuur |
| ZGW API's | zgw-apis |
| Digikoppeling | digikoppeling |
| StUF | stuf-migratie |
| WCAG/EN 301 549 | digitoegankelijk |
| DCAT-AP-NL | open-data |
| Peppol/EN 16931 | e-factureren |
| Standard for Public Code | publieke-code |
| NL Design System | nl-design-system |
| CLOUD Act | digitale-soevereiniteit |
| OWASP LLM Top 10 | llm-security |
| KWIV | kwiv-loopbaanpaden, kwiv-agent-personas, kwiv-junior-agents |
| FGR | kwiv-agent-personas |
| GEMMA | gemma-common-ground |
| Common Ground | gemma-common-ground, gemeentelijke-iv |
| EUIF | eu-interoperability |

## Government Level → Skills Mapping

| Level | Organisaties | Kern-Skills |
|-------|-------------|-------------|
| Rijk | 10 ministeries + agentschappen | nora-architectuur, bio-security-baseline, avg-privacy, genai-governance |
| Provincie | 12 provincies | dso-omgevingswet, geo-ruimtelijke-iv, gemeentelijke-iv |
| Gemeente | 342+ gemeenten | gemeentelijke-iv, zgw-apis, digikoppeling, sociaal-domein |
| Waterschap | 21 waterschappen | dso-omgevingswet, geo-ruimtelijke-iv |
| Uitvoeringsorgaan | UWV, Belasting, IND, SVB | uitvoeringsorganisaties, avg-privacy, bio-security-baseline |
| EU | Europese instellingen | eu-interoperability, genai-governance |

## Agent Persona → Skills Mapping

| Agent Persona | Primaire Skills | Secundaire Skills |
|---------------|-----------------|-------------------|
| Compliance Officer | nora-architectuur, bio-security-baseline | avg-privacy, digitoegankelijk |
| Solution Architect | nora-architectuur, gemma-common-ground | zgw-apis, digikoppeling |
| Security Expert | bio-security-baseline, llm-security | overheid-authenticatie, digitale-soevereiniteit |
| Data Engineer | open-data, logboek-dataverwerkingen | avg-privacy, dpia-assessment |
| AI Engineer | genai-governance, algoritmekader | iama-assessment, llm-security |
| Jurist | algoritmekader, dpia-assessment | iama-assessment, avg-privacy |
| Griffier | kwiv-loopbaanpaden, zgw-apis | tooi-metadata, open-data |
| Developer | zgw-apis, digikoppeling | publieke-code, nl-design-system |
| DevOps | cloud-overheid, bio-security-baseline | digitale-soevereiniteit |
| Privacy Officer | avg-privacy, dpia-assessment | logboek-dataverwerkingen, iama-assessment |

## Gerelateerde skills

Alle skills in deze plugin zijn via deze matrix verbonden.
Zie de individuele SKILL.md bestanden voor detail-informatie.

## Bronnen

- NORA: noraonline.nl
- BIO2: MinBZK Baseline Informatiebeveiliging Overheid
- e-CF: ecompetences.eu
- KWIV: kwiv.rijksapplicaties.nl
- FGR: functiehuisrijksoverheid.nl
- GEMMA: gemmaonline.nl
