---
name: gemeentelijke-iv
version: 1.0.0
description: >
  IV voor Nederlandse gemeenten (342+). Dekking van burgerzaken, belastingen,
  APV, Wmo, archivering, ruimtelijke ordening en sociale diensten.
  Gebruik bij gemeentelijke software-ontwikkeling, Common Ground implementatie,
  of gemeentelijke compliance.
triggers:
  keywords:
    - gemeente
    - gemeentelijk
    - burgerzaken
    - OZB
    - APV
    - Wmo
    - Common Ground
    - Open Zaak
    - gemeentelijke belastingen
    - sociale dienst
    - gemeentelijke herindeling
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# Gemeentelijke IV

Informatievoorziening voor de 342+ Nederlandse gemeenten. Dit skill biedt
richtlijnen, standaarden en compliance-patronen specifiek voor gemeentelijke
organisaties.

## Wanneer deze skill gebruiken

- Gemeentelijke software-ontwikkeling
- Common Ground / Open Zaak implementatie
- Gemeentelijke API-ontwikkeling (ZGW standaarden)
- Gemeentelijke compliance (AVG, toegankelijkheid, open data)
- Gemeentelijke archivering en records management
- Intergemeentelijke samenwerking (samenwerkingsverbanden)

## Gemeentelijke IV Domeinen

### 1. Burgerzaken (BRP koppeling)

Gemeenten zijn aangesloten op de Basisregistratie Personen (BRP) via
Haal Centraal / BRP API. Belangrijke aandachtspunten:

- **Rechtmatigheid**: Alleen verwerken voor wettelijke taak (Burgerlijk Wetboek Boek 1)
- **Data minimisation**: Alleen opvragen wat nodig is voor de dienst
- **Bewaartermijnen**: Conform Archiefwet 2021 en gemeentelijke selectielijst
- **Toegankelijkheid**: Digitale dienstverlening conform WCAG 2.2
- **DigiD**: Verplichte authenticatie voor inlogdiensten

Standaarden:
- Haal Centraal BRP Persoon API (v2.1)
- StUF-BG 3.10 (legacy, migratie naar ZGW)
- RSIN + OIN identificatie

### 2. Gemeentelijke Belastingen

Gemeenten heffen:
- **OZB** (Onroerendezaakbelasting) — gekoppeld aan BRK/waardebepaling
- **Afvalstoffenheffing** — verschillend per gemeente
- **Precario** — gebruik openbare ruimte
- **Leges** — voor gemeentelijke diensten

Compliance:
- Wet waardering onroerende zaken (WOZ koppeling)
- Gemeentewet (artikel 223-228: heffingsbevoegdheid)
- AVG bij belastinggegevens (bijzondere persoonsgegevens)
- Toezicht door Algemene Rekenkamer

### 3. APV / Algemene Plaatselijke Verordening

- **Omgevingswet**: Gemeenten hebben een APV onder het Omgevingsloket
- **STOP/TPOD**: Standaard voor omgevingsdocumenten
- **DSO API**: Omgevingsloket API voor inzage en aanvragen
- **Publicatie**: Verplicht via Woo (Wet open overheid)

### 4. Wmo / Jeugdhulp / Participatiewet

- **Wet maatschappelijke ondersteuning (Wmo 2015)**: Gemeentelijke uitvoering
- **Jeugdwet**: Gemeentelijke verantwoordelijkheid jeugdhulp
- **Participatiewet**: Re-integratie (deels gemeentelijk, deels UWV)
- **iWmo/iJw/iEb**: Berichtenstandaarden voor ketenintegratie
- **Suwinet**: Voorzieningen informatienetwerk

### 5. Gemeentelijke Archivering

- **Archiefwet 2021**: Verplichte archiefwetgeving
- **NEN 2082**: Archiefklassering voor gemeenten
- **MDTO**: Metagegevens voor duurzame toegankelijkheid
- **DUTO**: Duurzame toegankelijkheidseisen
- **e-depot**: Digitaal archiefdepot

### 6. Ruimtelijke Ordening

- **Omgevingswet**: Omgevingsplan, omgevingsvergunning
- **DSO (Digitaal Stelsel Omgevingswet)**: TPOD, IMOW, STTR, LVBB
- **BAG**: Basisregistratie Adressen en Gebouwen
- **BRK**: Basisregistratie Kadaster
- **IMGeo**: Informatiemodel Geografie

### 7. Sociale Dienst / Werk en Inkomen

- **Wmo 2015**: Maatschappelijke participatie
- **Participatiewet**: Re-integratie ondersteuning
- **IOAW/IOAZ**: Inkomenstoets arbeidsongeschikten
- **Bijstand**: Algemene bijstand (gemeentelijk beleid)

## Gemeentelijke Architectuur

### GEMMA (Gemeentelijke Variant NORA)

GEMMA is de gemeentelijke referentiearchitectuur:
- **GEMMA Online**: gemmaonline.nl
- **Vijflagenmodel**: Strategie, Organisatief, Informatie, Applicaties, Techniek
- **Koppeling met NORA**: GEMMA implementeert NORA principes op gemeentelijk niveau
- **Gemeentelijke standaarden**: Uitbreiding van NORA met gemeentelijke praktijk

### Common Ground

Common Ground is de gemeentelijke platformstrategie:
- **Open Zaak**: Zaakafhandeling (ZGW API's)
- **Open Formulieren**: Formulieren voor dienstverlening
- **Open Notificaties**: Notificatie-uitwisseling
- **Objecten API / Objecttypen API**: Beheer van objecttypen
- **Referentie-implementatie**: VNG-Realisatie

### Haal Centraal

Gemeenten gebruiken Haal Centraal voor basisregistraties:
- **BRP**: Personen
- **BAG**: Adressen en gebouwen
- **HR**: Handelsregister (KvK)
- **BRK**: Kadaster
- **WOZ**: Waardering onroerende zaken

## Gemeentelijke Compliance

### AVG bij Gemeentelijke Dienstverlening

- **Rechtmatigheid**: Wettelijke taak als grondslag (artikel 6 lid 1 sub e AVG)
- **Privacy by Design**: Verplicht bij nieuwe systemen
- **DPIA**: Verplicht bij hoog-risico verwerking (bijv. cameratoezicht)
- **Functionaris Gegevensbescherming**: Verplicht bij gemeenten
- **Verzoekrechten**: Inzage, correctie, verwijdering, dataportabiliteit

### Toegankelijkheid

- **WCAG 2.2 AA**: Verplicht voor gemeentelijke websites
- **EN 301 549**: Europese toegankelijkheidsstandaard
- **EAA (European Accessibility Act)**: Van toepassing juni 2025
- **Toegankelijkheidsverklaring**: Verplicht op elke site

### Open Data

- **Woo (Wet open overheid)**: Publicatieverplichtingen
- **data.overheid.nl**: DCAT-NL metadata
- **High Value Datasets**: EU verplichting (verkeer, geospatiaal, aardeobservatie, statistiek)
- **Open data licenties**: CC-BY of CC-0

### Woo (Wet open overheid)

- **Publicatieplicht**: Besluiten, documenten, rapporten
- **KOOP**: Kennis- en Openbaarheidspodium Overheid
- **TOOI**: Thesaurus en Ontologie voor Overheidsinformatie
- **Aanpasbaar Woo-beleid**: Gemeentelijk openbaarheidsbeleid

## Intergemeentelijke Samenwerking

Gemeenten werken samen in:
- **Samenwerkingsverbanden**: Gemeenschappelijke regelingen (GR)
- **Regionale samenwerking**: Veiligheidsregio's, netwerkstelsels
- **Shared services**: Gedeelde IT-diensten
- **Gemeentelijke herindeling**: Fusies vereisen datamigratie

## KWIV voor Gemeenten

Gemeentelijke IV-professionals kunnen het KWIV raadplegen:
- **I-leerkaarten**: Competentieprofielen voor IV-beroepen
- **e-CF mapping**: Europese competentieraamwerk
- **Loopbaanpaden**: Van junior naar senior IV-professional
- **FGR alignment**: Functiehuis Rijk als referentie voor gemeentelijke schalen

## Gerelateerde skills

- [zgw-apis](../zgw-apis/SKILL.md) — ZGW API-standaarden voor zaakafhandeling
- [digikoppeling](../digikoppeling/SKILL.md) — Digikoppeling REST/WUS/ebMS2
- [avg-privacy](../avg-privacy/SKILL.md) — AVG/GDPR compliance
- [dpia-assessment](../dpia-assessment/SKILL.md) — DPIA uitvoeren
- [gemma-common-ground](../gemma-common-ground/SKILL.md) — GEMMA en Common Ground
- [dso-omgevingswet](../dso-omgevingswet/SKILL.md) — Omgevingswet implementatie
- [mdto-archivering](../mdto-archivering/SKILL.md) — Gemeentelijke archivering
- [open-data](../open-data/SKILL.md) — Open data publicatie
- [digitoegankelijk](../digitoegankelijk/SKILL.md) — WCAG toegankelijkheid
- [kwiv-loopbaanpaden](../kwiv-loopbaanpaden/SKILL.md) — IV-carrierepaden
- [nora-architectuur](../nora-architectuur/SKILL.md) — NORA principes
- [sociaal-domein](../sociaal-domein/SKILL.md) — Wmo/Jeugdhulp berichtenstandaarden
- [geo-ruimtelijke-iv](../geo-ruimtelijke-iv/SKILL.md) — BAG, BRK, IMGeo

## Bronnen

- GEMMA Online: gemmaonline.nl
- Common Ground: commonground.nl
- Haal Centraal: haalcentraal.nl
- VNG Realisatie: vngrealisatie.nl
- Archiefwet 2021: wetten.overheid.nl
- Omgevingswet: omgevingswet.overheid.nl
- Woo: wetten.overheid.nl
- Wmo 2015: wetten.overheid.nl
