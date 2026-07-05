---
name: ai-governance
version: 1.0.0
description: >
  EU AI Act compliance checker voor de Nederlandse overheid. Classificeert
  AI-systemen in risicocategorieën, checkt verplichte documentatie, genereert
  compliance checklists, en adviseert over governance-structuren voor hoog-risico
  AI. Integreert met BIO2, IAMA en NORA.
  Gebruik bij AI-systeem beoordeling, FRIA, of EU AI Act compliance.
triggers:
  keywords:
    - EU AI Act
    - AI-verordening
    - AI governance
    - AI compliance
    - algoritme toezicht
    - AI risicoclassificatie
    - hoog risico AI
    - conformiteitsbeoordeling AI
    - AI transparantie
    - FRIA
    - fundamental rights
    - AI sandbox
    - IAMA
    - algoritmerisico
    - discriminatie AI
    - bias AI
    - AI uitlegbaarheid
    - menselijk toezicht AI
    - human-in-the-loop AI
    - AI kwaliteitsmanagement
    - AI incident melden
    - notified body AI
    - CE-markering AI
tools:
  - Read
  - Glob
  - Grep
  - Bash
  - WebFetch
---

# EU AI Act Compliance Checker

Toets AI-systemen aan de EU AI Act (Verordening 2024/1689). De AI Act is van kracht sinds 1 augustus 2024 met gefaseerde inwerkingtreding.

## Wanneer deze skill gebruiken

- AI-systeem classificatie (verboden/hoog-risico/beperkt/minimaal)
- FRIA (Fundamental Rights Impact Assessment) uitvoeren
- Conformiteitsbeoordeling voor hoog-risico AI
- Technische documentatie opstellen (Annex IV)
- Menselijk toezicht-maatregelen ontwerpen
- AI incident-melding procedure
- AI Literacy training voor overheidspersoneel

## Risicoclassificatie

### Stap 1: Bepaal de risicocategorie

```
Is het AI-systeem verboden onder Art. 5?
  ├── Ja → ONAANVAARDBAAR RISICO (verboden)
  └── Nee
      └── Valt het onder Annex III (hoog-risico use cases)?
            ├── Ja → HOOG RISICO (Art. 6 + Annex III)
            └── Nee
                └── Is het een GPAI-model met systemisch risico?
                      ├── Ja → SYSTEMISCH RISICO (Art. 51-55)
                      └── Nee
                          └── Interageert het direct met mensen?
                                ├── Ja → BEPERKT RISICO (transparantieplicht)
                                └── Nee → MINIMAAL RISICO
```

### Verboden AI-praktijken (Art. 5)

| Praktijk | Kenmerken |
|----------|-----------|
| Subliminale manipulatie | Technieken onder bewustzijn die gedrag verstoren |
| Kwetsbaren uitbuiten | Leeftijd of handicap exploiteren |
| Social scoring | Classificatie op basis van sociaal gedrag |
| Individuele risicovoorspelling | Profiling voor crimineel gedrag |
| Gezichtsdatabases scrapen | Ongerichte scraping voor herkenning |
| Emotieherkenning | Op werkplek/onderwijs (uitzondering: medisch) |
| Biometrische categorisatie | Op basis van gevoelige kenmerken |
| Real-time biometrische ID | In publieke ruimten (beperkt toegestaan) |

### Hoog-risico AI-systemen (Annex III)

| Domein | Use case |
|--------|----------|
| Biometrie | Biometrische identificatie op afstand, emotieherkenning |
| Kritieke infrastructuur | Beheer digitale infrastructuur, wegverkeer, nutsvoorzieningen |
| Onderwijs | Toelating, toewijzing, evaluatie leerresultaten |
| Werkgelegenheid | Werving, selectie, prestatiebeoordeling, beëindiging |
| Essentiële diensten | Toegang publieke diensten, kredietwaardigheid, verzekeringen |
| Wetshandhaving | Recidiverisicobeoordeling, leugendetectie, bewijsanalyse |
| Migratie | Asiel, visum, grenscontrole, risicobeoordeling |
| Rechtspraak | Rechtsfeitelijk onderzoek, interpretatie van recht |
| Democratische processen | Beïnvloeding verkiezingsuitslagen |

## Verplichtingen voor hoog-risico AI

### 1. Risicomanagementsysteem (Art. 9)
Continue, iteratief proces: identificatie → analyse → evaluatie → beperking → testen

### 2. Datakwaliteit (Art. 10)
Relevant, representatief, foutloos, compleet. Bias-detectie verplicht.

### 3. Technische documentatie (Art. 11 + Annex IV)
Algemene beschrijving, elementen, monitoring, risicomanagement, wijzigingen, EU-conformiteitsverklaring.

### 4. Transparantie (Art. 13)
Gebruiksinstructie met: identiteit aanbieder, kenmerken, risico's, nauwkeurigheid, menselijk toezicht.

### 5. Menselijk toezicht (Art. 14)
Interface moet begrip, herkenning automatisbias, correcte interpretatie, stop-knop mogelijk maken.

### 6. Nauwkeurigheid en robuustheid (Art. 15)
Gepast niveau, weerbaar tegen fouten/manipulatie, fail-safe plannen, cyberbeveiliging.

## Rollen en verantwoordelijkheden

| Rol | Definitie | Kernverplichtingen |
|-----|-----------|-------------------|
| Aanbieder | Ontwikt AI en brengt op markt | Volledige compliance, CE-markering, EU-databank |
| Gebruiksverantwoordelijke | Gebruikt AI professioneel | Menselijk toezicht, FRIA, monitoring, incidenten melden |
| Importier | Brengt niet-EU AI op EU-markt | Verificatie compliance aanbieder |
| Distributeur | Maakt beschikbaar op markt | Verificatie CE-markering |

## FRIA (Art. 27)

Gebruiksverantwoordelijken van hoog-risico AI moeten:

1. Procesbeschrijving vastleggen
2. Gebruiksperiode en frequentie bepalen
3. Getroffen personen categoriseren
4. Risico's voor grondrechten analyseren
5. Menselijk toezicht-maatregelen beschrijven
6. Mitigerende maatregelen bij materialisatie

**Uitzondering:** MKB (klein/micro) — geldt NIET voor overheidsinstanties!

## Sancties (Art. 99)

| Overtreding | Maximale boete |
|------------|----------------|
| Verboden AI-praktijken | €35M of 7% wereldwijde omzet |
| Andere inbreuken | €15M of 3% |
| Onjuiste informatie | €7,5M of 1.5% |

## IAMA Integratie

Bij AI-systemen in overheidscontext moet ook het IAMA worden doorlopen:

| Aspect | FRIA (AI Act) | IAMA (NL) |
|--------|---------------|-----------|
| Doel | Grondrechten-effecten AI | Integrale algoritme-effecten |
| Reikwijdte | Hoog-risico AI | Alle overheidsalgoritmen |
| Verplicht | Voor deployers | Voor overheid |

**Advies:** Voer IAMA als hoofdproces uit, documenteer FRIA-specifieke elementen apart.

## Compliance Checklist

### Aanbieder hoog-risico AI
- [ ] Risicoclassificatie gedocumenteerd
- [ ] Risicomanagementsysteem (Art. 9)
- [ ] Data governance (Art. 10)
- [ ] Technische documentatie Annex IV (Art. 11)
- [ ] Gebruiksinstructie (Art. 13)
- [ ] Menselijk toezicht interface (Art. 14)
- [ ] Nauwkeurigheid en robuustheid (Art. 15)
- [ ] Conformiteitsbeoordeling (Art. 43)
- [ ] EU-conformiteitsverklaring (Art. 47)
- [ ] CE-markering (Art. 48)
- [ ] EU-databank registratie (Art. 49)
- [ ] Documentatie 10 jaar bewaren (Art. 18)

### Gebruiksverantwoordelijke (overheid)
- [ ] FRIA uitgevoerd (Art. 27)
- [ ] Menselijk toezicht toegewezen (Art. 26)
- [ ] AI-geletterdheid personeel (Art. 4)
- [ ] Inputdata representativiteit
- [ ] Monitoring ingericht
- [ ] Incidentmelding (binnen 15 dagen)
- [ ] EU-databank registratie (overheid verplicht)
- [ ] DPIA indien persoonsgegevens

## Gerelateerde skills

- [genai-governance](../genai-governance/SKILL.md) — EU AI Act technische governance
- [algoritmekader](../algoritmekader/SKILL.md) — Algoritmekader compliance
- [iama-assessment](../iama-assessment/SKILL.md) — IAMA uitvoeren
- [dpia-assessment](../dpia-assessment/SKILL.md) — DPIA uitvoeren
- [nora-architectuur](../nora-architectuur/SKILL.md) — Architectuur compliance
- [bio-security-baseline](../bio-security-baseline/SKILL.md) — BIO2
- [uitvoeringsorganisaties](../uitvoeringsorganisaties/SKILL.md) — UWV, Belasting, IND

## Bronnen

- EU AI Act: eur-lex.europa.eu/eli/reg/2024/1689
- AI Act Explorer: artificialintelligenceact.eu/ai-act-explorer/
- Nederlandse AI-autoriteit: ai-autoriteit.nl
- Algoritmekader: algoritmekader.overheid.nl
- IAMA: algoritmekader.overheid.nl/iama
