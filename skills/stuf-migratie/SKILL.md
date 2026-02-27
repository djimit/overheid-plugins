---
name: stuf-migratie
description: >-
  Helpt bij het migreren van StUF-BG/StUF-ZKN (Standaard Uitwisseling
  Formaat) naar moderne ZGW API's en Common Ground architectuur.
  Biedt mapping-tabellen, coexistentiepatronen, migratiestrategieen
  en codevoorbeelden voor de overgang van SOAP/XML naar REST/JSON.
  Gebruik deze skill wanneer de gebruiker vraagt over
  'StUF', 'StUF-BG', 'StUF-ZKN', 'StUF migratie', 'StUF migration',
  'StUF naar ZGW', 'StUF to ZGW', 'StUF naar API', 'StUF to API',
  'SOAP naar REST overheid', 'SOAP to REST government',
  'XML naar JSON overheid', 'legacy migratie overheid',
  'legacy migration government', 'StUF-koppelvlak',
  'BG-koppelvlak', 'ZKN-koppelvlak',
  'Sectormodel BG', 'Sectormodel ZKN',
  'StUF vertaallaag', 'StUF translator',
  'StUF proxy', 'StUF adapter',
  'Kennismodel StUF', 'RSGB', 'RGBZ',
  'StUF coexistentie', 'StUF coexistence',
  'GBA-V StUF', 'BRP StUF',
  of wanneer de gebruiker een StUF-koppeling wil moderniseren,
  migreren naar ZGW API's of een coexistentiestrategie wil opzetten.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# StUF-migratie — Van StUF-BG/ZKN naar ZGW API's

Migreer van legacy StUF SOAP/XML-koppelingen naar moderne ZGW REST/JSON API's conform Common Ground.

Bron: [VNG Standaarden](https://vng.nl/rubrieken/onderwerpen/standaarden) | [ZGW API's](https://vng-realisatie.github.io/gemma-zaken/) | [Common Ground](https://commonground.nl/)

## Overzicht StUF-standaarden

| Standaard | Naam | Scope | Status |
|-----------|------|-------|--------|
| **StUF** | Standaard Uitwisseling Formaat | Basisprotocol voor XML-berichtenverkeer | Legacy — uitfasering |
| **StUF-BG** | Sectormodel Basisgegevens | Personen, adressen, panden (RSGB) | Legacy — vervangen door BRP/BAG API |
| **StUF-ZKN** | Sectormodel Zaken | Zaken, documenten, besluiten (RGBZ) | Legacy — vervangen door ZGW API's |
| **StUF-EF** | Sectormodel e-Formulieren | Formuliergegevens | Legacy — vervangen door Open Formulieren |
| **StUF-GEO** | Sectormodel Geo | Geografische gegevens | Legacy — vervangen door BAG/BGT API |

### StUF-berichtstructuur

```xml
<!-- StUF-BG: opvragen persoon (Lv01) -->
<soapenv:Envelope
    xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
    xmlns:stuf="http://www.egem.nl/StUF/StUF0301"
    xmlns:bg="http://www.egem.nl/StUF/sector/bg/0310">
  <soapenv:Header/>
  <soapenv:Body>
    <bg:npsLv01>
      <stuf:stuurgegevens>
        <stuf:berichtcode>Lv01</stuf:berichtcode>
        <stuf:zender>
          <stuf:organisatie>0363</stuf:organisatie>
          <stuf:applicatie>ZaakApp</stuf:applicatie>
        </stuf:zender>
        <stuf:ontvanger>
          <stuf:organisatie>0363</stuf:organisatie>
          <stuf:applicatie>BRP</stuf:applicatie>
        </stuf:ontvanger>
        <stuf:referentienummer>uuid-1234</stuf:referentienummer>
        <stuf:tijdstipBericht>20260227120000</stuf:tijdstipBericht>
      </stuf:stuurgegevens>
      <stuf:parameters>
        <stuf:sortering>1</stuf:sortering>
        <stuf:indicatorVervolgvraag>false</stuf:indicatorVervolgvraag>
      </stuf:parameters>
      <stuf:gelijk>
        <bg:bsn>123456789</bg:bsn>
      </stuf:gelijk>
      <stuf:scope>
        <bg:object stuf:entiteittype="NPS">
          <bg:geslachtsnaam stuf:noValue="geenWaarde"/>
          <bg:voorvoegselGeslachtsnaam stuf:noValue="geenWaarde"/>
          <bg:voornamen stuf:noValue="geenWaarde"/>
          <bg:geboortedatum stuf:noValue="geenWaarde"/>
          <bg:verblijfsadres>
            <bg:aoa.identificatie stuf:noValue="geenWaarde"/>
          </bg:verblijfsadres>
        </bg:object>
      </stuf:scope>
    </bg:npsLv01>
  </soapenv:Body>
</soapenv:Envelope>
```

## Migratiepad: StUF naar ZGW/Haal Centraal

### Informatiemodellen

| Legacy model | Opvolger | Verschil |
|-------------|---------|----------|
| **RSGB** (Referentiemodel Stelsel Gemeentelijke Basisgegevens) | **BRP API / Haal Centraal** | Van XML-objecten naar REST/JSON resources |
| **RGBZ** (Referentiemodel Gemeentelijke Zaken) | **ZGW API's** (Zaken, Documenten, Catalogi, Besluiten) | Van SOAP-berichten naar RESTful API's |
| **StUF-kennismodel** | **API-specificaties (OAS 3.x)** | Van XSD-schema's naar OpenAPI Specifications |

### Berichttypen mapping

| StUF-berichttype | Betekenis | ZGW/REST equivalent |
|-----------------|-----------|-------------------|
| **Lv01** | Vrij bericht (opvragen) | `GET /resource?filter=waarde` |
| **La01** | Antwoord op Lv01 | Response body (JSON) |
| **Lk01** | Opvragen op sleutel | `GET /resource/{uuid}` |
| **Lk02** | Antwoord op Lk01 | Response body (JSON) |
| **Di01** | Mutatiebericht toevoegen | `POST /resource` |
| **Di02** | Antwoord op Di01 | `201 Created` + Location header |
| **Du01** | Mutatiebericht wijzigen | `PUT /resource/{uuid}` of `PATCH` |
| **Du02** | Antwoord op Du01 | `200 OK` + updated resource |
| **Fo01** | Foutbericht | `4xx/5xx` + Problem JSON (RFC 9457) |
| **Bv03** | Kennisgeving (asynchroon) | Notificatie via Notificaties API |

### Velden mapping StUF-BG naar Haal Centraal BRP

| StUF-BG veld | XPath | Haal Centraal BRP | JSON path |
|-------------|-------|-------------------|-----------|
| `bsn` | `bg:bsn` | `burgerservicenummer` | `$.burgerservicenummer` |
| `geslachtsnaam` | `bg:geslachtsnaam` | `naam.geslachtsnaam` | `$.naam.geslachtsnaam` |
| `voorvoegsel` | `bg:voorvoegselGeslachtsnaam` | `naam.voorvoegsel` | `$.naam.voorvoegsel` |
| `voornamen` | `bg:voornamen` | `naam.voornamen` | `$.naam.voornamen` |
| `geboortedatum` | `bg:geboortedatum` | `geboorte.datum` | `$.geboorte.datum` |
| `postcode` | `bg:aoa.postcode` | `verblijfplaats.postcode` | `$.verblijfplaats.postcode` |
| `huisnummer` | `bg:aoa.huisnummer` | `verblijfplaats.huisnummer` | `$.verblijfplaats.huisnummer` |
| `woonplaatsnaam` | `bg:wpl.woonplaatsNaam` | `verblijfplaats.woonplaats` | `$.verblijfplaats.woonplaats` |

### Velden mapping StUF-ZKN naar ZGW Zaken API

| StUF-ZKN veld | XPath | ZGW Zaken API | JSON path |
|--------------|-------|---------------|-----------|
| `identificatie` | `zkn:identificatie` | `identificatie` | `$.identificatie` |
| `omschrijving` | `zkn:omschrijving` | `omschrijving` | `$.omschrijving` |
| `startdatum` | `zkn:startdatum` | `startdatum` | `$.startdatum` |
| `einddatumGepland` | `zkn:einddatumGepland` | `einddatumGepland` | `$.einddatumGepland` |
| `zaaktype` | `zkn:isVan` | `zaaktype` | `$.zaaktype` (URL) |
| `status` | `zkn:heeftAlsDeelzaak` | `status` | `$.status` (URL) |
| `resultaat` | `zkn:resultaat` | `resultaat` | `$.resultaat` (URL) |
| `verantwoordelijke` | `zkn:verantwoordelijkeOrganisatie` | `verantwoordelijkeOrganisatie` | `$.verantwoordelijkeOrganisatie` |

## Migratiestrategieen

### Strategie 1: Strangler Fig (aanbevolen)

```
┌─────────────────────────────────────────────────┐
│                   API Gateway                     │
│                                                   │
│  Inkomend verzoek                                │
│       │                                           │
│       ├── Nieuwe zaaktypen ──→ ZGW API's          │
│       │                                           │
│       └── Legacy zaaktypen ──→ StUF Adapter ──→   │
│                                  StUF Backend     │
└─────────────────────────────────────────────────┘

Fase 1: Gateway routeert ALLES naar StUF
Fase 2: Nieuwe zaaktypen naar ZGW; rest naar StUF
Fase 3: Migreer bestaande zaaktypen een voor een
Fase 4: StUF volledig uitgefaseerd
```

### Strategie 2: Anti-Corruption Layer

```
┌──────────┐     ┌───────────────────┐     ┌──────────┐
│  Nieuwe  │     │  Anti-Corruption  │     │  Legacy  │
│  ZGW     │────→│  Layer (ACL)      │────→│  StUF    │
│  Client  │     │                   │     │  Backend │
│          │←────│  REST→SOAP        │←────│          │
│          │     │  JSON→XML         │     │          │
│          │     │  Mapping          │     │          │
└──────────┘     └───────────────────┘     └──────────┘
```

### Strategie 3: Dual Write (tijdelijk)

```
┌──────────┐     ┌──────────────────┐
│  Client  │────→│  Orchestrator    │
│          │     │                  │
│          │     │  ├── POST ZGW ───│──→ ZGW API
│          │     │  │               │
│          │     │  └── Di01 StUF ──│──→ StUF Backend
│          │     │                  │
│          │     │  Sync check      │
└──────────┘     └──────────────────┘

LET OP: Dual write introduceert consistentierisico's.
Gebruik alleen als tijdelijke overbrugging.
```

## Vertaallaag implementatie

### Python StUF-naar-ZGW adapter

```python
"""StUF-naar-ZGW vertaallaag (Anti-Corruption Layer)."""

from dataclasses import dataclass
from datetime import date, datetime
from typing import Any
import xml.etree.ElementTree as ET

import httpx

# Namespaces voor StUF-BG/ZKN parsing
NS = {
    "soapenv": "http://schemas.xmlsoap.org/soap/envelope/",
    "stuf": "http://www.egem.nl/StUF/StUF0301",
    "bg": "http://www.egem.nl/StUF/sector/bg/0310",
    "zkn": "http://www.egem.nl/StUF/sector/zkn/0310",
}


@dataclass
class StufBericht:
    """Geparsed StUF-bericht."""

    berichtcode: str
    zender_organisatie: str
    zender_applicatie: str
    ontvanger_organisatie: str
    ontvanger_applicatie: str
    referentienummer: str
    tijdstip: str
    inhoud: dict[str, Any]


def parse_stuf_envelope(xml_bytes: bytes) -> StufBericht:
    """Parse een StUF SOAP-envelope naar een StufBericht."""
    root = ET.fromstring(xml_bytes)
    body = root.find(".//soapenv:Body", NS)
    # Eerste element in Body is het StUF-bericht
    bericht_elem = list(body)[0]

    stuur = bericht_elem.find(".//stuf:stuurgegevens", NS)
    return StufBericht(
        berichtcode=stuur.findtext("stuf:berichtcode", "", NS),
        zender_organisatie=stuur.findtext("stuf:zender/stuf:organisatie", "", NS),
        zender_applicatie=stuur.findtext("stuf:zender/stuf:applicatie", "", NS),
        ontvanger_organisatie=stuur.findtext("stuf:ontvanger/stuf:organisatie", "", NS),
        ontvanger_applicatie=stuur.findtext("stuf:ontvanger/stuf:applicatie", "", NS),
        referentienummer=stuur.findtext("stuf:referentienummer", "", NS),
        tijdstip=stuur.findtext("stuf:tijdstipBericht", "", NS),
        inhoud=_extract_inhoud(bericht_elem),
    )


def _extract_inhoud(bericht_elem: ET.Element) -> dict[str, Any]:
    """Extraheer de inhoudelijke data uit het StUF-bericht."""
    # Zoek gelijk/scope elementen voor zoekvragen
    gelijk = bericht_elem.find(".//stuf:gelijk", NS)
    if gelijk is not None:
        return {child.tag.split("}")[-1]: child.text for child in gelijk}

    # Zoek object elementen voor mutaties
    obj = bericht_elem.find(".//*[@stuf:entiteittype]", NS)
    if obj is not None:
        return {child.tag.split("}")[-1]: child.text for child in obj if child.text}

    return {}


class StufNaarZgwAdapter:
    """Vertaalt StUF-BG/ZKN-berichten naar ZGW API-calls."""

    # Mapping StUF-BG velden naar Haal Centraal BRP paden
    BG_NAAR_BRP: dict[str, str] = {
        "bsn": "burgerservicenummer",
        "geslachtsnaam": "naam.geslachtsnaam",
        "voorvoegselGeslachtsnaam": "naam.voorvoegsel",
        "voornamen": "naam.voornamen",
        "geboortedatum": "geboorte.datum",
    }

    # Mapping StUF-ZKN velden naar ZGW Zaken API
    ZKN_NAAR_ZGW: dict[str, str] = {
        "identificatie": "identificatie",
        "omschrijving": "omschrijving",
        "startdatum": "startdatum",
        "einddatumGepland": "einddatumGepland",
        "registratiedatum": "registratiedatum",
    }

    def __init__(self, zgw_base_url: str, brp_base_url: str, api_key: str):
        self.zgw_base_url = zgw_base_url.rstrip("/")
        self.brp_base_url = brp_base_url.rstrip("/")
        self.client = httpx.Client(
            headers={
                "Authorization": f"Bearer {api_key}",
                "Content-Type": "application/json",
                "Accept": "application/json",
            }
        )

    def vertaal_lv01_bg(self, bericht: StufBericht) -> dict:
        """Vertaal StUF-BG Lv01 (opvragen persoon) naar BRP API call."""
        bsn = bericht.inhoud.get("bsn")
        if not bsn:
            raise ValueError("BSN ontbreekt in Lv01-bericht")

        response = self.client.get(
            f"{self.brp_base_url}/ingeschrevenpersonen/{bsn}",
            params={"fields": ",".join(self.BG_NAAR_BRP.values())},
        )
        response.raise_for_status()
        return response.json()

    def vertaal_di01_zkn(self, bericht: StufBericht) -> dict:
        """Vertaal StUF-ZKN Di01 (aanmaken zaak) naar ZGW Zaken API POST."""
        zgw_data = {}
        for stuf_veld, zgw_veld in self.ZKN_NAAR_ZGW.items():
            if stuf_veld in bericht.inhoud:
                zgw_data[zgw_veld] = bericht.inhoud[stuf_veld]

        # Datumvelden converteren van StUF-formaat (YYYYMMDD) naar ISO 8601
        for datum_veld in ("startdatum", "einddatumGepland", "registratiedatum"):
            if datum_veld in zgw_data and len(zgw_data[datum_veld]) == 8:
                d = zgw_data[datum_veld]
                zgw_data[datum_veld] = f"{d[:4]}-{d[4:6]}-{d[6:8]}"

        response = self.client.post(
            f"{self.zgw_base_url}/zaken/api/v1/zaken",
            json=zgw_data,
        )
        response.raise_for_status()
        return response.json()

    def vertaal_bericht(self, xml_bytes: bytes) -> dict:
        """Routeer een StUF-bericht naar de juiste ZGW API."""
        bericht = parse_stuf_envelope(xml_bytes)

        handlers = {
            "Lv01": self._handle_lv01,
            "Lk01": self._handle_lk01,
            "Di01": self._handle_di01,
            "Du01": self._handle_du01,
        }

        handler = handlers.get(bericht.berichtcode)
        if not handler:
            raise NotImplementedError(
                f"Berichtcode {bericht.berichtcode} wordt niet ondersteund"
            )

        return handler(bericht)

    def _handle_lv01(self, bericht: StufBericht) -> dict:
        return self.vertaal_lv01_bg(bericht)

    def _handle_lk01(self, bericht: StufBericht) -> dict:
        return self.vertaal_lv01_bg(bericht)

    def _handle_di01(self, bericht: StufBericht) -> dict:
        return self.vertaal_di01_zkn(bericht)

    def _handle_du01(self, bericht: StufBericht) -> dict:
        uuid = bericht.inhoud.get("identificatie")
        if not uuid:
            raise ValueError("Identificatie ontbreekt in Du01-bericht")

        zgw_data = {}
        for stuf_veld, zgw_veld in self.ZKN_NAAR_ZGW.items():
            if stuf_veld in bericht.inhoud:
                zgw_data[zgw_veld] = bericht.inhoud[stuf_veld]

        response = self.client.patch(
            f"{self.zgw_base_url}/zaken/api/v1/zaken/{uuid}",
            json=zgw_data,
        )
        response.raise_for_status()
        return response.json()
```

### Django middleware voor coexistentie

```python
"""Django middleware: routeer StUF SOAP en REST naast elkaar."""

from django.http import HttpRequest, HttpResponse

from .adapter import StufNaarZgwAdapter


class StufCoexistentieMiddleware:
    """Detecteert StUF SOAP-verzoeken en routeert ze naar de ZGW adapter."""

    SOAP_CONTENT_TYPES = (
        "text/xml",
        "application/soap+xml",
    )

    def __init__(self, get_response):
        self.get_response = get_response
        self.adapter = StufNaarZgwAdapter(
            zgw_base_url="https://zgw.gemeente.nl",
            brp_base_url="https://brp.gemeente.nl",
            api_key="configured-via-env",
        )

    def __call__(self, request: HttpRequest) -> HttpResponse:
        content_type = request.content_type or ""

        # Als het een SOAP-verzoek is, vertaal naar ZGW
        if any(ct in content_type for ct in self.SOAP_CONTENT_TYPES):
            return self._handle_stuf(request)

        # Anders: normaal REST-verzoek
        return self.get_response(request)

    def _handle_stuf(self, request: HttpRequest) -> HttpResponse:
        """Vertaal StUF SOAP-verzoek naar ZGW API-call."""
        try:
            result = self.adapter.vertaal_bericht(request.body)
            return HttpResponse(
                content=self._build_soap_response(result),
                content_type="text/xml",
                status=200,
            )
        except NotImplementedError as e:
            return HttpResponse(
                content=self._build_soap_fault(str(e)),
                content_type="text/xml",
                status=500,
            )

    def _build_soap_response(self, data: dict) -> str:
        """Bouw een minimale SOAP-response voor legacy clients."""
        # In productie: volledig StUF-antwoordbericht genereren
        return f"""<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
  <soapenv:Body>
    <response>{data}</response>
  </soapenv:Body>
</soapenv:Envelope>"""

    def _build_soap_fault(self, message: str) -> str:
        return f"""<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
  <soapenv:Body>
    <soapenv:Fault>
      <faultcode>soapenv:Server</faultcode>
      <faultstring>{message}</faultstring>
    </soapenv:Fault>
  </soapenv:Body>
</soapenv:Envelope>"""
```

## Datamigratie

### Zaak-migratie script

```python
"""Migreer zaken van StUF-ZKN backend naar ZGW Zaken API."""

import logging
from datetime import datetime

import httpx
from lxml import etree

logger = logging.getLogger(__name__)

NS = {
    "soapenv": "http://schemas.xmlsoap.org/soap/envelope/",
    "stuf": "http://www.egem.nl/StUF/StUF0301",
    "zkn": "http://www.egem.nl/StUF/sector/zkn/0310",
}

ZAAKTYPE_MAPPING = {
    # StUF zaaktype-identificatie → ZGW zaaktype URL
    "B0100": "https://catalogi.gemeente.nl/api/v1/zaaktypen/uuid-b0100",
    "B0200": "https://catalogi.gemeente.nl/api/v1/zaaktypen/uuid-b0200",
    "B0300": "https://catalogi.gemeente.nl/api/v1/zaaktypen/uuid-b0300",
}


def migreer_zaken(
    stuf_endpoint: str,
    zgw_base_url: str,
    api_key: str,
    zaaktype_stuf: str,
    startdatum_vanaf: str,
    batch_size: int = 100,
) -> dict:
    """
    Migreer zaken van StUF-ZKN naar ZGW Zaken API.

    Args:
        stuf_endpoint: URL van het StUF-ZKN SOAP-endpoint
        zgw_base_url: Basis-URL van de ZGW API's
        api_key: API-sleutel voor ZGW
        zaaktype_stuf: StUF zaaktype-identificatie
        startdatum_vanaf: Alleen zaken vanaf deze datum (YYYYMMDD)
        batch_size: Aantal zaken per batch

    Returns:
        Migratieresultaat met tellingen
    """
    zgw_client = httpx.Client(
        base_url=zgw_base_url,
        headers={
            "Authorization": f"Bearer {api_key}",
            "Content-Type": "application/json",
        },
    )

    zaaktype_url = ZAAKTYPE_MAPPING.get(zaaktype_stuf)
    if not zaaktype_url:
        raise ValueError(f"Onbekend zaaktype: {zaaktype_stuf}")

    # Stap 1: Haal zaken op uit StUF-ZKN
    stuf_zaken = _opvragen_stuf_zaken(
        stuf_endpoint, zaaktype_stuf, startdatum_vanaf
    )
    logger.info("Opgehaald: %d zaken uit StUF-ZKN", len(stuf_zaken))

    resultaat = {"totaal": len(stuf_zaken), "geslaagd": 0, "mislukt": 0, "fouten": []}

    # Stap 2: Migreer per zaak naar ZGW
    for zaak in stuf_zaken:
        try:
            zgw_zaak = _converteer_zaak(zaak, zaaktype_url)
            response = zgw_client.post("/zaken/api/v1/zaken", json=zgw_zaak)
            response.raise_for_status()
            resultaat["geslaagd"] += 1
            logger.info("Zaak %s gemigreerd", zaak.get("identificatie"))
        except Exception as e:
            resultaat["mislukt"] += 1
            resultaat["fouten"].append(
                {"zaak": zaak.get("identificatie"), "fout": str(e)}
            )
            logger.error("Fout bij zaak %s: %s", zaak.get("identificatie"), e)

    return resultaat


def _opvragen_stuf_zaken(
    endpoint: str, zaaktype: str, startdatum: str
) -> list[dict]:
    """Vraag zaken op via StUF-ZKN Lv01."""
    soap_body = f"""<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
    xmlns:stuf="http://www.egem.nl/StUF/StUF0301"
    xmlns:zkn="http://www.egem.nl/StUF/sector/zkn/0310">
  <soapenv:Body>
    <zkn:zakLv01>
      <stuf:stuurgegevens>
        <stuf:berichtcode>Lv01</stuf:berichtcode>
        <stuf:zender>
          <stuf:applicatie>MigratieTool</stuf:applicatie>
        </stuf:zender>
      </stuf:stuurgegevens>
      <stuf:parameters>
        <stuf:sortering>1</stuf:sortering>
      </stuf:parameters>
      <stuf:gelijk>
        <zkn:isVan stuf:entiteittype="ZAKZKT">
          <zkn:gerelateerde stuf:entiteittype="ZKT">
            <zkn:identificatie>{zaaktype}</zkn:identificatie>
          </zkn:gerelateerde>
        </zkn:isVan>
      </stuf:gelijk>
    </zkn:zakLv01>
  </soapenv:Body>
</soapenv:Envelope>"""

    response = httpx.post(
        endpoint,
        content=soap_body.encode(),
        headers={"Content-Type": "text/xml"},
    )
    response.raise_for_status()

    # Parse StUF-antwoord
    root = etree.fromstring(response.content)
    zaken = []
    for obj in root.findall(".//zkn:object", NS):
        zaak = {}
        for child in obj:
            tag = etree.QName(child).localname
            if child.text:
                zaak[tag] = child.text
        zaken.append(zaak)

    return zaken


def _converteer_zaak(stuf_zaak: dict, zaaktype_url: str) -> dict:
    """Converteer StUF-zaak dict naar ZGW Zaken API formaat."""

    def _parse_datum(d: str) -> str:
        """Converteer StUF datum (YYYYMMDD) naar ISO 8601."""
        if d and len(d) >= 8:
            return f"{d[:4]}-{d[4:6]}-{d[6:8]}"
        return d

    return {
        "zaaktype": zaaktype_url,
        "identificatie": stuf_zaak.get("identificatie", ""),
        "omschrijving": stuf_zaak.get("omschrijving", ""),
        "startdatum": _parse_datum(stuf_zaak.get("startdatum", "")),
        "einddatumGepland": _parse_datum(stuf_zaak.get("einddatumGepland", "")),
        "registratiedatum": _parse_datum(stuf_zaak.get("registratiedatum", "")),
        "verantwoordelijkeOrganisatie": stuf_zaak.get(
            "verantwoordelijkeOrganisatie", ""
        ),
        "bronorganisatie": stuf_zaak.get("verantwoordelijkeOrganisatie", ""),
    }
```

## Veelvoorkomende problemen

| Probleem | Oorzaak | Oplossing |
|----------|---------|-----------|
| **Datumformaat** | StUF: `YYYYMMDD`, ZGW: `YYYY-MM-DD` | Conversie in vertaallaag |
| **Relaties** | StUF: geneste XML, ZGW: URL-referenties | Mapping-tabel met UUID-lookup |
| **Identificatie** | StUF: organisatie+volgnummer, ZGW: UUID | Mapping-tabel bijhouden |
| **Bestandsbijlagen** | StUF: base64 in XML, ZGW: multipart upload | Decodeer en upload apart via Documenten API |
| **Null-waarden** | StUF: `noValue="geenWaarde"`, ZGW: `null` of veld weglaten | Null-detectie in parser |
| **Sortering** | StUF: parameter in bericht, ZGW: query parameter `ordering` | Vertaal naar `?ordering=veld` |
| **Paginering** | StUF: indicatorVervolgvraag, ZGW: `?page=N` | Cursor-based naar offset-based |
| **Autorisatie** | StUF: organisatie in stuurgegevens, ZGW: JWT met scopes | Autorisaties API configureren |

## Implementatie-checklist

- [ ] **Inventarisatie**: alle StUF-koppelingen in kaart gebracht (BG, ZKN, EF)
- [ ] **Mapping**: veldmapping StUF naar ZGW/Haal Centraal gedocumenteerd
- [ ] **Zaaktype-mapping**: StUF zaaktypen gekoppeld aan ZGW zaaktype-URL's
- [ ] **Strategie**: migratiestrategie gekozen (Strangler Fig / ACL / Dual Write)
- [ ] **Vertaallaag**: adapter gebouwd voor StUF-naar-ZGW vertaling
- [ ] **Datumconversie**: YYYYMMDD naar ISO 8601 conversie geimplementeerd
- [ ] **Relaties**: URL-referenties correct opgebouwd (zaaktype, status, resultaat)
- [ ] **Documenten**: bijlagemigratie van base64-in-XML naar Documenten API
- [ ] **Notificaties**: StUF-kennisgevingen (Bv03) vertaald naar Notificaties API
- [ ] **Autorisatie**: JWT-tokens en scopes geconfigureerd in Autorisaties API
- [ ] **Datamigratie**: historische zaken gemigreerd met integriteitscontrole
- [ ] **Coexistentie**: legacy StUF-clients werken tijdens migratieperiode
- [ ] **Monitoring**: logging van vertaalde berichten voor debugging
- [ ] **Rollback**: terugvalscenario gedocumenteerd en getest

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **zgw-apis** | ZGW API's (Zaken, Documenten, Catalogi, Besluiten) — de opvolger van StUF-ZKN |
| **gemma-common-ground** | Common Ground architectuur en 5-lagenmodel |
| **digikoppeling** | Digikoppeling voor MSH/MSH2 en ebMS2 berichtenverkeer |
| **nora-architectuur** | Verplichte standaarden en architectuurprincipes |
| **sociaal-domein** | iStandaarden (iWmo/iJw) die ook StUF-elementen bevatten |

## Meer informatie

- [VNG StUF-standaarden](https://vng.nl/rubrieken/onderwerpen/standaarden) — officieel beheer
- [StUF 03.01 specificatie](https://www.gemmaonline.nl/index.php/StUF_Berichtenstandaard) — technische specificatie
- [ZGW API's](https://vng-realisatie.github.io/gemma-zaken/) — opvolger van StUF-ZKN
- [Haal Centraal BRP](https://brp-api.github.io/Haal-Centraal-BRP-bevragen/) — opvolger van StUF-BG
- [GEMMA Online](https://www.gemmaonline.nl/) — gemeentelijke modelarchitectuur
- [Common Ground](https://commonground.nl/) — doelarchitectuur voor migratie
