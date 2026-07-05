# AGENTS.md — Overheid Plugins

## Purpose

Dit is de centrale catalogus van Claude Code plugins voor de Nederlandse overheid.
Het doel: **agentic government development** — het bouwen van overheidssoftware met
AI agents die compliance, architectuur en wet- en regelgeving als first-class citizens behandelen.

## Instruction Layers

Bij conflict:
1. Deze `AGENTS.md`
2. Project `AGENTS.md` / `CLAUDE.md`
3. Tool defaults

## Agentic Government Framework

### Principes

1. **Compliance als Code** — Elke overheidsregel is machine-leesbaar, testbaar en auditeerbaar
2. **NORA als Meta-Laag** — Alle skills koppelen aan NORA principes
3. **KWIV als IV-Fundament** — IV-competenties vertaalt naar agent capabilities
4. **Multi-Agent Orchestratie** — Complexe overheidsprocessen = keten van gespecialiseerde agents
5. **Cross-Government Dekking** — Rijk, provincie, gemeente, waterschappen, uitvoeringsorganisaties
6. **EU-Interoperabiliteit** — EIF mapping, EUDI Wallet, Once-Only Principle
7. **Open Standaarden** — JREM, ZGW API's, Digikoppeling, DCAT-AP-NL

### Agent Persona's (gebaseerd op KWIV/FGR)

| Rol | KWIV Profiel | Primaire Skills | Escalatie |
|-----|-------------|-----------------|-----------|
| Compliance Officer | 5.3.5 Kwaliteitsmanagement IV | nora-architectuur, avg-privacy, bio-security-baseline | Jurist |
| Solution Architect | 1.1.5 Systeemarchitectuur | nora-architectuur, gemma-common-ground, zgw-apis | Enterprise Architect |
| Security Expert | 4.1.1 Security Management | bio-security-baseline, llm-security, overheid-authenticatie | CISO |
| Data Engineer | 1.2.1 Data Management | open-data, logboek-dataverwerkingen, avg-privacy | Privacy Officer |
| AI Engineer | 5.4.2 AI & Data Science | genai-governance, algoritmekader, llm-security | Jurist |
| Jurist | N/A | algoritmekader, dpia-assessment, iama-assessment | Hoger beroep |
| Griffier | N/A | kwiv-loopbaanpaden, zgw-apis | Sectorvoorzitter |
| Developer | 2.1.1 Software Ontwikkeling | zgw-apis, digikoppeling, publieke-code | Solution Architect |
| DevOps Engineer | 3.1.1 Infrastructuur | cloud-overheid, bio-security-baseline | Security Expert |
| Privacy Officer | N/A | avg-privacy, dpia-assessment, logboek-dataverwerkingen | Autoriteit Persoonsgegevens |

### Multi-Agent Workflow Patroon

```
Intake Agent → Regelcheck Agent → Compliance Agent → Jurist-Acceptatie → Publicatie Agent → Monitoring Agent
```

Elke agent gebruikt de relevante skills als toolset. Escalatie naar mens bij L3+ (discretionair).

### Rule Maturity Model

| Level | Omschrijving | Agent Gedrag |
|-------|-------------|--------------|
| L1 | Deterministisch, geen uitzonderingen | Automatisch uitvoeren |
| L2 | Deterministisch met bekende uitzonderingen | Uitzonderingen flaggen voor review |
| L3 | Deterministisch hoofdregel + discretionaire uitzonderingen | Indicator + escalatie naar mens |
| L4 | Volledig discretionair | NIET automatiseren, alleen adviseren |

## Skill Quality Gates

Elke SKILL.md moet voldoen aan:
- [ ] Geldig YAML frontmatter (name, description, version)
- [ ] Minimaal 5 trigger-keywords
- [ ] "Gerelateerde skills" sectie met minimaal 2 cross-references
- [ ] NORA principe mapping
- [ ] Wettelijke bronverwijzing (wetten.overheid.nl of EUR-Lex)
- [ ] Test scenario (happy path + edge case)
- [ ] Jurist-acceptatie bij juridische skills (volgens Gate 14)

## Cross-Reference Matrix

Alle skills zijn verbonden via:
- **NORA principes** (meta-laag)
- **BIO2 maatregelen** (beveiliging)
- **e-CF competenties** (IV-professionalisering)
- **Wettelijke bronnen** (primair recht)

Zie `skills/cross-reference-matrix/SKILL.md` voor de volledige matrix.

## Government Levels

| Level | Organisaties | Relevante Skills |
|-------|-------------|------------------|
| Rijk | 10 ministeries + agentschappen | nora-architectuur, bio-security-baseline, avg-privacy, etc. |
| Provincie | 12 provincies | gemeentelijke-iv, dso-omgevingswet, geo-ruimtelijke-iv |
| Gemeente | 342+ gemeenten | gemeentelijke-iv, zgw-apis, digikoppeling |
| Waterschap | 21 waterschappen | dso-omgevingswet, geo-ruimtelijke-iv |
| Uitvoeringsorgaan | UWV, Belasting, IND, SVB | uitvoeringsorganisaties |
| EU | Europese instellingen | eu-interoperability |

## Security Baseline

- Lees NOOIT `auth.json`, `.env` bestanden, of private keys
- Print NOOIT API keys, tokens, of credentials
- Gebruik `trash` boven `rm`
- Geen `git push` zonder expliciete toestemming
- Geen productie-muterende acties zonder approval

## Change Control

Gebruik OpenSpec voor materiële wijzigingen:
- Proposals in `~/openspec/changes/`
- Specs in `~/openspec/specs/`
- Critical/High: expliciete user approval
- Medium: auto-approved als OpenSpec change bestaat
