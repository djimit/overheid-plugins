---
name: functiehuis-rijk
version: 1.0.0
description: >
  Functiehuis Rijk (FGR) voor IT-professionals. Functiebeschrijvingen,
  salarisschalen, competenties en loopbaanpaden voor de rijksdienst.
  Gebruik bij team-samenstelling, salaris-advies, of IV-carrièreplanning.
triggers:
  keywords:
    - FGR
    - functiehuis
    - salarischaal
    - functiebeschrijving
    - rijksdienst
    - loopbaan
    - competentie
    - schaal
    - IT-functie
    - rijksoverheid
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# Functiehuis Rijk (FGR)

Het Functiehuis Rijk is het kader voor functiebeschrijvingen en
salarisschalen binnen de Nederlandse rijksdienst. Dit skill biedt
overzichten en richtlijnen voor IT-functies.

## Wanneer deze skill gebruiken

- Team-samenstelling voor overheidssoftware-projecten
- Salaris-advies voor IT-professionals
- Loopbaanplanning voor IV-medewerkers
- Inkoop: welke functies zijn nodig?
- KWIV → FGR mapping

## FGR Schalen

| Schaal | Omschrijving | Maandbruto (2026) |
|--------|-------------|-------------------|
| 5 | Uitvoerend | €2.800 - €3.400 |
| 6 | Uitvoerend (ervaren) | €3.200 - €3.900 |
| 7 | Senior uitvoerend | €3.600 - €4.400 |
| 8 | Specialist | €4.000 - €5.000 |
| 9 | Senior specialist | €4.500 - €5.800 |
| 10 | Expert | €5.200 - €6.800 |
| 11 | Senior expert | €6.000 - €7.800 |
| 12 | Principal | €7.000 - €9.000 |
| 13 | Senior principal | €8.200 - €10.500 |
| 14 | Directie | €9.500 - €12.000 |
| 15 | Senior directie | €11.000 - €14.000 |

## IT-Functies in het FGR

### Informatievoorziening (IV)

| Functie | Schaal | KWIV Profiel |
|---------|--------|-------------|
| Junior IV-er | 5-7 | Niveau 1-2 |
| IV-er | 7-9 | Niveau 2-3 |
| Senior IV-er | 9-11 | Niveau 3-4 |
| IV-Architect | 10-12 | 1.1.5 Systeemarchitectuur |
| IV-Manager | 11-13 | 5.1.1 Strategie & Beleid |
| IV-Directeur | 13-15 | 5.1.1 Strategie & Beleid |

### ICT & Data

| Functie | Schaal | KWIV Profiel |
|---------|--------|-------------|
| Developer | 6-9 | 2.1.1 Software Ontwikkeling |
| Senior Developer | 8-11 | 2.1.1 Software Ontwikkeling |
| Tech Lead | 10-12 | 1.1.5 Systeemarchitectuur |
| Data Engineer | 7-10 | 1.2.1 Data Management |
| Data Scientist | 8-11 | 5.4.2 AI & Data Science |
| AI Engineer | 9-12 | 5.4.2 AI & Data Science |

### Beveiliging

| Functie | Schaal | KWIV Profiel |
|---------|--------|-------------|
| Security Analyst | 7-10 | 4.1.1 Security Management |
| Security Engineer | 9-12 | 4.1.1 Security Management |
| CISO | 13-15 | 4.1.1 Security Management |

### Cloud & Infrastructuur

| Functie | Schaal | KWIV Profiel |
|---------|--------|-------------|
| System Administrator | 6-9 | 3.1.1 Infrastructuur |
| DevOps Engineer | 8-11 | 3.1.1 Infrastructuur |
| Cloud Architect | 10-12 | 1.1.5 Systeemarchitectuur |
| SRE | 9-12 | 4.2.1 Service Management |

## KWIV → FGR Mapping

| KWIV Niveau | FGR Schaal | Agent Autonomie |
|-------------|-----------|-----------------|
| 1 | 5-7 | Geen (alleen advisering) |
| 2 | 7-9 | L1 regels |
| 3 | 9-11 | L1 + L2 regels |
| 4 | 11-13 | L1 + L2 + L3 indicator |
| 5 | 13-15 | Alles + zelf leren |

## Competentie-Profielen

### 1.1.5 Systeemarchitectuur
- **FGR Schaal**: 10-12
- **e-CF**: A.1, A.3, A.5, A.9, E.1, E.3, E.7
- **Verantwoordelijkheid**: Referentiearchitectuur, standaarden, patronen

### 2.1.1 Software Ontwikkeling
- **FGR Schaal**: 6-11
- **e-CF**: B.1, B.2, B.3, B.4, B.5, B.6, D.1, D.11
- **Verantwoordelijkheid**: Ontwikkelen, testen, deployen

### 4.1.1 Security Management
- **FGR Schaal**: 7-15
- **e-CF**: A.5, A.9, D.1, E.1, E.3, E.7, E.8
- **Verantwoordelijkheid**: BIO2, NCSC, incidenten

### 5.4.2 AI & Data Science
- **FGR Schaal**: 8-12
- **e-CF**: A.4, A.7, B.1, B.2, B.3, B.4, B.5, B.6, D.10
- **Verantwoordelijkheid**: AI-systemen, data-analyse, algoritmen

## Loopbaanpaden

### Ontwikkelaar → Architect
```
Junior Dev (schaal 6) → Dev (schaal 8) → Senior Dev (schaal 10)
  → Tech Lead (schaal 11) → Architect (schaal 12)
```

### Security → CISO
```
Security Analyst (schaal 8) → Security Engineer (schaal 10)
  → Senior Security (schaal 12) → CISO (schaal 14)
```

### Data → AI Lead
```
Data Engineer (schaal 8) → Data Scientist (schaal 10)
  → AI Engineer (schaal 11) → AI Lead (schaal 13)
```

## Gerelateerde skills

- [kwiv-loopbaanpaden](../kwiv-loopbaanpaden/SKILL.md) — KWIV loopbaanpaden
- [kwiv-agent-personas](../kwiv-agent-personas/SKILL.md) — KWIV → agent mapping
- [kwiv-junior-agents](../kwiv-junior-agents/SKILL.md) — Junior agent templates
- [nora-architectuur](../nora-architectuur/SKILL.md) — Architectuur
- [bio-security-baseline](../bio-security-baseline/SKILL.md) — Beveiliging
- [agentic-governance](../agentic-governance/SKILL.md) — Orchestratie

## Bronnen

- FGR: functiehuisrijksoverheid.nl
- KWIV: kwiv.rijksapplicaties.nl
- e-CF: ecompetences.eu
- Salarisschalen: rijksoverheid.nl/rijkspersoneel
