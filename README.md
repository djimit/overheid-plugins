# Overheid Claude Plugins

[![EUPL-1.2](https://img.shields.io/badge/licentie-EUPL--1.2-blue.svg)](LICENSE)
[![skills](https://img.shields.io/badge/skills-24-green.svg)](#skills-in-deze-plugin)
[![plugins](https://img.shields.io/badge/marketplace_plugins-7-blue.svg)](#marketplace-plugins)
[![CI](https://github.com/djimit/overheid-claude-plugins/actions/workflows/validate.yml/badge.svg)](https://github.com/djimit/overheid-claude-plugins/actions/workflows/validate.yml)

Centrale catalogus van [Claude Code](https://docs.anthropic.com/en/docs/claude-code) plugins voor de Nederlandse overheid. Bevat **24 eigen skills** voor het bouwen van overheidssoftware en een marketplace met 7 community-plugins.

## Snel starten

```bash
# 1. Voeg de marketplace toe
claude plugin marketplace add djimit/overheid-claude-plugins

# 2. Installeer een plugin
claude plugin install logius-standaarden@overheid-plugins
```

![Demo: plugin installeren en browsen](docs/demo.gif)

## Skills in deze plugin

24 skills voor het bouwen van overheidssoftware, gegroepeerd per domein:

### Architectuur & standaarden

| Skill | Beschrijving |
|-------|-------------|
| [nora-architectuur](skills/nora-architectuur/) | NORA-principes, BIO informatiebeveiliging, GDI, verplichte open standaarden |
| [gemma-common-ground](skills/gemma-common-ground/) | GEMMA referentiearchitectuur, Common Ground, Open Zaak/Formulieren, Haven |
| [zgw-apis](skills/zgw-apis/) | ZGW API-standaarden (Zaken, Documenten, Catalogi), Haal Centraal, paginering |
| [digikoppeling](skills/digikoppeling/) | Digikoppeling REST/WUS/ebMS2, PKIoverheid, MSH, OIN, Diginetwerk |
| [stuf-migratie](skills/stuf-migratie/) | StUF-BG/ZKN migratie naar ZGW API's, vertaallaag, coexistentiepatronen |

### Wet- en regelgeving

| Skill | Beschrijving |
|-------|-------------|
| [avg-privacy](skills/avg-privacy/) | AVG/GDPR, Privacy by Design/Default, verwerkingsregister, rechten betrokkenen |
| [dpia-assessment](skills/dpia-assessment/) | Volledig DPIA (7 stappen, AP 9-criteria, risicomatrix, rapporttemplate) |
| [algoritmekader](skills/algoritmekader/) | AI Act risicoklassen, Algoritmekader, Algoritmeregister, generatieve AI |
| [iama-assessment](skills/iama-assessment/) | Volledig IAMA (3 fasen, 33+ vragen, grondrechtentoets, fairness-metrics) |
| [dso-omgevingswet](skills/dso-omgevingswet/) | STOP/TPOD, IMOW, STTR toepasbare regels, LVBB publicatie, DSO API's |
| [tooi-metadata](skills/tooi-metadata/) | TOOI thesauri, Woo publicatie, KOOP, overheids-URI's |

### Toegankelijkheid & design

| Skill | Beschrijving |
|-------|-------------|
| [digitoegankelijk](skills/digitoegankelijk/) | WCAG 2.1/2.2, EN 301 549, EAA, codepatronen, testtools, CI/CD |
| [nl-design-system](skills/nl-design-system/) | Design tokens, community componenten, Storybook, Rijkshuisstijl |

### AI governance & beveiliging

| Skill | Beschrijving |
|-------|-------------|
| [genai-governance](skills/genai-governance/) | EU AI Act technische governance: model card, audit trail, HITL, conformiteitsbeoordeling |
| [llm-security](skills/llm-security/) | OWASP LLM Top 10: prompt injection, output sanitization, DLP, PII-filtering |
| [digitale-soevereiniteit](skills/digitale-soevereiniteit/) | CLOUD Act, soevereine hosting, BIV-classificatie, data residency, on-prem LLM |

### Cloud & infrastructuur

| Skill | Beschrijving |
|-------|-------------|
| [cloud-overheid](skills/cloud-overheid/) | Rijkscloudbeleid, BIO cloud controls, SaaS-beoordeling, Haven, exit-strategie |

### Authenticatie & beveiliging

| Skill | Beschrijving |
|-------|-------------|
| [overheid-authenticatie](skills/overheid-authenticatie/) | DigiD, eHerkenning, eIDAS 2.0, SAML/OIDC, BSN-verwerking |

### Data & archivering

| Skill | Beschrijving |
|-------|-------------|
| [mdto-archivering](skills/mdto-archivering/) | MDTO, Archiefwet 2021, DUTO, e-depot, NEN 2082 |
| [open-data](skills/open-data/) | DCAT-AP-NL, data.overheid.nl, high-value datasets, FAIR-principes |
| [logboek-dataverwerkingen](skills/logboek-dataverwerkingen/) | Logboek Dataverwerkingen API, verwerkingsactiviteiten, AVG-logging |

### Domeinspecifiek

| Skill | Beschrijving |
|-------|-------------|
| [sociaal-domein](skills/sociaal-domein/) | iWmo/iJw/iEb berichtenstandaarden, Suwinet, ketenintegratie |
| [e-factureren](skills/e-factureren/) | Peppol, SI-UBL 2.0, EN 16931, OIN, e-invoicing |
| [publieke-code](skills/publieke-code/) | Standard for Public Code, publiccode.yml, REUSE, EUPL-1.2, open source overheid |

## Marketplace plugins

| Plugin | Skills | Beschrijving | Maintainer |
|--------|--------|-------------|------------|
| [logius-standaarden](https://github.com/MinBZK/logius-standaarden-plugin) | 10 | Skills voor 77 Logius standaarden repositories: API Design Rules, Digikoppeling, OAuth NL, FSC, CloudEvents, BOMOS, en meer | [MinBZK](https://github.com/MinBZK) |
| [zad-actions](https://github.com/RijksICTGilde/zad-actions) | 5 | Skills voor ZAD deployment: linting, releases, action validatie, workflow generatie en debugging | [Rijks ICT Gilde](https://github.com/RijksICTGilde) |
| [developer-overheid](https://github.com/dstotijn/developer-overheid-nl-agent-skills) | 9 | Kennisbank van developer.overheid.nl: richtlijnen en standaarden voor overheidssoftwareontwikkeling (API's, data, frontend, infra, security, open source) | [David Stotijn](https://github.com/dstotijn) |
| [nerds](https://github.com/MinBZK/NeRDS) | 14 | Skills voor de Nederlandse Richtlijn Digitale Systemen (NeRDS): 13 richtlijnen voor ontwerpen, ontwikkelen en inkopen van digitale systemen (toegankelijkheid, open source, cloud, veiligheid, privacy, en meer) | [MinBZK](https://github.com/MinBZK) |
| [internet-nl](https://github.com/MinBZK/internet-nl-plugin) | 5 | Skills voor internet.nl: test compliance met moderne internetstandaarden voor websites en mailservers (IPv6, DNSSEC, HTTPS, TLS, DMARC, DKIM, SPF, DANE) | [MinBZK](https://github.com/MinBZK) |
| [geonovum](https://github.com/MinBZK/geonovum-plugin) | 6 | Skills voor Geonovum geo-standaarden: OGC API, WMS, WFS, metadata (ISO 19115), informatiemodellen (NEN 3610, MIM), INSPIRE en 3D | [MinBZK](https://github.com/MinBZK) |
| [bio-security-baseline](https://github.com/djimit/overheid-claude-plugins) | 1 | BIO2 security baseline: verplichte beveiligingsmaatregelen, Forum Standaardisatie-standaarden, NCSC-richtlijnen, NIS2/Cyberbeveiligingswet, EU CRA, AI Act en compliance-informatie | [djimit](https://github.com/djimit) |

## Plugin toevoegen

Heb je een Claude Code plugin die relevant is voor de Nederlandse overheid? Voeg hem toe aan deze marketplace:

1. **Plugin bouwen** - Zie [docs/plugin-maken.md](docs/plugin-maken.md) voor een stap-voor-stap handleiding
2. **Plugin aanmelden** - Zie [docs/plugin-toevoegen.md](docs/plugin-toevoegen.md) of open een [issue](../../issues/new?template=plugin-aanmelding.yml)

### Kwaliteitseisen

- Open-source licentie (EUPL-1.2, Apache-2.0, MIT, of vergelijkbaar)
- Publieke GitHub repository
- Geldige `.claude-plugin/plugin.json`
- Minimaal 1 werkende skill, command of agent
- Nederlandse of tweetalige documentatie

Zie [CONTRIBUTING.md](CONTRIBUTING.md) voor het volledige review-proces.

## Structuur

```
.claude-plugin/
  marketplace.json      # Catalogus met marketplace-plugins
skills/
  algoritmekader/       # AI Act, Algoritmekader, Algoritmeregister
  avg-privacy/          # AVG/GDPR, Privacy by Design
  cloud-overheid/       # Rijkscloudbeleid, BIO cloud, Haven
  digikoppeling/        # Digikoppeling REST/WUS/ebMS2, PKIoverheid
  digitale-soevereiniteit/ # CLOUD Act, soevereine hosting, BIV
  digitoegankelijk/     # WCAG, EN 301 549, EAA
  dpia-assessment/      # DPIA (7 stappen, risicomatrix)
  dso-omgevingswet/     # STOP/TPOD, IMOW, STTR, DSO API's
  e-factureren/         # Peppol, SI-UBL 2.0, EN 16931
  gemma-common-ground/  # GEMMA, Common Ground, Open Zaak
  genai-governance/     # EU AI Act governance, audit trail, HITL
  iama-assessment/      # IAMA (3 fasen, grondrechtentoets)
  llm-security/         # OWASP LLM Top 10, prompt injection, DLP
  logboek-dataverwerkingen/ # Logboek Dataverwerkingen API
  mdto-archivering/     # MDTO, Archiefwet, e-depot
  nl-design-system/     # Design tokens, community componenten
  nora-architectuur/    # NORA, BIO, GDI, open standaarden
  open-data/            # DCAT-AP-NL, data.overheid.nl, HVD
  overheid-authenticatie/ # DigiD, eHerkenning, eIDAS
  publieke-code/        # Standard for Public Code, REUSE, EUPL
  sociaal-domein/       # iWmo, iJw, iEb, Suwinet
  stuf-migratie/        # StUF-BG/ZKN naar ZGW migratie
  tooi-metadata/        # TOOI, Woo, KOOP
  zgw-apis/             # ZGW API's, Haal Centraal
docs/
  plugin-maken.md       # Handleiding: plugin bouwen
  plugin-toevoegen.md   # Handleiding: plugin registreren
```

## Licentie

[EUPL-1.2](LICENSE) - European Union Public Licence
