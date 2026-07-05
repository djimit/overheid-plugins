---
name: provincies
version: 1.0.0
description: >
  IV voor de 12 Nederlandse provincies. Omgevingsvisie, provinciale wegen,
  MER-beoordeling, waterbeheer, en provinciale archivering.
  Gebruik bij provinciale software-ontwikkeling of intergemeentelijke
  samenwerking.
triggers:
  keywords:
    - provincie
    - provinciale
    - omgevingsvisie
    - provinciale wegen
    - MER
    - waterbeheer
    - provinciegronden
    - intergemeentelijk
    - omgevingsplan provincie
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# Provincies

Informatievoorziening voor de 12 Nederlandse provincies. Provincies hebben
een unieke positie tussen rijk en gemeenten met eigen IV-uitdagingen.

## Wanneer deze skill gebruiken

- Provinciale software-ontwikkeling
- Omgevingsvisie implementatie
- Provinciale wegen-beheer
- MER-beoordeling (Milieueffectrapportage)
- Waterbeheer en waterkeringen
- Intergemeentelijke samenwerking
- Provinciale archivering

## De 12 Provincies

| Provincie | Inwoners (2026) | IV-omvang |
|-----------|---------------|-----------|
| Zuid-Holland | 3.800.000 | Groot |
| Noord-Holland | 2.900.000 | Groot |
| Noord-Brabant | 2.600.000 | Groot |
| Gelderland | 2.100.000 | Groot |
| Utrecht | 1.400.000 | Middel |
| Overijssel | 1.200.000 | Middel |
| Limburg | 1.100.000 | Middel |
| Friesland | 660.000 | Klein |
| Groningen | 590.000 | Klein |
| Drenthe | 500.000 | Klein |
| Flevoland | 440.000 | Klein |
| Zeeland | 390.000 | Klein |

## IV Domeinen

### 1. Omgevingsvisie

Provincies stellen een omgevingsvisie op conform de Omgevingswet:

- **Omgevingsvisie**: Strategisch document voor de fysieke leefomgeving
- **Omgevingsverordening**: Regels voor de fysieke leefomgeving
- **MER-beoordeling**: Milieueffectrapportage voor grote projecten
- **DSO koppeling**: Digitaal Stelsel Omgevingswet

### 2. Provinciale Wegen

- **Wegenbeheer**: Onderhoud provinciale wegen
- **Verkeersmanagement**: Verkeersstromen, signalisatie
- **Bruggen en tunnels**: Beheer en onderhoud
- **OV**: Openbaar vervoer regiocontracten

### 3. Waterbeheer

- **Waterkeringen**: Dijken, duinen, keringen
- **Waterkwaliteit**: Monitoring en behandeling
- **Wateroverlast**: Riolering, pompcapaciteit
- **Waterschappen**: Coördinatie met 21 waterschappen

### 4. Ruimtelijke Ordening

- **Structuurvisie**: Provinciale ruimtelijke strategie
- **Bestemmingsplannen**: Goedkeuringsbevoegdheid
- **Reconstructie**: Herindeling landelijk gebied
- **Natuur**: Natura 2000-gebieden

### 5. Mobiliteit

- **OV-regio's**: OV-contracten
- **Fietsnetwerk**: Provinciaal fietsroutenetwerk
- **Laadinfrastructuur**: Elektrisch rijden
- **Hubs**: Mobiliteitshuizen

### 6. Cultuur en Erfgoed

- **Monumenten**: Provinciale monumenten
- **Erfgoed**: Cultuurhistorische waarden
- **Archieven**: Provinciaal archief
- **Bibliotheken**: Provinciale bibliotheken

## Architectuur

### Provinciaal GEMMA

Provincies gebruiken GEMMA (gemeentelijke variant NORA):
- **GEMMA Online**: gemmaonline.nl
- **Vijflagenmodel**: Strategie, Organisatie, Informatie, Applicaties, Techniek
- **Koppeling met rijk**: NORA → GEMMA mapping
- **Provinciale standaarden**: Uitbreiding met provinciale praktijk

### Intergemeentelijke Samenwerking

Provincies coördineren:
- **Veiligheidsregio's**: Brandweer, GHOR, rampenbestrijding
- **GGD-regio's**: Geneeskundige hulpverleningsorganisatie
- **Samenwerkingsverbanden**: Gemeenschappelijke regelingen
- **IT-samenwerking**: Gedeelde diensten via provincies

## Compliance

### Omgevingswet
- STOP/TPOD standaarden
- DSO API koppeling
- Omgevingsloket provinciale component

### AVG
- Provinciale taken als publieke taak
- Verwerkingsregister
- Functionaris Gegevensbescherming

### Open Data
- Provinciale open data strategie
- data.overheid.nl publicatie
- High Value Datasets

## Gerelateerde skills

- [gemeentelijke-iv](../gemeentelijke-iv/SKILL.md) — Gemeentelijke IV
- [dso-omgevingswet](../dso-omgevingswet/SKILL.md) — Omgevingswet
- [geo-ruimtelijke-iv](../geo-ruimtelijke-iv/SKILL.md) — Geo-data
- [nora-architectuur](../nora-architectuur/SKILL.md) — Architectuur
- [open-data](../open-data/SKILL.md) — Open data
- [mdto-archivering](../mdto-archivering/SKILL.md) — Archivering
- [avg-privacy](../avg-privacy/SKILL.md) — Privacy
- [waterschappen](../waterschappen/SKILL.md) — Waterschappen

## Bronnen

- Interprovinciael Overleg: ipo.nl
- GEMMA: gemmaonline.nl
- Omgevingswet: omgevingswet.overheid.nl
- Waterschappen: waterschappen.nl
