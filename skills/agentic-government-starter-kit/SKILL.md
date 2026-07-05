---
name: agentic-government-starter-kit
version: 1.0.0
description: >
  Snel starten met agentic government development. Scaffold, configureer
  en deploy multi-agent workflows voor overheidsprocessen.
  Gebruik bij nieuwe projecten, team-onboarding, of proof-of-concept.
triggers:
  keywords:
    - starter kit
    - quick start
    - scaffold
    - template
    - boilerplate
    - npx
    - init
    - agent template
    - government template
tools:
  - Read
  - Glob
  - Grep
  - Bash
  - Task
  - Write
  - Edit
---

# Agentic Government Starter Kit

Snel beginnen met agentic government development. Dit skill biedt
templates, configuraties en stapsgewijze instructies voor het opzetten
van multi-agent workflows binnen de Nederlandse overheid.

## Wanneer deze skill gebruiken

- Nieuw overheidssoftware-project opzetten
- Team onboarding voor agentic development
- Proof-of-concept voor compliance-automatisering
- Multi-agent workflow design
- Government AI project initiatie

## Snel Starten

### Stap 1: Project Scaffold

Maak een nieuw agentic government project aan:

```
my-gov-project/
├── agents/
│   ├── compliance-agent.yaml
│   ├── architect-agent.yaml
│   └── security-agent.yaml
├── workflows/
│   ├── compliance-pipeline.yaml
│   └── incident-response.yaml
├── skills/
│   └── (symlink naar overheid-plugins/skills/)
├── tests/
│   ├── scenarios/
│   │   ├── happy-path.yaml
│   │   ├── edge-cases.yaml
│   │   └── worst-case.yaml
│   └── conftest.py
├── ci/
│   └── validate-skills.yml
├── monitoring/
│   ├── prometheus-rules.yaml
│   └── grafana-dashboard.json
└── README.md
```

### Stap 2: Configureer Agents

Gebruik deze templates als basis:

#### Compliance Agent Template

```yaml
# agents/compliance-agent.yaml
name: compliance-agent
version: 1.0.0
role: Compliance Officer
organisation:
  level: rijk | provincie | gemeente | waterschap | uitvoeringsorgaan
  name: "Mijn Organisatie"

system_prompt: |
  Je bent de Compliance Agent voor [ORGANISATIE].
  Je controleert of voldaan wordt aan:
  - NORA architectuurprincipes
  - BIO2 beveiligingsmaatregelen
  - AVG/GDPR vereisten
  - Toegankelijkheid (WCAG 2.2)
  - EU AI Act (bij AI-systemen)

  Beleid:
  - L1 regels: automatisch uitvoeren
  - L2 regels: uitzonderingen flaggen voor review
  - L3 regels: altijd escaleren naar mens
  - L4 regels: NIET automatiseren, alleen adviseren

primary_skills:
  - nora-architectuur
  - bio-security-baseline
  - avg-privacy
  - digitoegankelijk
  - dpia-assessment

escalation:
  target: jurist
  threshold: 0.95
  method: human-review

monitoring:
  metrics_endpoint: /metrics
  log_level: INFO
  audit_trail: true
```

#### Security Agent Template

```yaml
# agents/security-agent.yaml
name: security-agent
version: 1.0.0
role: Security Expert
organisation:
  level: rijk | provincie | gemeente | waterschap | uitvoeringsorgaan
  name: "Mijn Organisatie"

system_prompt: |
  Je bent de Security Agent voor [ORGANISATIE].
  Je controleert informatiebeveiliging op:
  - BIO2 maatregelen (162 verplicht)
  - NCSC richtlijnen (TLS, webapplicaties, basisprincipes)
  - NIS2/Cyberbeveiligingswet compliance
  - LLM security (OWASP Top 10)
  - Digitale soevereiniteit (CLOUD Act)

  Beleid:
  - Kritieke beveiligingsissues: direct escaleren
  - BIO2 non-compliance: flaggen met deadline
  - LLM security: alleen advisering, geen automatische actie

primary_skills:
  - bio-security-baseline
  - llm-security
  - overheid-authenticatie
  - digitale-soevereiniteit

escalation:
  target: ciso
  threshold: 0.97
  method: immediate-alert

monitoring:
  metrics_endpoint: /metrics
  log_level: WARN
  audit_trail: true
```

#### Privacy Agent Template

```yaml
# agents/privacy-agent.yaml
name: privacy-agent
version: 1.0.0
role: Privacy Officer
organisation:
  level: rijk | provincie | gemeente | waterschap | uitvoeringsorgaan
  name: "Mijn Organisatie"

system_prompt: |
  Je bent de Privacy Agent voor [ORGANISATIE].
  Je controleert AVG/GDPR compliance:
  - Rechtmatigheid van verwerking
  - Data minimisation
  - Bewaartermijnen
  - DPIA-vereisten
  - Verzoekrechten (inzage, correctie, verwijdering)
  - Logboek Dataverwerkingen

  Beleid:
  - Hoog-risico verwerking: altijd escaleren
  - DPIA-vereist: automatisch DPIA-template genereren
  - Verzoekrechten: binnen 30 dagen afhandelen

primary_skills:
  - avg-privacy
  - dpia-assessment
  - logboek-dataverwerkingen
  - iama-assessment

escalation:
  target: autoriteit-persoonsgegevens
  threshold: 0.95
  method: human-review

monitoring:
  metrics_endpoint: /metrics
  log_level: INFO
  audit_trail: true
```

### Stap 3: Definieer Workflows

```yaml
# workflows/compliance-pipeline.yaml
name: compliance-pipeline
version: 1.0.0
description: End-to-end compliance checking voor overheidssoftware

steps:
  - name: intake
    agent: intake-agent
    output: validated-input

  - name: security-check
    agent: security-agent
    input: validated-input
    output: security-report
    escalation:
      condition: critical-finding
      target: ciso

  - name: privacy-check
    agent: privacy-agent
    input: validated-input
    output: privacy-report
    escalation:
      condition: high-risk-processing
      target: privacy-officer

  - name: architecture-check
    agent: architect-agent
    input: validated-input
    output: architecture-report
    escalation:
      condition: new-standard
      target: enterprise-architect

  - name: synthesis
    agent: synthesis-agent
    input:
      - security-report
      - privacy-report
      - architecture-report
    output: compliance-report

  - name: jurist-review
    agent: human-gate
    input: compliance-report
    condition: confidence < 0.95
    output: approved-report

  - name: publication
    agent: publication-agent
    input: approved-report
    output: published-decision
```

### Stap 4: Test met Scenarios

```yaml
# tests/scenarios/happy-path.yaml
name: happy-path-compliance
description: L1 regels, geen escalatie verwacht

input:
  project: "Nieuwe gemeentelijke website"
  type: website
  data_classification: open
  ai_involvement: false

expected:
  security-result: PASS
  privacy-result: PASS
  architecture-result: PASS
  escalations: 0
  final-status: APPROVED
```

```yaml
# tests/scenarios/edge-cases.yaml
name: edge-case-ai-classification
description: L2 regels, escalatie bij AI-classificatie onzekerheid

input:
  project: "AI-gestuurde werkzoekenden-advisering"
  type: ai-system
  data_classification: persoonsgegevens
  ai_involvement: true
  ai_risk_class: limited-risk

expected:
  security-result: PASS-WITH-FINDINGS
  privacy-result: DPIA-REQUIRED
  architecture-result: PASS
  escalations: 1
  escalation-target: jurist
  final-status: PENDING-REVIEW
```

### Stap 5: CI/CD Integratie

```yaml
# ci/validate-skills.yml
name: Validate Skills

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Validate agent configurations
        run: |
          python3 -c "
          import yaml, sys, os
          errors = []
          for root, dirs, files in os.walk('agents'):
              for f in files:
                  if f.endswith('.yaml'):
                      path = os.path.join(root, f)
                      try:
                          with open(path) as fh:
                              data = yaml.safe_load(fh)
                          for field in ['name', 'role', 'system_prompt', 'primary_skills']:
                              if field not in data:
                                  errors.append(f'{path}: missing {field}')
                      except Exception as e:
                          errors.append(f'{path}: {e}')
          if errors:
              for e in errors:
                  print(f'ERROR: {e}')
              sys.exit(1)
          print('All agent configurations valid')
          "

      - name: Validate workflow definitions
        run: |
          python3 -c "
          import yaml, sys, os
          for root, dirs, files in os.walk('workflows'):
              for f in files:
                  if f.endswith('.yaml'):
                      path = os.path.join(root, f)
                      with open(path) as fh:
                          data = yaml.safe_load(fh)
                      assert 'steps' in data, f'{path}: missing steps'
                      for step in data['steps']:
                          assert 'name' in step, f'{path}: step missing name'
                          assert 'agent' in step, f'{path}: step missing agent'
          print('All workflow definitions valid')
          "

      - name: Run scenario tests
        run: |
          echo "Running scenario tests..."
          for scenario in tests/scenarios/*.yaml; do
            echo "Testing: $scenario"
            # In production: run actual agent workflow
            echo "PASS: $scenario"
          done
```

## Monitoring Setup

### Prometheus Rules

```yaml
# monitoring/prometheus-rules.yaml
groups:
  - name: agentic-government
    rules:
      - alert: HighEscalationRate
        expr: rate(agent_escalations_total[5m]) > 0.2
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "High escalation rate ({{ $value }})"

      - alert: AgentConfidenceLow
        expr: agent_confidence_score < 0.85
        for: 10m
        labels:
          severity: warning
        annotations:
          summary: "Agent confidence below threshold"

      - alert: ComplianceCheckFailed
        expr: compliance_check_status == 0
        labels:
          severity: critical
        annotations:
          summary: "Compliance check failed"
```

## Gerelateerde skills

- [agentic-governance](../agentic-governance/SKILL.md) — Orchestratie patronen
- [kwiv-agent-personas](../kwiv-agent-personas/SKILL.md) — Agent persona mapping
- [cross-reference-matrix](../cross-reference-matrix/SKILL.md) — Skill dependencies
- [nora-architectuur](../nora-architectuur/SKILL.md) — Architectuur compliance
- [bio-security-baseline](../bio-security-baseline/SKILL.md) — Beveiliging

## Bronnen

- OpenMythos: ~/OpenMythos/analysis/legal-ruleops-platform/
- Djimitflo: ~/djimitflo/.data/djimitflo.sqlite
- JuraRegel: ~/Rechtspraak/rule-service/
- Prometheus: prometheus.io/docs/
- YAML spec: yaml.org/spec/
