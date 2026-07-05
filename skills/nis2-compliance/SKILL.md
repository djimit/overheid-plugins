---
name: nis2-compliance
version: 1.0.0
description: >
  NIS2/Cyberbeveiligingswet compliance voor de Nederlandse overheid.
  Implementatie van NIS2-vereisten voor essentiële en belangrijke diensten.
  Gebruik bij cybersecurity compliance, incidentrapportage, of risicomanagement.
triggers:
  keywords:
    - NIS2
    - Cyberbeveiligingswet
    - cybersecurity
    - incident rapportage
    - risicomanagement
    - essentieel dienst
    - belangrijk dienst
    - CCB
    - NCSC
    - supply chain security
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# NIS2 Compliance

NIS2-richtlijn (Richtlijn (EU) 2022/2555) en de Nederlandse
Cyberbeveiligingswet (Cbw). Verplichte cybersecurity-maatregelen voor
essentiële en belangrijke diensten.

## Wanneer deze skill gebruiken

- NIS2-classificatie (essentieel of belangrijk)
- Cybersecurity risicomanagement
- Incidentrapportage aan CCB/NCSC
- Supply chain security
- Technische en organisatorische maatregelen
- Audit voorbereiding

## NIS2 Classificatie

### Essentiële diensten (Art. 2(1))

| Sector | Diensten |
|--------|----------|
| Energie | Elektriciteit, gas, olie, warmte |
| Transport | Luchtvaart, spoor, scheepvaart, weg |
| Banken | Kredietinstellingen |
| Financiële markten | Beurzen, centrale tegenpartijen |
| Gezondheid | Ziekenhuizen, laboratoria, farma |
| Drinkwater | Distributie en levering |
| Afvalwater | Behandeling en distributie |
| Digitale infrastructuur | DNS, TLD, IXPs, cloud |
| Telecom | Elektronische communicatie |
| Overheid | Overheidsdiensten op nationaal niveau |
| Ruimte | Grondstations, satellieten |

### Belangrijke diensten (Art. 2(2))

| Sector | Diensten |
|--------|----------|
| Postdiensten | Post en koeriers |
| Afvalbeheer | Afvalverwerking |
- Chemicaliën | Productie en distributie |
| Voedsel | Productie, verwerking, distributie |
| Productie | Fabricage van medische hulpmiddelen, elektronica |
| Digitale providers | Sociale netwerken, zoekmachines |
| Onderwijs | Universiteiten, onderzoek |

## Verplichtingen

### Technische maatregelen (Art. 21)

- **Risicomanagement**: Identificatie, analyse, beperking van risico's
- **Incidentafhandeling**: Preventie, detectie, respons
- **Business continuity**: Back-up, disaster recovery
- **Supply chain security**: Leveranciersbeoordeling
- **Secure development**: Veilige ontwikkelpraktijken
- **Cryptografie**: Versleuteling van data in rust en transit
- **Toegangsbeheer**: Principle of least privilege
- **Multi-factor authentication**: Verplicht voor bevoegde personen

### Organisatorische maatregelen

- **Verantwoordelijkheid**: Management is verantwoordelijk
- **Training**: Periodieke cybersecurity training
- **Beleid**: Cybersecurity beleid en procedures
- **Audits**: Periodieke audits (intern en extern)
- **Certificering**: ISO 27001 of equivalent

### Incidentrapportage (Art. 23)

| Type | Termijn | Aan |
|------|---------|-----|
| Vroegschakel | Binnen 24 uur | CCB/NCSC |
| Volledig | Binnen 72 uur | CCB/NCSC |
| Eindrapport | Binnen 1 maand | CCB/NCSC |

### Sancties

| Overtreding | Essentieel | Belangrijk |
|-------------|-----------|------------|
| Non-compliance | €10M of 2% omzet | €7M of 1,4% omzet |
| Niet melden incident | €10M of 2% omzet | €7M of 1,4% omzet |

## NIS2 → BIO2 Mapping

| BIO2 Domein | NIS2 Artikel | Maatregel |
|-------------|-------------|-----------|
| 2.1 Beleid | Art. 21(1) | Cybersecurity beleid |
| 3.1 Organisatie | Art. 21(1) | Verantwoordelijkheden |
| 4.1 Risicomanagement | Art. 21(2)(a) | Risico-analyse |
| 5.1 Technische maatregelen | Art. 21(2)(b) | Incidentafhandeling |
| 6.1 Fysieke beveiliging | Art. 21(2)(c) | Fysieke toegangscontrole |
| 7.1 Operationeel beheer | Art. 21(2)(d) | Patch management |
| 8.1 Communicatiebeveiliging | Art. 21(2)(e) | Versleuteling |
| 9.1 Systeemontwikkeling | Art. 21(2)(f) | Secure development |
| 10.1 Incidentmanagement | Art. 23 | Rapportage |
| 11.1 Business continuity | Art. 21(2)(b) | Back-up, DR |
| 12.1 Compliance | Art. 21(1) | Audits |
| 13.1 Externe partijen | Art. 21(2)(d) | Supply chain |

## Implementatie Stappen

### 1. Classificatie
- Bepaal of je organisatie essentieel of belangrijk is
- Documenteer de classificatie
- Registreer bij bevoegde autoriteit

### 2. Gap Analyse
- BIO2 baseline toepassen
- NIS2-specifieke eisen toevoegen
- Huidige maatregelen beoordelen
- Gaps identificeren

### 3. Maatregelen Implementeren
- Technische maatregelen prioriteren
- Organisatorische maatregelen uitrollen
- Training voor personeel
- Procedures documenteren

### 4. Incidentafhandeling
- Incident response team
- Meldprocedure (24h/72h/1mnd)
- Communicatie-template
- Post-incident review

### 5. Monitoring en Improvement
- Continue monitoring
- Periodieke audits
- Lessons learned
- Beleidsupdate

## Gerelateerde skills

- [bio-security-baseline](../bio-security-baseline/SKILL.md) — BIO2
- [llm-security](../llm-security/SKILL.md) — LLM security
- [cloud-overheid](../cloud-overheid/SKILL.md) — Cloud security
- [overheid-authenticatie](../overheid-authenticatie/SKILL.md) — Authenticatie
- [digitale-soevereiniteit](../digitale-soevereiniteit/SKILL.md) — Soevereiniteit
- [agentic-governance](../agentic-governance/SKILL.md) — Orchestratie

## Bronnen

- NIS2 Richtlijn: eur-lex.europa.eu/eli/dir/2022/2555
- Cyberbeveiligingswet: wetten.overheid.nl
- NCSC: ncsc.nl
- CCB: ccb.nl
- BIO2: MinBZK Baseline Informatiebeveiliging Overheid
