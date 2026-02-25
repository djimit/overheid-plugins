---
name: mdto-archivering
description: >-
  Helpt bij het bouwen van archiveringssystemen conform het Metagegevensmodel
  voor Duurzaam Toegankelijke Overheidsinformatie (MDTO), de Archiefwet 2021,
  het Archievenbesluit en DUTO-eisen. Biedt richtlijnen voor metadata,
  bewaartermijnen, vernietigingslijsten, overbrenging naar e-depot en
  duurzame toegankelijkheid. Gebruik deze skill wanneer de gebruiker vraagt
  over 'MDTO', 'archivering', 'archiefwet', 'duurzaam toegankelijk',
  'e-depot', 'digitaal archief', 'bewaartermijn', 'selectielijst',
  'vernietigingslijst', 'overbrenging', 'metagegevens', 'metadata archief',
  'informatieobject', 'archiefbescheiden', 'record management',
  'DUTO', 'duurzame toegankelijkheid', 'preservering', 'preservation',
  'NEN 2082', 'NEN-ISO 15489', 'NEN-ISO 23081', 'TMLO', 'RGBZ',
  'zaakgericht archiveren', 'overdracht digitaal archief',
  'Nationaal Archief', 'regionaal archief',
  of wanneer de gebruiker een systeem wil bouwen dat voldoet aan
  archiveringseisen van de Nederlandse overheid.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# MDTO & Archiefwet — Duurzaam Toegankelijke Overheidsinformatie

Bouw systemen die voldoen aan de archiveringseisen voor Nederlandse overheidsinformatie conform het MDTO, de Archiefwet 2021 en DUTO-criteria.

Bron: [Nationaal Archief — MDTO](https://www.nationaalarchief.nl/archiveren/mdto) | [Archiefwet 2021](https://wetten.overheid.nl/BWBR0048912) | [DUTO](https://www.nationaalarchief.nl/archiveren/duto)

## Wettelijk kader

| Aspect | Detail |
|--------|--------|
| **Wet** | Archiefwet 2021 (vervangt Archiefwet 1995 per 2025) |
| **Besluit** | Archievenbesluit 2024 |
| **Metadatastandaard** | MDTO (Metagegevensmodel Duurzaam Toegankelijke Overheidsinformatie) |
| **Kwaliteitseisen** | DUTO (Duurzame Toegankelijkheid Overheidsinformatie) |
| **Beheernormen** | NEN 2082 (e-depot), NEN-ISO 15489 (records management) |
| **Toezicht** | Inspectie Overheidsinformatie en Erfgoed |
| **Scope** | Alle overheidsorganen: Rijk, provincies, gemeenten, waterschappen, ZBO's |

### Kernverplichtingen Archiefwet 2021

- **Duurzame toegankelijkheid** (Art. 6): informatie moet vindbaar, beschikbaar, leesbaar, interpreteerbaar en betrouwbaar zijn
- **Metagegevens** (Art. 7): overheidsorganen registreren metagegevens conform MDTO
- **Selectie** (Art. 14-18): besluiten over bewaren of vernietigen op basis van selectielijst
- **Overbrenging** (Art. 20-25): permanente informatie overbrengen naar archiefbewaarplaats (max 20 jaar)
- **Vernietiging** (Art. 19): informatie vernietigen na verstrijken bewaartermijn (mag niet te vroeg, niet te laat)

## MDTO — metagegevensmodel

Het MDTO vervangt het TMLO (Toepassingsprofiel Metagegevens Lokale Overheden) en geldt voor alle overheden.

### Objecttypen

| Objecttype | Beschrijving |
|------------|-------------|
| **Informatieobject** | Eenheid van informatie (document, e-mail, dataset, foto, video) |
| **Bestand** | Technische representatie van een informatieobject (PDF, TIFF, XML) |
| **Groepsobject** | Aggregatie: dossier, zaak, serie (optioneel) |

### Verplichte metagegevens — Informatieobject

| Element | Kardinaliteit | Beschrijving | Voorbeeld |
|---------|--------------|-------------|-----------|
| **identificatie** | 1..* | Unieke identificatie (bron + kenmerk) | `{"identificatieBron": "Zaaksysteem", "identificatieKenmerk": "DOC-2026-001234"}` |
| **naam** | 1..1 | Beschrijvende naam | "Beschikking omgevingsvergunning Hoofdstraat 1" |
| **waardering** | 1..1 | Bewaren of vernietigen | `"vernietigen"` met vernietigingstermijn |
| **archiefvormer** | 1..* | Organisatie die het heeft gecreeerd | `{"archiefvormerType": "organisatie", "archiefvormerNaam": "Gemeente Amsterdam"}` |
| **beperkingGebruik** | 0..* | Openbaarheid, AVG-beperkingen | `{"beperkingGebruikType": "niet openbaar", "beperkingGebruikTermijn": "2046-01-01"}` |

### Verplichte metagegevens — Bestand

| Element | Kardinaliteit | Beschrijving | Voorbeeld |
|---------|--------------|-------------|-----------|
| **identificatie** | 1..* | Unieke identificatie | `{"identificatieBron": "DMS", "identificatieKenmerk": "FILE-001"}` |
| **naam** | 1..1 | Bestandsnaam | "beschikking_hoofdstraat_1.pdf" |
| **bestandsformaat** | 1..1 | PRONOM-referentie of MIME-type | `{"bestandsformaatNaam": "PDF/A-2b"}` |
| **omvang** | 1..1 | Bestandsgrootte in bytes | `1048576` |
| **checksum** | 1..* | Integriteitscontrole | `{"checksumAlgoritme": "SHA-256", "checksumWaarde": "a1b2c3..."}` |

### Optionele maar aanbevolen metagegevens

| Element | Beschrijving |
|---------|-------------|
| **classificatie** | Ordening binnen het archief (bijv. I-navigator, zaaktypecode) |
| **trefwoord** | Zoektermen |
| **dekking** | Tijd- en/of geografische dekking |
| **taal** | Taal van het informatieobject (ISO 639-2: `nld`) |
| **event** | Levenscyclusgebeurtenissen (creatie, wijziging, overbrenging) |
| **relatie** | Verwijzingen naar andere objecten |
| **betrokkene** | Personen/organisaties gerelateerd aan het object |
| **activiteit** | Het werkproces waarbinnen het object is gecreeerd |

### MDTO XML-voorbeeld

```xml
<?xml version="1.0" encoding="UTF-8"?>
<MDTO:informatieobject
  xmlns:MDTO="https://www.nationaalarchief.nl/mdto"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://www.nationaalarchief.nl/mdto mdto.xsd">

  <MDTO:identificatie>
    <MDTO:identificatieBron>Zaaksysteem</MDTO:identificatieBron>
    <MDTO:identificatieKenmerk>DOC-2026-001234</MDTO:identificatieKenmerk>
  </MDTO:identificatie>

  <MDTO:naam>Beschikking omgevingsvergunning Hoofdstraat 1</MDTO:naam>

  <MDTO:waardering>
    <MDTO:waarderingBasis>Selectielijst gemeenten 2020</MDTO:waarderingBasis>
    <MDTO:waarderingDatum>2026-02-25</MDTO:waarderingDatum>
    <MDTO:waarderingProces>6.1.3 - Vergunningverlening</MDTO:waarderingProces>
    <MDTO:bewaartermijn>
      <MDTO:bewaartermijnTrigger>Na afloop vergunning</MDTO:bewaartermijnTrigger>
      <MDTO:bewaartermijnLooptijd>P20Y</MDTO:bewaartermijnLooptijd>
    </MDTO:bewaartermijn>
  </MDTO:waardering>

  <MDTO:archiefvormer>
    <MDTO:archiefvormerType>organisatie</MDTO:archiefvormerType>
    <MDTO:archiefvormerNaam>Gemeente Amsterdam</MDTO:archiefvormerNaam>
    <MDTO:archiefvormerIdentificatie>
      <MDTO:identificatieBron>TOOI</MDTO:identificatieBron>
      <MDTO:identificatieKenmerk>tooi:gem0363</MDTO:identificatieKenmerk>
    </MDTO:archiefvormerIdentificatie>
  </MDTO:archiefvormer>

  <MDTO:event>
    <MDTO:eventType>creatie</MDTO:eventType>
    <MDTO:eventTijd>2026-02-25</MDTO:eventTijd>
  </MDTO:event>

  <MDTO:beperkingGebruik>
    <MDTO:beperkingGebruikType>openbaar</MDTO:beperkingGebruikType>
  </MDTO:beperkingGebruik>
</MDTO:informatieobject>
```

## DUTO — Duurzame Toegankelijkheid

De 10 DUTO-kwaliteitseisen voor overheidsinformatie:

| # | Eis | Beschrijving |
|---|-----|-------------|
| 1 | **Vindbaar** | Informatie is te vinden via zoeken en browsen |
| 2 | **Beschikbaar** | Informatie is op te vragen als dat nodig is |
| 3 | **Leesbaar** | Informatie is te openen en te lezen |
| 4 | **Interpreteerbaar** | De betekenis van informatie is te begrijpen |
| 5 | **Betrouwbaar** | Integriteit en authenticiteit zijn gewaarborgd |
| 6 | **Compleet** | Alle relevante informatie is aanwezig |
| 7 | **Tijdig** | Informatie is actueel en op tijd beschikbaar |
| 8 | **Geordend** | Informatie is logisch georganiseerd |
| 9 | **Duurzaam** | Informatie blijft toegankelijk gedurende de bewaartermijn |
| 10 | **Beveiligd** | Informatie is beschermd tegen ongeautoriseerde toegang |

## Selectie en waardering

### Selectielijsten

| Overheidslaag | Selectielijst | Geldig |
|---------------|--------------|--------|
| **Gemeenten** | Selectielijst gemeenten en intergemeentelijke organen 2020 | 2020-heden |
| **Rijksoverheid** | Generieke selectielijst Rijksoverheid (per ministerie) | Verschilt |
| **Provincies** | Selectielijst provincies 2021 | 2021-heden |
| **Waterschappen** | Selectielijst waterschappen 2021 | 2021-heden |

### Waarderingsbesluit implementeren

```python
from dataclasses import dataclass
from datetime import date, timedelta
from enum import Enum

class Waardering(Enum):
    BEWAREN = "bewaren"          # Permanent bewaren (overbrengen naar e-depot)
    VERNIETIGEN = "vernietigen"  # Vernietigen na bewaartermijn

@dataclass
class Bewaartermijn:
    trigger: str                  # Bijv. "na afhandeling zaak"
    looptijd_jaren: int           # Bijv. 10
    selectielijst: str            # Bijv. "Selectielijst gemeenten 2020"
    procescode: str               # Bijv. "6.1.3"

    def bereken_vernietingsdatum(self, triggerdatum: date) -> date:
        return triggerdatum + timedelta(days=self.looptijd_jaren * 365)

@dataclass
class ArchiefObject:
    identificatie: str
    naam: str
    waardering: Waardering
    bewaartermijn: Bewaartermijn | None
    zaak_einddatum: date | None = None

    def is_vernietigbaar(self) -> bool:
        if self.waardering != Waardering.VERNIETIGEN:
            return False
        if not self.zaak_einddatum or not self.bewaartermijn:
            return False
        vernietingsdatum = self.bewaartermijn.bereken_vernietingsdatum(
            self.zaak_einddatum
        )
        return date.today() >= vernietingsdatum
```

## E-depot en overbrenging

### Overbrengingsproces

| Stap | Activiteit | Verantwoordelijke |
|------|-----------|-------------------|
| 1 | **Selectie**: bepaal welke informatie permanent te bewaren | Zorgdrager |
| 2 | **Metadata**: vul MDTO-metagegevens aan | Zorgdrager |
| 3 | **Formaten**: converteer naar duurzame formaten | Zorgdrager |
| 4 | **Validatie**: controleer tegen MDTO-schema en e-depot-eisen | Zorgdrager + Archiefbewaarplaats |
| 5 | **SIP**: maak Submission Information Package (E-ARK SIP of lokaal formaat) | Zorgdrager |
| 6 | **Overdracht**: lever SIP aan bij archiefbewaarplaats | Zorgdrager |
| 7 | **Ingest**: archiefbewaarplaats neemt op in e-depot | Archiefbewaarplaats |
| 8 | **Bevestiging**: akkoordverklaring overbrenging | Beide partijen |

### Duurzame bestandsformaten

| Type | Voorkeur | Acceptabel | Vermijden |
|------|----------|-----------|-----------|
| **Tekst** | PDF/A-1b, PDF/A-2b | PDF/A-3 | .doc, .docx (niet duurzaam) |
| **Spreadsheet** | ODS, CSV | XLSX (met restricties) | XLS |
| **Afbeelding** | TIFF, JPEG 2000 | PNG, JPEG | BMP, GIF |
| **E-mail** | EML (RFC 5322) | MBOX | PST, OST |
| **Database** | SIARD 2.1 | CSV + schema | Proprietaire dump |
| **XML** | XML + XSD | — | XML zonder schema |
| **Video** | MKV/FFV1 | MP4/H.264 | WMV, AVI |

### Checksum-generatie

```python
import hashlib
from pathlib import Path

def generate_checksum(filepath: Path, algorithm: str = "sha256") -> dict:
    """Genereer checksum conform MDTO-vereisten."""
    h = hashlib.new(algorithm)
    with open(filepath, "rb") as f:
        for chunk in iter(lambda: f.read(8192), b""):
            h.update(chunk)
    return {
        "checksumAlgoritme": f"SHA-{algorithm[3:]}" if algorithm.startswith("sha") else algorithm.upper(),
        "checksumWaarde": h.hexdigest(),
        "checksumDatum": date.today().isoformat()
    }
```

## Zaakgericht archiveren

Bij zaakgericht werken (ZGW) worden zaken en documenten gearchiveerd na afhandeling:

| Stap | ZGW-actie | Archiveringsactie |
|------|-----------|-------------------|
| 1 | Zaak krijgt resultaat + einddatum | Bewaartermijn start |
| 2 | Zaak wordt afgesloten | Status → "Afgesloten" |
| 3 | Bewaartermijn verstreken | Vernietigingslijst genereren (bij waardering "vernietigen") |
| 4 | Akkoord op vernietigingslijst | Informatie + metagegevens vernietigen + verklaring van vernietiging |
| 5 | Permanente informatie | Overbrengen naar e-depot (met MDTO-export) |

### ZGW → MDTO mapping

| ZGW-veld | MDTO-element |
|----------|-------------|
| `zaak.identificatie` | `informatieobject.identificatie` (als groepsobject) |
| `zaak.zaaktype.selectielijstProcestype` | `waardering.waarderingProces` |
| `zaak.archiefnominatie` | `waardering` (bewaren/vernietigen) |
| `zaak.archiefactiedatum` | Berekend: einddatum + bewaartermijn |
| `enkelvoudiginformatieobject` | `informatieobject` |
| `enkelvoudiginformatieobject.bestandsnaam` | `bestand.naam` |
| `enkelvoudiginformatieobject.formaat` | `bestand.bestandsformaat` |

## NEN 2082 — E-depoteisen

Kerneisen voor een e-depot (digitaal archiefsysteem):

| Categorie | Eis |
|-----------|-----|
| **Ingest** | Validatie van SIP, viruscontrole, formatidentificatie (PRONOM/DROID) |
| **Opslag** | Redundante opslag, geografische spreiding, bitrot-detectie |
| **Preservering** | Formaat-migratie, emulatie-strategie, preserveringsplan |
| **Toegang** | Zoeken, raadplegen, DIP-levering, openbaarheidsregime |
| **Integriteit** | Checksums, fixity checks, audittrail |
| **Metagegevens** | MDTO-compliant, preserveringsmetadata (PREMIS) |

## Implementatie-checklist

- [ ] **MDTO-metagegevens**: alle verplichte elementen worden vastgelegd bij creatie
- [ ] **Selectielijst**: juiste selectielijst toegepast; procescodes gekoppeld aan zaaktypen
- [ ] **Bewaartermijnen**: geautomatiseerd berekend op basis van zaak-einddatum + selectielijst
- [ ] **Vernietigingslijst**: periodiek gegenereerd voor informatie waarvan termijn is verstreken
- [ ] **Vernietigingsproces**: beveiligd proces met accordering, logging en verklaring van vernietiging
- [ ] **Duurzame formaten**: documenten geconverteerd naar PDF/A, TIFF of andere duurzame formaten
- [ ] **Checksums**: SHA-256 checksums bij creatie en bij elke verplaatsing
- [ ] **E-depot-koppeling**: SIP-export naar archiefbewaarplaats geimplementeerd
- [ ] **MDTO-validatie**: export gevalideerd tegen MDTO XML-schema
- [ ] **Openbaarheid**: beperkingen op gebruik (AVG, Woo) vastgelegd in metagegevens
- [ ] **Audittrail**: alle archiveringsbeslissingen traceerbaar gelogd
- [ ] **ZGW-integratie**: archiefnominatie en archiefactiedatum correct ingevuld bij zaakafhandeling

## Meer informatie

- [Nationaal Archief — MDTO](https://www.nationaalarchief.nl/archiveren/mdto) | [MDTO XML-schema](https://www.nationaalarchief.nl/archiveren/mdto/xml-schema)
- [Archiefwet 2021](https://wetten.overheid.nl/BWBR0048912) | [Archievenbesluit](https://wetten.overheid.nl/BWBR0007748)
- [DUTO](https://www.nationaalarchief.nl/archiveren/duto) — kwaliteitseisen duurzame toegankelijkheid
- [Selectielijst gemeenten 2020](https://vng.nl/rubrieken/onderwerpen/selectielijst)
- [NEN 2082](https://www.nen.nl/nen-2082-2008-nl-153866) — eisen functionaliteit informatie- en archiefmanagement
- [KIDO](https://www.nationaalarchief.nl/archiveren/kennisbank/kido) — Kwaliteitskader Informatiebeheer Decentrale Overheden
