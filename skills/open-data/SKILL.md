---
name: open-data
description: >-
  Helpt bij het publiceren en gebruiken van open data conform Nederlandse
  en Europese standaarden, inclusief DCAT-AP-NL, data.overheid.nl,
  high-value datasets en de Wet hergebruik overheidsinformatie (Who).
  Gebruik deze skill wanneer de gebruiker vraagt over 'open data',
  'DCAT', 'DCAT-AP', 'DCAT-AP-NL', 'data.overheid.nl',
  'dataset publiceren', 'publish dataset', 'open data overheid',
  'government open data', 'high-value dataset', 'HVD',
  'Wet hergebruik overheidsinformatie', 'Who',
  'Open Data Richtlijn', 'Open Data Directive',
  'CKAN', 'dataportaal', 'data portal', 'catalogus',
  'metadata dataset', 'linked data overheid', 'SPARQL overheid',
  'API dataset', 'bulk download', 'machine-leesbaar',
  'machine-readable', 'CSV overheid', 'JSON overheid',
  'RDF overheid', 'open data licentie', 'CC0', 'public domain',
  'hergebruik data', 'data reuse', 'FAIR data',
  'dataregister', 'data inventory',
  of wanneer de gebruiker data wil publiceren of gebruiken via
  Nederlandse overheidsdata-platformen.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(curl *)
  - Bash(gh api *)
  - Bash(gh search *)
---

# Open Data — DCAT-AP-NL & data.overheid.nl

Publiceer en gebruik open overheidsdata conform Nederlandse en Europese standaarden.

Bron: [data.overheid.nl](https://data.overheid.nl/) | [DCAT-AP-NL](https://docs.geostandaarden.nl/dcat/dcat-ap-nl/) | [Open Data Richtlijn](https://eur-lex.europa.eu/eli/dir/2019/1024/oj)

## Wettelijk kader

| Aspect | Detail |
|--------|--------|
| **EU-richtlijn** | Open Data Richtlijn (2019/1024) — vervangt PSI-richtlijn |
| **Nationale wet** | Wet hergebruik overheidsinformatie (Who) |
| **HVD-verordening** | Uitvoeringsverordening High-Value Datasets (2023/138) — verplicht sinds juni 2024 |
| **Standaard** | DCAT-AP-NL 2.0 (gebaseerd op DCAT-AP 2.1.1 en W3C DCAT 3) |
| **Platform** | data.overheid.nl — nationaal open data portaal |
| **Europees** | data.europa.eu — Europees data portaal (harvested uit nationale portalen) |
| **Toezicht** | Ministerie van BZK |

### Kernverplichtingen

| Verplichting | Detail |
|-------------|--------|
| **Hergebruik** | Overheidsinformatie is in beginsel herbruikbaar (tenzij uitzondering) |
| **Machine-leesbaar** | Data in open, machine-leesbare formaten beschikbaar stellen |
| **Geen kosten** | Gratis of maximaal marginale kosten |
| **Geen discriminatie** | Gelijke voorwaarden voor iedereen |
| **API-verplichting** | Dynamische data via API beschikbaar stellen |
| **HVD** | 6 categorieën high-value datasets verplicht gratis als open data via API + bulk |

## High-Value Datasets (HVD)

Sinds juni 2024 verplicht als open data met API + bulkdownload:

| Categorie | Voorbeelden | Houder(s) |
|-----------|------------|-----------|
| **Geospatial** | Topografie, adressen, gebouwen, kadaster, hoogte | Kadaster, BAG |
| **Aardobservatie en milieu** | Lucht- en waterkwaliteit, emissies | RIVM, Rijkswaterstaat |
| **Meteorologie** | Weergegevens, klimaatdata | KNMI |
| **Statistiek** | CBS StatLine datasets | CBS |
| **Bedrijven en eigendom** | Handelsregister, KvK-gegevens | KVK |
| **Mobiliteit** | Verkeerstellingen, OV-data | NDW, OVapi |

### HVD-vereisten

| Eis | Detail |
|-----|--------|
| **Formaat** | Machine-leesbaar, open standaard |
| **API** | Beschikbaar via API (REST, OGC API, SPARQL) |
| **Bulkdownload** | Volledige dataset downloadbaar |
| **Licentie** | CC0 of CC BY 4.0 (geen restrictievere licentie) |
| **Metadata** | DCAT-AP catalogus-entry |
| **Kosten** | Gratis |

## DCAT-AP-NL — metadatastandaard

DCAT-AP-NL is het Nederlandse toepassingsprofiel van DCAT-AP (W3C/EU) voor het beschrijven van datasets.

### Kernklassen

| Klasse | Beschrijving | Verplicht |
|--------|-------------|-----------|
| **dcat:Catalog** | Catalogus (data.overheid.nl) | Ja |
| **dcat:Dataset** | Dataset (logische eenheid van data) | Ja |
| **dcat:Distribution** | Distributie (specifiek formaat/API) | Ja |
| **dcat:DataService** | API-service | Aanbevolen |
| **foaf:Agent** | Uitgever/beheerder | Ja |
| **vcard:Kind** | Contactgegevens | Aanbevolen |

### Verplichte metadata — Dataset

| Eigenschap | Predikaat | Kardinaliteit | Voorbeeld |
|-----------|-----------|--------------|-----------|
| **Titel** | `dct:title` | 1..* | "Adressen en gebouwen (BAG)" |
| **Beschrijving** | `dct:description` | 1..* | "Alle adressen en gebouwen in Nederland" |
| **Uitgever** | `dct:publisher` | 1..1 | Kadaster |
| **Thema** | `dcat:theme` | 1..* | `http://standaarden.overheid.nl/owms/terms/Ruimte_en_infrastructuur` |
| **Trefwoord** | `dcat:keyword` | 0..* | "adressen", "gebouwen", "BAG" |
| **Taal** | `dct:language` | 1..* | `http://publications.europa.eu/resource/authority/language/NLD` |
| **Contactpunt** | `dcat:contactPoint` | 1..* | Contactpersoon of helpdesk |
| **Licentie** | `dct:license` | 1..1 (op Distribution) | CC0, CC BY 4.0 |
| **Wijzigingsdatum** | `dct:modified` | 0..1 | "2026-02-01" |
| **Frequentie** | `dct:accrualPeriodicity` | 0..1 | Dagelijks, wekelijks, maandelijks |

### DCAT-AP-NL in JSON-LD

```json
{
  "@context": {
    "dcat": "http://www.w3.org/ns/dcat#",
    "dct": "http://purl.org/dc/terms/",
    "foaf": "http://xmlns.com/foaf/0.1/",
    "overheid": "http://standaarden.overheid.nl/owms/terms/"
  },
  "@type": "dcat:Dataset",
  "dct:title": "Basisregistratie Adressen en Gebouwen (BAG)",
  "dct:description": "Alle adressen, verblijfsobjecten, standplaatsen, ligplaatsen en panden in Nederland.",
  "dct:publisher": {
    "@type": "foaf:Agent",
    "foaf:name": "Kadaster"
  },
  "dcat:theme": [
    "http://standaarden.overheid.nl/owms/terms/Ruimte_en_infrastructuur"
  ],
  "dcat:keyword": ["adressen", "gebouwen", "BAG", "basisregistratie"],
  "dct:language": "http://publications.europa.eu/resource/authority/language/NLD",
  "dct:accrualPeriodicity": "http://publications.europa.eu/resource/authority/frequency/DAILY",
  "dct:modified": "2026-02-01",
  "dcat:distribution": [
    {
      "@type": "dcat:Distribution",
      "dct:title": "BAG API",
      "dcat:accessURL": "https://api.bag.kadaster.nl/lvbag/individuelebevragingen/v2",
      "dct:format": "application/json",
      "dct:license": "https://creativecommons.org/publicdomain/zero/1.0/"
    },
    {
      "@type": "dcat:Distribution",
      "dct:title": "BAG Extract (bulkdownload)",
      "dcat:downloadURL": "https://service.pdok.nl/lv/bag/atom/downloads/lvbag-extract-nl.zip",
      "dct:format": "application/xml",
      "dct:license": "https://creativecommons.org/publicdomain/zero/1.0/"
    }
  ]
}
```

### DCAT-AP-NL in RDF/Turtle

```turtle
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix dct:  <http://purl.org/dc/terms/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<https://data.overheid.nl/dataset/bag>
  a dcat:Dataset ;
  dct:title "Basisregistratie Adressen en Gebouwen (BAG)"@nl ;
  dct:description "Alle adressen en gebouwen in Nederland."@nl ;
  dct:publisher <https://identifier.overheid.nl/tooi/id/organisatie/kadaster> ;
  dcat:theme <http://standaarden.overheid.nl/owms/terms/Ruimte_en_infrastructuur> ;
  dcat:keyword "adressen"@nl, "gebouwen"@nl, "BAG"@nl ;
  dct:language <http://publications.europa.eu/resource/authority/language/NLD> ;
  dct:accrualPeriodicity <http://publications.europa.eu/resource/authority/frequency/DAILY> ;
  dcat:distribution <https://data.overheid.nl/dataset/bag/api> .

<https://data.overheid.nl/dataset/bag/api>
  a dcat:Distribution ;
  dct:title "BAG API"@nl ;
  dcat:accessURL <https://api.bag.kadaster.nl/lvbag/individuelebevragingen/v2> ;
  dct:format <http://publications.europa.eu/resource/authority/file-type/JSON> ;
  dct:license <https://creativecommons.org/publicdomain/zero/1.0/> .
```

## data.overheid.nl — Registratie

### Metadata aanleveren via API

```http
POST /api/3/action/package_create HTTP/1.1
Host: data.overheid.nl
Authorization: Api-Key {api-key}
Content-Type: application/json

{
  "name": "mijn-dataset-2026",
  "title": "Openingstijden overheidsloketten",
  "notes": "Actuele openingstijden van alle overheidsloketten in Nederland.",
  "owner_org": "gemeente-amsterdam",
  "license_id": "cc-zero",
  "tags": [
    {"name": "openingstijden"},
    {"name": "loketten"},
    {"name": "dienstverlening"}
  ],
  "resources": [
    {
      "name": "Openingstijden API",
      "url": "https://api.gemeente.nl/openingstijden/v1",
      "format": "JSON",
      "description": "REST API conform NL API Design Rules"
    },
    {
      "name": "Openingstijden CSV",
      "url": "https://data.gemeente.nl/downloads/openingstijden.csv",
      "format": "CSV"
    }
  ]
}
```

### Harvesting

data.overheid.nl kan automatisch metadata harvesten uit lokale CKAN-instanties of DCAT-endpoints:

| Methode | Protocol | Beschrijving |
|---------|----------|-------------|
| **DCAT-AP harvest** | HTTP/JSON-LD | Endpoint levert DCAT-AP-NL metadata |
| **CKAN harvest** | CKAN API | Lokale CKAN wordt geharvest |
| **CSW harvest** | OGC CSW | Geo-metadata (ISO 19115) |

## Formaten en licenties

### Aanbevolen formaten (5-sterrenmodel Tim Berners-Lee)

| Sterren | Formaat | Voorbeeld | Open? |
|---------|---------|-----------|-------|
| ★ | Beschikbaar op het web | PDF | Nee |
| ★★ | Machine-leesbaar | Excel (XLS) | Nee |
| ★★★ | Open formaat | **CSV, JSON, XML, GeoJSON** | **Ja** |
| ★★★★ | Linked Data (URI's) | **RDF, JSON-LD, Turtle** | **Ja** |
| ★★★★★ | Linked Open Data | **SPARQL endpoint, linked datasets** | **Ja** |

**Minimaal**: ★★★ (open formaat). HVD vereist API + bulkdownload.

### Licenties

| Licentie | Vereisten | Gebruik |
|----------|----------|---------|
| **CC0 (Public Domain)** | Geen restricties | **Aanbevolen** voor overheidsdata |
| **CC BY 4.0** | Naamsvermelding vereist | Acceptabel voor HVD |
| **CC BY-SA 4.0** | Naamsvermelding + gelijk delen | **Niet toegestaan** voor HVD |
| **Publiek domein** | Geen restricties | Gelijk aan CC0 |

## FAIR-principes

| Principe | Beschrijving | Implementatie |
|---------|-------------|---------------|
| **Findable** | Data is vindbaar via metadata | DCAT-AP-NL op data.overheid.nl; persistente URI's |
| **Accessible** | Data is opvraagbaar via standaard protocol | HTTPS, API's, bulkdownload |
| **Interoperable** | Data gebruikt open standaarden | JSON, CSV, RDF; gestandaardiseerde vocabulaires |
| **Reusable** | Data is herbruikbaar met duidelijke licentie | CC0/CC BY; rijke metadata; provenance |

## API voor open data

```python
# Voorbeeld: dataset publiceren met Python
import httpx

CKAN_URL = "https://data.overheid.nl/api/3/action"
API_KEY = "mijn-api-key"

async def publiceer_dataset(titel: str, beschrijving: str, resources: list[dict]):
    """Publiceer een dataset op data.overheid.nl."""
    async with httpx.AsyncClient() as client:
        response = await client.post(
            f"{CKAN_URL}/package_create",
            json={
                "name": titel.lower().replace(" ", "-"),
                "title": titel,
                "notes": beschrijving,
                "license_id": "cc-zero",
                "resources": resources,
            },
            headers={"Authorization": API_KEY}
        )
        return response.json()
```

## Implementatie-checklist

- [ ] **Dataset geidentificeerd**: welke data kan als open data worden gepubliceerd?
- [ ] **Privacycheck**: geen persoonsgegevens in de dataset (of geanonimiseerd)
- [ ] **Formaat**: data beschikbaar in open, machine-leesbaar formaat (CSV, JSON, GeoJSON)
- [ ] **API**: dynamische data ontsloten via REST API (NL API Design Rules)
- [ ] **Bulkdownload**: volledige dataset downloadbaar
- [ ] **Licentie**: CC0 of CC BY 4.0 toegepast
- [ ] **DCAT-AP-NL metadata**: alle verplichte velden ingevuld
- [ ] **data.overheid.nl**: dataset geregistreerd op het nationale portaal
- [ ] **HVD-check**: valt de dataset onder een HVD-categorie? Zo ja: verplicht API + bulk + gratis
- [ ] **Kwaliteit**: data gevalideerd op compleetheid, juistheid, actualiteit
- [ ] **Updatefrequentie**: schema voor regelmatige updates gedefinieerd en geautomatiseerd
- [ ] **Documentatie**: databeschrijving, kolombeschrijvingen, licentie duidelijk vermeld

## Meer informatie

- [data.overheid.nl](https://data.overheid.nl/) — nationaal open data portaal
- [DCAT-AP-NL](https://docs.geostandaarden.nl/dcat/dcat-ap-nl/) — metadatastandaard
- [Open Data Richtlijn](https://eur-lex.europa.eu/eli/dir/2019/1024/oj) | [HVD-verordening](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)
- [data.europa.eu](https://data.europa.eu/) — Europees data portaal
- [FAIR principes](https://www.go-fair.org/fair-principles/)
- [5-sterrenmodel Open Data](https://5stardata.info/nl/)
