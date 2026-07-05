---
name: geo-ruimtelijke-iv
version: 1.0.0
description: >
  Ruimtelijke IV voor de Nederlandse overheid. BAG, BRK, IMGeo, 3D
  Basisvoorziening, en adressen. Gebruik bij gemeentelijke
  ruimtelijke-ordeningsprojecten, geo-ontwikkeling, of basisregistraties.
triggers:
  keywords:
    - BAG
    - BRK
    - IMGeo
    - 3D
    - basisregistratie
    - geo
    - ruimtelijk
    - adressen
    - gebouwen
    - kadaster
    - WOZ
    - INSPIRE
    - OGC
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# Geo/Ruimtelijke IV

Ruimtelijke informatievoorziening voor de Nederlandse overheid. Dit skill
biedt richtlijnen voor het werken met basisregistraties, geo-standaarden
en ruimtelijke data binnen overheidsorganisaties.

## Wanneer deze skill gebruiken

- Gemeentelijke ruimtelijke ordening
- Basisregistraties (BAG, BRK, WOZ) implementatie
- Geo-API ontwikkeling (OGC API standaarden)
- 3D Basisvoorziening projecten
- INSPIRE compliance
- Data-uitwisseling met kadaster
- Gemeentelijke belastingen (OZB/WOZ koppeling)

## Basisregistraties

### BAG (Basisregistratie Adressen en Gebouwen)

De BAG is de meest gebruikte basisregistratie bij gemeenten:

- **Adressen**: Straatnaam, huisnummer, postcode, woonplaats
- **Gebouwen**: Panden, verblijfsobjecten, standplaatsen, ligplaatsen
- **Woonplaatsen**: Erkende woonplaatsen
- **Openbare ruimten**: Straatnamen, parken, wateren

API's:
- **Haal Centraal BAG API**: v1.5 (actueel), v2.0 (in ontwikkeling)
- **BAG Viewer**: Inzage op bagviewer.kadaster.nl
- **BAG Extract**: Downloaden van BAG-data

Compliance:
- **Wet Bag**: Wet Basisregistratie Adressen en Gebouwen
- **Uitvoeringsregeling**: Besluit en AMvB BAG
- **Kwaliteis**: Verplichte kwaliteitseisen voor gemeenten

### BRK (Basisregistratie Kadaster)

De BRK bevat kadastrale gegevens:

- **Kadastrale grenzen**: Gemeentelijke en kadastrale grenzen
- **Percelen**: Kadastrale percelen
- **Rechten**: Eigendom, erfpacht, beperkte rechten
- **Hypotheken**: Inschrijvingen

API's:
- **Haal Centraal BRK API**: v1.0
- **BRK Download**: Kadastrale kaart
- **Kadaster API**: Kadaster B2B API's

### WOZ (Waardering Onroerende Zaken)

De WOZ is essentieel voor gemeentelijke belastingen:

- **WOZ-waarde**: Taxatiewaarde van onroerende zaken
- **Aanpassingen**: Jaarlijkse waardebepaling
- **Bezwaarschrift**: Procedure voor bezwaar
- **OZB-koppeling**: Input voor Onroerendezaakbelasting

### HR (Handelsregister)

KvK Handelsregister voor bedrijfsgegevens:

- **Rechtspersonen**: BV, NV, stichting, vereniging
- **Vestigingen**: Locaties van bedrijven
- **Functionarissen**: Bestuurders, gemachtigden
- **Insolventies**: Faillissementen, surseéance

## Geo Standaarden

### OGC API

De Open Geospatial Consortium (OGC) standaarden voor geo-API's:

- **OGC API Features**: RESTful feature access
- **OGC API Tiles**: Vector en raster tiles
- **OGC API Maps**: Map rendering
- **OGC API Processes**: Geoprocessing
- **OGC API Records**: Catalogus zoeken
- **OGC API Coverages**: Coverage data
- **OGC API Routes**: Routering
- **OGC API DGGS**: Discrete Global Grid Systems
- **OGC API EDR**: Environmental Data Retrieval
- **OGC API 3D GeoVolumes**: 3D volumes

### INSPIRE

Europese richtlijn voor ruimtelijke data infrastructuur:

- **Metadata**: Conform ISO 19115
- **Data specificaties**: 34 data-thema's
- **Network services**: View, Download, Transformation
- **Spatial data themes**: Adressen, gebouwen, transport, hydrografie
- **Metadata editor**: Nationaal Geo Register

### NEN 3610

Nederlands informatiemodellen voor ruimtelijke data:

- **Basis model**: Kernentiteiten en relaties
- **Sector modellen**: Infrastructuur, water, milieu
- **Uitbreidingen**: Sector-specifieke uitbreidingen
- **MIM (Modellen in Modellen)**: Meta-model voor informatiemodellen

### IMGeo

Informatiemodel Geografie voor grootschalige topografie:

- **Niveaus**: IMGeo+, IMGeo basis
- **Objecten**: Gebouw, weg, spoor, water, terrein, functioneel gebied
- **Topologie**: Topologische regels
- **Kwaliteit**: Actualiteit, volledigheid, positionele nauwkeurigheid

### 3D Basisvoorziening

Nederlandse standaard voor 3D geo-data:

- **CityGML**: 3D stadsmodellen
- **3D Tiles**: Streaming 3D data
- **I3S**: Indexed 3D Scene
- **3D Mesh**: Driedimensionale meshes
- **BIM-GIS integratie**: Building Information Modeling + GIS

## Gemeentelijke Toepassingen

### OZB Berekening

Gemeenten gebruiken WOZ + BAG + BRK voor OZB:

```
WOZ-waarde × heffingspercentage + toeslag = OZB-bedrag
```

### Omgevingswet

Ruimtelijke componenten van de Omgevingswet:

- **Omgevingsplan**: Gemeentelijk ruimtelijk beleid
- **Omgevingsvergunning**: Activiteiten in de fysieke leefomgeving
- **DSO (Digitaal Stelsel Omgevingswet)**: STOP/TPOD, IMOW, STTR, LVBB
- **Omgevingsloket**: Digitale toegang tot omgevingsregels

### Ruimtelijke Ordening

- **Bestemmingsplannen**: Traditioneel (tot 2024)
- **Omgevingsplan**: Vanaf 2024 (Omgevingswet)
- **Projectbesluiten**: Grote projecten
- **Omgevingsvergunningen**: Activiteiten

### Rampenbestrijding

- **Risicokaart**: Overstroming, brand, gevaarlijke stoffen
- **Sleutelgevallen**: Gebouwen met extra risico's
- **Evuatieroutes**: Planning en visualisatie
- **Gemeentelijke Risicobeoordeling**: Proces voor gemeenten

## Data-uitwisseling

### Haal Centraal

Gemeenten krijgen geo-gegevens via Haal Centraal:

- **BAG API**: Adressen en gebouwen
- **BRK API**: Kadastrale gegevens
- **WOZ API**: Waarderingen
- **WMS/WFS**: Kaartlagen

### PDOK (Publieke Dienstverlening op de Kaart)

Nationaal platform voor geo-informatie:
- **PDOK Viewer**: Kaartviewer
- **PDOK Services**: WMS, WFS, WMTS
- **PDOK Download**: Data downloaden
- **PDOK Locatiezoeker**: Adres zoeken

### Nationaal Geo Register

Metadata-register voor ruimtelijke datasets:
- **Zoeken**: Zoeken naar geo-datasets
- **Metadata**: ISO 19115 metadata
- **Services**: OGC service discovery
- **INSPIRE**: INSPIRE-compliant metadata

## Compliance

### Wet- en regelgeving

- **Wet Bag**: Basisregistratie Adressen en Gebouwen
- **Wet WKPB**: Wet waardering onroerende zaken
- **INSPIRE richtlijn**: 2007/2/EG
- **Omgevingswet**: Ruimtelijke componenten
- **Geo-informatiewet**: Wet op de geo-informatie

### Privacy bij Geo-data

- **Locatiegegevens**: Kunnen persoonsgegevens zijn
- **Thuisadressen**: Beschermd onder AVG
- **Cameratoezicht**: ANPR, CCTV
- **Track and trace**: Voertuigvolging

## Gerelateerde skills

- [dso-omgevingswet](../dso-omgevingswet/SKILL.md) — Omgevingswet
- [gemeentelijke-iv](../gemeentelijke-iv/SKILL.md) — Gemeentelijke IV
- [open-data](../open-data/SKILL.md) — Open data publicatie
- [nora-architectuur](../nora-architectuur/SKILL.md) — Architectuur
- [digikoppeling](../digikoppeling/SKILL.md) — Data-uitwisseling
- [zgw-apis](../zgw-apis/SKILL.md) — API standaarden
- [tooi-metadata](../tooi-metadata/SKILL.md) — Metadata
- [eu-interoperability](../eu-interoperability/SKILL.md) — INSPIRE

## Bronnen

- Kadaster: kadaster.nl
- PDOK: pdok.nl
- Nationaal Geo Register: nationaalgeoregister.nl
- Geonovum: geonovum.nl
- INSPIRE: inspire.ec.europa.eu
- Haal Centraal: haalcentraal.nl
- OGC: ogc.org
- NEN 3610: nen.nl
