---
name: waterschappen
version: 1.0.0
description: >
  IV voor de 21 Nederlandse waterschappen. Waterbeheer, waterkeringen,
  waterkwaliteit, en ruimtelijke ordening. Gebruik bij waterschaps-ontwikkeling
  of waterbeheer-projecten.
triggers:
  keywords:
    - waterschap
    - waterbeheer
    - waterkering
    - dijk
    - waterkwaliteit
    - riolering
    - pompcapaciteit
    - wateroverlast
    - hoogwater
    - WBH
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# Waterschappen

Informatievoorziening voor de 21 Nederlandse waterschappen. Waterschappen
zijn de oudste democratische instellingen van Nederland en hebben complexe
IV-behoeften op het gebied van waterbeheer.

## Wanneer deze skill gebruiken

- Waterschaps-ontwikkeling
- Waterkering-beheer
- Waterkwaliteitsmonitoring
- Rioleringsbeheer
- Hoogwaterbeschermingsprogramma
- Klimaatadaptatie projecten
- Samenwerking met provincies en gemeenten

## De 21 Waterschappen

| Waterschap | Provincie | Type |
|-----------|-----------|------|
| Rijnland | Zuid-Holland/Noord-Holland/Utrecht | Delta |
| Schieland en de Krimpenerwaard | Zuid-Holland | Delta |
| Delfland | Zuid-Holland | Delta |
| Hollandse Delta | Zuid-Holland | Delta |
| Zeeuwse Eilanden | Zeeland | Zee |
| Zeeuws-Vlaanderen | Zeeland | Grens |
| Reest en Wieden | Drenthe/Overijssel | Binnenwater |
| Vechtstromen | Overijssel/Drenthe | Binnenwater |
| Drents Overijsselse Delta | Drenthe/Overijssel | Binnenwater |
| Hunze en Aa's | Groningen | Noord |
| Noorderzijlvest | Groningen | Noord |
| Fryslân | Friesland | Binnenwater |
| Rijn en IJssel | Gelderland | Rivier |
| Rivierenland | Gelderland/Zuid-Holland/Utrecht | Rivier |
| Gelderse Vallei | Gelderland/Utrecht | Binnenwater |
| Brabantse Delta | Noord-Brabant | Delta |
| De Dommel | Noord-Brabant | Binnenwater |
| Aa en Maas | Noord-Brabant | Rivier |
| Limburg | Limburg | Rivier |
| Scheldestroom | Zeeland | Zee |
| Hunze en Aa's | Groningen | Noord |

## IV Domeinen

### 1. Waterkeringen

- **Dijken**: Zee- en rivierdijken
- **Duinen**: Kustverdediging
- **Stormvloedkeringen**: Hart van Hollands Verdediging
- **Keringen**: Regionale keringen
- **Inspectie**: Periodieke keuring conform Waterwet

### 2. Waterkwaliteit

- **RWZI**: Rioolwaterzuiveringsinstallaties
- **Zuiveringsbeheer**: Zuivering van afvalwater
- **Effluent**: Lozing op oppervlaktewater
- **Monitoring**: Continue waterkwaliteitsmetingen
- **Kaderrichtlijn Water**: EU compliance

### 3. Wateroverlast

- **Riolering**: Transport van afvalwater
- **Gemengd systeem**: Regen + afvalwater
- **Verbeterde gescheiden systematiek**: Scheiding regen/afvalwater
- **Pompcapaciteit**: Capaciteit van gemaal
- **Bergingscapaciteit**: Oppervlakkige berging

### 4. Hoogwaterbescherming

- **HWBP**: Hoogwaterbeschermingsprogramma
- **Ruimte voor de Rivier**: Ruimtelijke maatregelen
- **Dijkversterking**: Verhoging en verbreding
- **Klimaatdijk**: Toekomstbestendige dijken
- **Evacuatie**: Planning en uitvoering

### 5. Klimaatadaptatie

- **Wateropvang**: Regenwater vasthouden
- **Groeninfrastructuur**: Groene daken, wadi's
- **Droogtebeheer**: Waterbesparing
- **Hittestress**: Koele zones
- **Veiligheidsregio**: Samenwerking bij rampen

## Architectuur

### Waterschaps GEMMA

Waterschappen gebruiken GEMMA (gemeentelijke variant NORA):
- **GEMMA Online**: gemmaonline.nl
- **Vijflagenmodel**: Strategie, Organisatie, Informatie, Applicaties, Techniek
- **Sector-standaarden**: Waterschaps-specifieke uitbreidingen

### Data-uitwisseling

Waterschappen wisselen data uit met:
- **Rijkswaterstaat**: Grote wateren, rijkswegen
- **Provincies**: Ruimtelijke ordening
- **Gemeenten**: Riolering, bouwvergunningen
- **KNMI**: Weersvoorspellingen
- **RIVM**: Waterkwaliteit

## Compliance

### Waterwet
- Waterbeheerplan (4-jaarlijks)
- Waterbeheersvisie
- Keur (waterschapsverordening)

### Kaderrichtlijn Water
- EU compliance voor oppervlaktewater
- Goede ecologische toestand
- Goede chemische toestand

### AVG
- Verwerkingsregister
- Functionaris Gegevensbescherming
- Monitoringgegevens als persoonsgegevens

### Omgevingswet
- DSO koppeling voor watergerelateerde vergunningen
- Omgevingsvisie water

## Gerelateerde skills

- [provincies](../provincies/SKILL.md) — Provincies
- [gemeentelijke-iv](../gemeentelijke-iv/SKILL.md) — Gemeentelijke IV
- [dso-omgevingswet](../dso-omgevingswet/SKILL.md) — Omgevingswet
- [geo-ruimtelijke-iv](../geo-ruimtelijke-iv/SKILL.md) — Geo-data
- [nora-architectuur](../nora-architectuur/SKILL.md) — Architectuur
- [open-data](../open-data/SKILL.md) — Open data
- [avg-privacy](../avg-privacy/SKILL.md) — Privacy

## Bronnen

- Waterschappen: waterschappen.nl
- Rijkswaterstaat: rijkswaterstaat.nl
- KNMI: knmi.nl
- Kaderrichtlijn Water: rws.nl
- Waterwet: wetten.overheid.nl
