---
name: juraregel-integratie
version: 1.0.0
description: >
  JuraRegel Rule Service integratie voor overheidsagents. Koppel
  compliance-agents aan JREM Rule APIs voor auditbare regelchecking.
  Gebruik bij Rule Service implementatie, JREM integratie, of
  Legal RuleOps platform ontwikkeling.
triggers:
  keywords:
    - JuraRegel
    - JREM
    - Rule Service
    - Rule API
    - Legal RuleOps
    - regel checking
    - compliance API
    - auditbare regels
    - rule engine
    - juridische regels
tools:
  - Read
  - Glob
  - Grep
  - Bash
  - Task
---

# JuraRegel Integratie

Integratie met het JuraRegel Legal RuleOps Platform. Dit skill biedt
patronen voor het koppelen van compliance-agents aan JREM Rule APIs
voor auditbare, testbare regelchecking.

## Wanneer deze skill gebruiken

- Rule Service implementatie voor overheidsorganisaties
- JREM (Juridisch Regelaar Exchange Model) integratie
- Compliance-agent koppeling aan Rule APIs
- Regelhardheid classificatie (L1-L4)
- Jurist-acceptatie workflow implementatie
- Rule Extraction Sprint uitvoeren

## JuraRegel Architectuur

```
AUTHORING      ALEF IDE · RegelSpraak CNL · Scenario editor
    ↓
GENERATION     ALEF custom generator → JREM (of handmatige fallback)
    ↓
EXCHANGE       JREM Registry — neutraal contract per domein
    ↓
VALIDATION     CI/CD — 14+ Legal Quality Gates
    ↓
SERVICE        Rule API Mesh — stateless APIs per domein
    ↓
CONSUMPTION    Intake · Zaaksysteem · Financieel · Burgerportaal
    ↓
GOVERNANCE     Rule Registry · Approval workflow · Audit log
```

## Rule API Integratie

### Beschikbare Rule Services

| Domein | API | Poort | Use Cases |
|--------|-----|-------|-----------|
| Griffierecht | `POST /v1/griffierecht/calculate` | 8490 | Civiel, kanton, bestuursrecht |
| Procesreglement | `POST /v1/procesreglement/check` | 8491 | Digitale indiening |
| Classificatie | `POST /v1/classificatie/classify` | 8492 | Zaakclassificatie |
| Publicatie | `POST /v1/publicatie/check-pii` | 8493 | PII-check bij publicatie |
| BIO2 | `POST /v1/bio2/check-maatregel` | 8494 | Compliance checks |
| NORA | `POST /v1/nora/check-principe` | 8495 | Architectuur compliance |
| AI Act | `POST /v1/ai-act/classificeer` | 8496 | AI risicoclassificatie |
| Forum Standaardisatie | `POST /v1/fs/check-standaard` | 8497 | Standaard compliance |

### API Voorbeeld: Griffierecht

```bash
curl -X POST http://localhost:8490/v1/grifferecht/calculate \
  -H "Content-Type: application/json" \
  -d '{
    "zaakstroom": "civiel",
    "vorderingWaarde": 25000,
    "typeProcedure": "procedure"
  }'
```

Response:
```json
{
  "griffierecht": 287,
  "berekening": {
    "staffel": 2,
    "basisbedrag": 176,
    "percentage": 0.0045,
    "vorderingWaarde": 25000
  },
  "juridischeContext": {
    "wet": "Wet griffierechten burgerlijke zaken",
    "wetBwbrId": "BWBR0002534",
    "wetVersieLaatstGecheckt": "2026-06-15",
    "tariefVersie": "2026.1",
    "juristAccordering": {
      "naam": "D. Landman",
      "datum": "2026-06-15",
      "geldigTot": "2027-06-15",
      "versie": "1.0.0"
    }
  },
  "inputHash": "sha256:abc123...",
  "rulesetHash": "sha256:def456..."
}
```

### API Voorbeeld: BIO2

```bash
curl -X POST http://localhost:8494/v1/bio2/check-maatregel \
  -H "Content-Type: application/json" \
  -d '{
    "maatregelId": "8.2.1",
    "evidence": {
      "implemented": true,
      "documentatie": "https://wiki...",
      "laatsteAudit": "2026-05-01"
    }
  }'
```

## Agent Integratie Patroon

### Compliance Agent → Rule Service

```python
class ComplianceAgent:
    def check_bio2(self, maatregel_id: str) -> ComplianceResult:
        response = requests.post(
            "http://localhost:8494/v1/bio2/check-maatregel",
            json={"maatregelId": maatregel_id, "evidence": self.get_evidence()}
        )
        result = response.json()
        if result["compliant"]:
            return ComplianceResult.PASS
        elif result["manualReviewRequired"]:
            return ComplianceResult.ESCALATE
        return ComplianceResult.FAIL

    def check_nora(self, principe: str, oplossing: dict) -> ComplianceResult:
        response = requests.post(
            "http://localhost:8495/v1/nora/check-principe",
            json={"principe": principe, "oplossing": oplossing}
        )
        return self.interpret_result(response.json())
```

## Rule Extraction Sprint

Gestandaardiseerde methode voor migratie van bronnen naar JREM:

| Dag | Activiteit | Output |
|-----|-----------|--------|
| 1 | Bronverzameling | Alle relevante bronnen |
| 2 | Begrippenmodel | begrippen.rspraak |
| 3-4 | Beslistabellen | regels.rspraak |
| 5 | JREM export + tests | JREM + test suite |
| 6-7 | Jurist-acceptatie | Geaccordeerde regelset |

## Jurist-Acceptatie Protocol

| Stap | Criterium | Threshold |
|------|-----------|-----------|
| 1. Leesbaarheidstest | Jurist leest 10 regels zonder code-uitleg | ≥95% correct |
| 2. Bronverificatie | Jurist verifieert alle sourceRefs | 100% correct |
| 3. Scenario-acceptatie | Jurist beoordeelt 10 scenarios | ≥95% correct |
| 4. Accordering | Jurist ondertekent | CI Gate 14 |

## CI/CD Integratie

```yaml
# .github/workflows/juraregel-gates.yml
name: JuraRegel Quality Gates

on: [push, pull_request]

jobs:
  gates:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Gate 1-13: Technical validation
        run: bash ci/run-gates.sh

      - name: Gate 14: Jurist acceptatie
        run: |
          python3 ci/check-acceptatie.py \
            --jrem-path use-cases/griffierecht/jrem/ \
            --min-versie 1.0.0
```

## Gerelateerde skills

- [agentic-governance](../agentic-governance/SKILL.md) — Multi-agent orchestratie
- [algoritmekader](../algoritmekader/SKILL.md) — Algoritme compliance
- [nora-architectuur](../nora-architectuur/SKILL.md) — NORA architectuur
- [bio-security-baseline](../bio-security-baseline/SKILL.md) — BIO2
- [genai-governance](../genai-governance/SKILL.md) — AI governance
- [cross-reference-matrix](../cross-reference-matrix/SKILL.md) — Volledige matrix

## Bronnen

- JuraRegel: github.com/djimit/juraregel
- JREM Schema: github.com/djimit/juraregel/jrem-open-source/
- RegelSpraak: regelspraak.nl
- ALEF: alef.nl
- OpenMythos: ~/OpenMythos/analysis/legal-ruleops-platform/
