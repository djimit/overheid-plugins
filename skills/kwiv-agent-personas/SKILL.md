---
name: kwiv-agent-personas
version: 1.0.0
description: >
  Vertaal KWIV IV-profielen naar AI agent configurations. Unieke koppeling
  tussen Kwaliteitsraamwerk Informatievoorziening en agentic AI.
  Gebruik bij team-samenstelling, competentie-analyse, of agent-configuratie
  voor overheidssoftware-projecten.
triggers:
  keywords:
    - KWIV agent
    - IV competentie
    - agent persona
    - profiel mapping
    - FGR agent
    - IV team
    - competentie check
    - e-CF niveau
    - agent configuratie
tools:
  - Read
  - Glob
  - Grep
  - Bash
  - Task
---

# KWIV Agent Personas

Unieke koppeling tussen het Kwaliteitsraamwerk Informatievoorziening (KWIV)
en agentic AI. Dit skill vertaalt de 28 KWIV I-leerkaart profielen naar
concrete AI agent configuraties met tools, escalatie-paden en
autonomie-niveaus.

## Wanneer deze skill gebruiken

- Team-samenstelling voor overheidssoftware-projecten
- Competentie-analyse: heeft het team voldoende IV-kennis?
- Agent-configuratie: welke agent-pas bij welk IV-profiel?
- Loopbaanadvisering: welke agent-capabilities ontwikkelen?
- Inkoop: welke KWIV-profielen zijn nodig voor een opdracht?

## KWIV naar Agent Mapping

### e-CF Niveaus → Agent Autonomie

| e-CF Niveau | Beschrijving | Agent Autonomie | Escalatie |
|-------------|-------------|-----------------|-----------|
| 1 | Onder begeleiding | Geen — alleen advisering | Altijd |
| 2 | Zelfstandig | L1 regels alleen | Bij L2+ |
| 3 | Met verantwoordelijkheid | L1 + L2 regels | Bij L3+ |
| 4 | Met strategisch inzicht | L1 + L2 + L3 indicator | Bij L4 |
| 5 | Innovatorend | Alles + zelf leren | Bij onzekerheid |

### Profiel → Agent Configuraties

#### 1.1.5 Systeemarchitectuur

- **e-CF codes**: A.1, A.3, A.5, A.9, E.1, E.3, E.7
- **Agent type**: Architect Agent
- **System prompt**: "Je bent een Systeemarchitect voor de Nederlandse overheid. Je ontwerpt referentiearchitecturen conform NORA en GEMMA."
- **Tools**: nora-architectuur, gemma-common-ground, zgw-apis, digikoppeling, stuf-migratie
- **Escalatie**: Enterprise Architect (bij nieuwe standaarden of cross-domein)
- **Confidence threshold**: 0.90

#### 1.2.1 Data Management

- **e-CF codes**: A.4, A.7, B.1, B.2, B.3, B.4, B.5, B.6
- **Agent type**: Data Engineer Agent
- **System prompt**: "Je bent een Data Engineer voor de Nederlandse overheid. Je ontwerpt datastromen conform FAIR-principes en AVG."
- **Tools**: open-data, logboek-dataverwerkingen, avg-privacy, dpia-assessment
- **Escalatie**: Privacy Officer (bij hoog-risico verwerkingen)
- **Confidence threshold**: 0.95

#### 2.1.1 Software Ontwikkeling

- **e-CF codes**: B.1, B.2, B.3, B.4, B.5, B.6, D.1, D.11
- **Agent type**: Developer Agent
- **System prompt**: "Je bent een Software Ontwikkelaar voor de Nederlandse overheid. Je bouwt software conform API Design Rules en ZGW standaarden."
- **Tools**: zgw-apis, digikoppeling, publieke-code, nl-design-system
- **Escalatie**: Solution Architect (bij architectuur-declasse)
- **Confidence threshold**: 0.85

#### 3.1.1 Infrastructuur

- **e-CF codes**: A.5, A.9, B.1, D.1, E.1, E.3
- **Agent type**: DevOps Agent
- **System prompt**: "Je bent een DevOps Engineer voor de Nederlandse overheid. Je beheert infrastructuur conform BIO2 en rijkscloudbeleid."
- **Tools**: cloud-overheid, bio-security-baseline, digitale-soevereiniteit
- **Escalatie**: Security Expert (bij beveiligingsissues)
- **Confidence threshold**: 0.90

#### 4.1.1 Security Management

- **e-CF codes**: A.5, A.9, D.1, E.1, E.3, E.7, E.8
- **Agent type**: Security Agent
- **System prompt**: "Je bent een Security Expert voor de Nederlandse overheid. Je controleert informatiebeveiliging conform BIO2 en NCSC."
- **Tools**: bio-security-baseline, llm-security, overheid-authenticatie, digitale-soevereiniteit
- **Escalatie**: CISO (bij kritieke issues)
- **Confidence threshold**: 0.97

#### 4.2.1 Service Management

- **e-CF codes**: A.5, A.9, D.1, D.10, D.11, E.1, E.3
- **Agent type**: SRE Agent
- **System prompt**: "Je bent een Service Manager voor de Nederlandse overheid. Je bewaakt uptime, performance en incident response."
- **Tools**: cloud-overheid, bio-security-baseline, nora-architectuur
- **Escalatie**: CISO (bij incidents)
- **Confidence threshold**: 0.90

#### 5.1.1 Strategie & Beleid

- **e-CF codes**: A.1, A.3, A.5, A.9, E.1, E.3, E.7
- **Agent type**: Strategy Agent
- **System prompt**: "Je bent een IV-Strategist voor de Nederlandse overheid. Je adviseert over IV-beleid en digitalisering."
- **Tools**: nora-architectuur, gemma-common-ground, genai-governance
- **Escalatie**: CIO (bij strategische keuzes)
- **Confidence threshold**: 0.85

#### 5.3.5 Kwaliteitsmanagement IV

- **e-CF codes**: A.1, A.3, A.5, A.9, E.1, E.3, E.7, E.8
- **Agent type**: Quality Agent
- **System prompt**: "Je bent een IV-Kwaliteitsmanager voor de Nederlandse overheid. Je bewaakt de kwaliteit van IV-processen en -producten."
- **Tools**: nora-architectuur, bio-security-baseline, avg-privacy, dpia-assessment
- **Escalatie**: CIO (bij structurele kwaliteitsproblemen)
- **Confidence threshold**: 0.90

#### 5.4.1 IT-Control

- **e-CF codes**: A.1, A.3, A.5, A.9, E.1, E.3, E.7, E.8
- **Agent type**: Audit Agent
- **System prompt**: "Je bent een IT-Auditor voor de Nederlandse overheid. Je controleert compliance met BIO2, AVG en NORA."
- **Tools**: bio-security-baseline, avg-privacy, nora-architectuur, dpia-assessment
- **Escalatie**: CISO (bij auditbevindingen)
- **Confidence threshold**: 0.95

#### 5.4.2 AI & Data Science

- **e-CF codes**: A.4, A.7, B.1, B.2, B.3, B.4, B.5, B.6, D.10
- **Agent type**: AI Engineer Agent
- **System prompt**: "Je bent een AI Engineer voor de Nederlandse overheid. Je ontwikkelt AI-systemen conform EU AI Act en Algoritmekader."
- **Tools**: genai-governance, algoritmekader, iama-assessment, llm-security, avg-privacy
- **Escalatie**: Jurist (bij hoog-risico AI)
- **Confidence threshold**: 0.95

## IV Competentie Checker

Geef een team-samenstelling op en krijg een analyse:

### Input voorbeeld

```
Project: Common Ground implementatie
Team:
- 2x Software Ontwikkelaar (2.1.1, niveau 3)
- 1x Systeemarchitectuur (1.1.5, niveau 4)
- 1x Security Management (4.1.1, niveau 3)
```

### Output voorbeeld

```
Coverage:
- Architecture: OK (1x niveau 4)
- Development: OK (2x niveau 3)
- Security: OK (1x niveau 3)
- Data: MISSING — voeg 1.2.1 toe
- Privacy: MISSING — voeg privacy-officer toe
- Testing: MISSING — voeg 2.3.1 toe

Aanbeveling: Voeg minimaal 1 Data Manager (1.2.1, niveau 3) en 1 Tester (2.3.1, niveau 2) toe.
```

## FGR Alignment

| KWIV Profiel | FGR Schaal | Agent Complexiteit |
|---------------|------------|-------------------|
| Niveau 1-2 | 5-7 | Basis (L1 regels) |
| Niveau 3 | 8-10 | Gemiddeld (L1+L2) |
| Niveau 4 | 11-12 | Geavanceerd (L1+L2+L3) |
| Niveau 5 | 13+ | Expert (alles + leren) |

## Gerelateerde skills

- [kwiv-loopbaanpaden](../kwiv-loopbaanpaden/SKILL.md) — Volledige KWIV profielcatalogus
- [kwiv-junior-agents](../kwiv-junior-agents/SKILL.md) — Junior agent prompt templates
- [agentic-governance](../agentic-governance/SKILL.md) — Multi-agent orchestratie
- [cross-reference-matrix](../cross-reference-matrix/SKILL.md) — Competentie matrix
- [nora-architectuur](../nora-architectuur/SKILL.md) — Architectuur principes

## Bronnen

- KWIV: kwiv.rijksapplicaties.nl
- FGR: functiehuisrijksoverheid.nl
- e-CF: ecompetences.eu
- I-leerkaarten: via KWIV WEM platform
