---
name: uitvoeringsorganisaties
version: 1.0.0
description: >
  IV voor uitvoeringsorganisaties: UWV, Belastingdienst, IND, SVB, DJI.
  Algoritme-compliance, massale gegevensverwerking, en werkgerelateerde
  dienstverlening. Gebruik bij software-ontwikkeling voor of samenwerking
  met uitvoeringsorganisaties.
triggers:
  keywords:
    - UWV
    - Belastingdienst
    - IND
    - SVB
    - DJI
    - uitvoeringsorgaan
    - uitvoeringsorganisatie
    - CAOP
    - werk en inkomen
    - belasting
    - asiel
    - pensioen
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# Uitvoeringsorganisaties

IV voor de grootste uitvoeringsorganisaties van de Nederlandse overheid.
Deze organisaties verwerken miljoenen persoonsgegevens en gebruiken
algoritmen voor besluitvorming op schaal.

## Wanneer deze skill gebruiken

- Software-ontwikkeling voor UWV, Belastingdienst, IND, SVB, DJI
- Algoritme-compliance bij massale gegevensverwerking
- DPIA voor hoog-risico verwerkingen
- IAMA voor beslissingsalgoritmen
- Data-uitwisseling tussen uitvoeringsorganisaties
- Architectuur-review bij uitvoeringsorganisaties

## Organisaties Overzicht

| Organisatie | Volgers | Kern-IV | Algoritmen |
|-------------|---------|---------|------------|
| UWV | 35.000+ | Uitkeringen, re-integratie | Risicoprofielering |
| Belastingdienst | 14.000+ | Belastingheffing | Aanwezigheidsdetectie |
| IND | 4.000+ | Asielprocedure | Risicoanalyse |
| SVB | 2.500+ | Pensioenen, kinderbijslag | Controlealgorithmen |
| DJI | 4.000+ | Justitiële jeugdzorg | Risicoschatting |
| CAOP | 1.500+ | Arbeidsvoorwaarden | — |

## UWV (Uitvoeringsinstituut Werknemersverzekeringen)

### Kern-IV Domeinen

- **Werkloosheid (WW)**: Uitkeringen, premie-inning, controle
- **Arbeidsongeschiktheid (WIA/WAO)**: Beoordeling, re-integratie
- **Ziekteverzuim (ZW)**: Bedrijfsgezondheidszorg, verzuimmanagement
- **Participatiewet**: Re-integratie, loonkostesubsidie

### Algoritme-Compliance

UWV gebruikt algoritmen voor:
- **Risicoprofielering**: Kans op langdurige arbeidsongeschiktheid
- **Re-integratie-advies**: Welke maatregelen hebben de meeste kans?
- **Fraudedetectie**: Onregelmatigheden in uitkeringen

Compliance vereisten:
- **IAMA**: Verplicht bij hoog-risico besluitvorming
- **Algoritmeregister**: Publicatie in register.algoritmes.overheid.nl
- **Verantwoordelijkheid**: UWV blijft verantwoordelijk, ook bij algoritmische ondersteuning

### Data-uitwisseling

UWV ontvigt gegevens van:
- **Belastingdienst**: Inkomensgegevens
- **SVB**: Pensioengegevens
- **Zorgverzekeraars**: Ziektemeldingen
- **Werkgevers**: Loonspecificaties

## Belastingdienst

### Kern-IV Domeinen

- **Inkomstenbelasting**: Aangiftes, hefting, teruggave
- **Vennootschapsbelasting**: Bedrijfsaangiftes
- **BTW**: Omzetbelasting
- **Accijnzen**: Alcohol, tabak, brandstof
- **Successierechten**: Erfbelasting

### Algoritme-Compliance

Belastingdienst gebruikt algoritmen voor:
- **Aanwezigheidsdetectie**: Risico op onterechte thuiswonenden
- **Fraudedetectie**: Onregelmatigheden in aangiftes
- **Profilering**: Belastingcontrole-prioritering

Compliance vereisten:
- **IAMA**: Verplicht bij risicoprofielering
- **Algoritmeregister**: Publicatie verplicht
- **Rechtsbescherming**: Bezwaarschrift en beroep mogelijk

### Data-uitwisseling

- **BRP**: Persoonsgegevens
- **UWV**: Werkgelegenheidsgegevens
- **SVB**: Pensioengegevens
- **Zorgverzekeraars**: Premiegegevens
- **Internationale uitwisseling**: CRS, FATCA

## IND (Immigratie- en Naturalisatiedienst)

### Kern-IV Domeinen

- **Asielprocedure**: Aanvraag, behandeling, beslissing
- **Verblijfsvergunningen**: Regulier, humanitair, gezinshereniging
- **Naturalisatie**: Naturalisatieverzoeken
- **vreemdelingenpolitie**: Opsporing, terugkeer

### Algoritme-Compliance

IND gebruikt algoritmen voor:
- **Risicoanalyse**: Veiligheidsrisico's bij asielzoekers
- **Processtroom**: Routering van aanvragen
- **Taalanalyse**: Herkomstbepaling aan de hand van taal

Compliance vereisten:
- **IAMA**: Verplicht bij risicoanalyse
- **Algoritmeregister**: Publicatie verplicht
- **Privacy**: Bijzondere zorg bij asielgegevens

## SVB (Sociale Verzekeringsbank)

### Kern-IV Domeinen

- **AOW**: Ouderdomspensioen
- **AOW**: Overlevingspensioen
- **Kinderbijslag**: Algemene Kinderbijslagwet
- **Anw**: Algemene nabestaandenwet

### Algoritme-Compliance

SVB gebruikt algoritmen voor:
- **Controlealgorithmen**: Onregelmatigheden detecteren
- **Prognoses**: Pensioenuitgaven voorspellen
- **Procesautomatisering**: Aanvragen routeren

## DJI (Dienst Justitiële Inrichtingen)

### Kern-IV Domeinen

- **Jeugdzorg**: Jeugdinrichtingen, jeugdhulp
- **Justitiële inrichtingen**: Gevangenissen, TBS-klinieken
- **Reclassering**: Toezicht, begeleiding

### Algoritme-Compliance

DJI gebruikt algoritmen voor:
- **Risicoschatting**: Recidivekans
- **Plaatsing**: Welke inrichting past bij welke justitiabele?
- **Voorwaardelijke invrijheidstelling**: Risico-assessment

## Gemeenschappelijke Compliance

### IAMA (Impact Assessment Mensenrechten en Algoritmen)

Verplicht voor alle uitvoeringsorganisaties bij:
- Hoog-risico algoritmen
- Systematische monitoring
- Besluitvorming zonder menselijke tussenkomst

### Algoritmeregister

Alle algoritmen moeten geregistreerd worden in:
- register.algoritmes.overheid.nl
- Met beschrijving, doel, risico's, maatregelen

### DPIA

Verplicht bij:
- Hoog-risico verwerking
- Systematische monitoring op grote schaal
- Biometrische gegevens
- Gezondheidsgegevens op grote schaal

### AVG Compliance

- **Rechtmatigheid**: Wettelijke grondslag (artikel 6 AVG)
- **Doelbinding**: Alleen voor oorspronkelijk doel
- **Data minimisation**: Alleen noodzakelijke gegevens
- **Bewaartermijnen**: Conform Archiefwet 2021
- **Verzoekrechten**: Inzage, correctie, verwijdering, verplaatsing

## Architectuur voor Uitvoeringsorganisaties

### NORA Compliance

Alle uitvoeringsorganisaties moeten voldoen aan:
- NORA principes (via agentic-governance skill)
- BIO2 beveiligingsmaatregelen
- API Design Rules
- GEMMA referentiearchitectuur

### Veiligde Verwerking

- **BIO2 domein 8**: Cryptografie
- **BIO2 domein 9**: Fysieke beveiliging
- **BIO2 domein 10**: Operationeel beheer
- **BIO2 domein 11**:Communicatiebeveiliging

## Gerelateerde skills

- [algoritmekader](../algoritmekader/SKILL.md) — Algoritme compliance
- [iama-assessment](../iama-assessment/SKILL.md) — IAMA uitvoeren
- [dpia-assessment](../dpia-assessment/SKILL.md) — DPIA uitvoeren
- [avg-privacy](../avg-privacy/SKILL.md) — AVG compliance
- [genai-governance](../genai-governance/SKILL.md) — AI governance
- [bio-security-baseline](../bio-security-baseline/SKILL.md) — BIO2
- [logboek-dataverwerkingen](../logboek-dataverwerkingen/SKILL.md) — Logging
- [nora-architectuur](../nora-architectuur/SKILL.md) — Architectuur

## Bronnen

- Algoritmeregister: register.algoritmes.overheid.nl
- IAMA: algoritmekader.overheid.nl
- UWV: uwv.nl
- Belastingdienst: belastingdienst.nl
- IND: ind.nl
- SVB: svb.nl
- DJI: dji.nl
