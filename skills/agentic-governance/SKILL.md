---
name: agentic-governance
version: 1.0.0
description: >
  Multi-agent orchestration voor overheidsprocessen. Configureer, chain en
  escalate AI agents voor compliance, architectuur en juridische acceptatie.
  Gebruik bij agentic government development, multi-agent workflows,
  compliance-automatisering, of human-in-the-loop governance.
triggers:
  keywords:
    - agentic government
    - multi-agent
    - orchestration
    - agent chaining
    - compliance automation
    - workflow orchestration
    - agent persona
    - escalation pattern
    - human-in-the-loop
    - rule maturity model
    - multi-agent workflow
tools:
  - Read
  - Glob
  - Grep
  - Bash
  - Task
---

# Agentic Government Governance

Multi-agent orchestration voor overheidsprocessen. Dit is het hart van het
agentic government framework: het ontwerpen van agent-ketens die complexe
overheidsautomatisering afhandelen met menselijke escalatie op de juiste momenten.

## Wanneer deze skill gebruiken

- Compliance-checks over meerdere domeinen tegelijk
- Architectuur-review met gespecialiseerde agents
- Juridische acceptatie-workflows (human-in-the-loop)
- Publicatie-workflows met PII-check
- Wijzigingsmanagement (wetwijziging → impact → implementatie)
- Cross-samenwerking tussen overheidsorganisaties

## Multi-Agent Workflow Patronen

### 1. Sequential Compliance Pipeline

```
Intake Agent → Regelcheck Agent → Compliance Agent → Jurist-Acceptatie → Publicatie Agent → Monitoring Agent
```

Elke agent voert zijn deel uit en geeft output door naar de volgende.
Escalatie naar mens bij confidence < threshold.

### 2. Parallel Fan-Out

```
            ┌─ Security Agent ─ BIO2 check
            │
Intake ─────┼─ Privacy Agent ── AVG/DPIA check
            │
            ├─ Architect Agent ─ NORA compliance
            │
            └─ AI Governance Agent ─ AI Act check
```

Alle agents draaien parallel. Resultaten worden geconsolideerd door een
synthesis agent.

### 3. Human-in-the-Loop Gates

```
Agent output → Confidence check → [≥95%] → Automatisch verder
                            → [<95%] → Mens review → Accept/Reject/Modify
```

### 4. Event-Driven Reactive

```
Wetwijziging (RSS Staatscourant)
  → Impact Agent (welke regels raken dit?)
  → Update Agent (welke JREM regels wijzigen?)
  → Test Agent (zijn alle tests nog groen?)
  → Jurist Review (is de wijziging correct?)
  → Deploy Agent (nieuwe versie productie)
```

## Rule Maturity Model → Agent Gedrag

| Level | Omschrijving | Agent Gedrag | Escalatie |
|-------|-------------|--------------|-----------|
| L1 | Deterministisch, geen uitzonderingen | Automatisch uitvoeren | Bij exception |
| L2 | Deterministisch met bekende uitzonderingen | Uitzonderingen flaggen | Bij uitzondering match |
| L3 | Hoofdregel + discretionaire uitzonderingen | Indicator + altijd escalatie | Altijd naar mens |
| L4 | Volledig discretionair | NIET automatiseren | Alleen adviseren |

## Agent Configuraties

Zie de agentic-government-starter-kit skill voor complete YAML configuraties
voor: Compliance Agent, Architect Agent, Security Agent, Privacy Agent,
AI Governance Agent, en Publicatie Agent.

## Orchestratie Implementatie

### Stap 1: Definieer het workflow

Bepaal welke agents nodig zijn, hun volgorde, en escalatie-paden.

### Stap 2: Configureer agents

Gebruik de agent-configuratie YAML als template. Pas:
- `primary_skills` aan voor het domein
- `confidence_threshold` aan voor de risicoclassificatie
- `escalation_target` aan voor de organisatie

### Stap 3: Definieer handoff protocols

Tussen elke agent: welke output wordt doorgegeven? Wat zijn acceptatiecriteria?

### Stap 4: Test met scenarios

- Happy path (L1 regels, geen escalatie)
- Edge case (L2 regels, escalatie bij uitzondering)
- Worst case (L3 regels, altijd escalatie)

### Stap 5: Monitor en improve

- Regel match rate per agent
- Escalatie rate (te hoog = agent te zwak, te laag = agent te sterk)
- Jurist acceptatie rate

## Integratie met JuraRegel Rule Services

Elke agent kan aan de slag met Rule APIs:

| Agent | Rule API | Endpoint |
|-------|----------|----------|
| Compliance Agent | BIO2 Service | `POST /v1/bio2/check-maatregel` |
| Architect Agent | NORA Service | `POST /v1/nora/check-principe` |
| Security Agent | BIO2 Service | `POST /v1/bio2/compliance-rapport` |
| Privacy Agent | AVG Service | `POST /v1/avg/check-verwerking` |
| AI Governance Agent | AI Act Service | `POST /v1/ai-act/classificeer` |
| Publicatie Agent | Publicatie Service | `POST /v1/publicatie/check-pii` |

## Integratie met Djimitflo

Gebruik Djimitflo's LROP database voor:
- **Goal tracking**: Elke agent-actie is een goal
- **Learning cycles**: Feedback van juristen wordt opgeslagen
- **Self-improvement**: Agent configuraties worden geoptimaliseerd op basis van fouten
- **Judge service**: Agent output wordt gescoord op kwaliteit

## Integratie met OpenMythos

Gebruik OpenMythos evolution loop:
- Genereer test scenarios voor agent workflows
- Meet agent kwaliteit (discrimination, calibration)
- Evolveer agent prompts op basis van judge feedback
- Promote alleen bij verbeterde metrics

## Gerelateerde skills

- [nora-architectuur](../nora-architectuur/SKILL.md) — Architectuur compliance
- [avg-privacy](../avg-privacy/SKILL.md) — Privacy
- [genai-governance](../genai-governance/SKILL.md) — AI governance
- [algoritmekader](../algoritmekader/SKILL.md) — Algoritme compliance
- [kwiv-agent-personas](../kwiv-agent-personas/SKILL.md) — Agent persona's
- [cross-reference-matrix](../cross-reference-matrix/SKILL.md) — Volledige matrix
- [agentic-government-starter-kit](../agentic-government-starter-kit/SKILL.md) — Snel starten

## Bronnen

- EU AI Act — Verordening (EU) 2024/1689
- NORA — noraonline.nl
- BIO2 — MinBZK Baseline Informatiebeveiliging Overheid
- Algoritmekader — algoritmekader.overheid.nl
- OpenMythos — ~/OpenMythos/analysis/legal-ruleops-platform/
- Djimitflo — ~/djimitflo/.data/djimitflo.sqlite
