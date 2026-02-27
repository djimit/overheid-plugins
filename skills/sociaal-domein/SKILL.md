---
name: sociaal-domein
description: >-
  Helpt bij het bouwen van systemen voor het sociaal domein van gemeenten,
  inclusief iWmo, iJw, iEb berichtenstandaarden, Suwinet-koppeling,
  en ketenstandaarden voor de Wmo, Jeugdwet en Participatiewet. Gebruik
  deze skill wanneer de gebruiker vraagt over 'sociaal domein',
  'iWmo', 'iJw', 'iEb', 'Suwinet', 'Wmo', 'Jeugdwet',
  'Participatiewet', 'schuldhulpverlening', 'bijstand',
  'Wmo-aanvraag', 'jeugdzorg', 'jeugdhulp', 'maatschappelijke ondersteuning',
  'berichtenstandaard sociaal domein', 'StUF sociaal domein',
  'iStandaarden', 'ketenstandaard', 'GGK', 'Gemeentelijk Gegevensknooppunt',
  'BKWI', 'Bureau Keteninformatisering Werk en Inkomen',
  'UWV koppeling', 'SVB koppeling', 'CAK koppeling',
  'toewijzing', 'verantwoording', 'declaratie',
  'zorgtoewijzing', 'zorgaanbieder', 'beschikking sociaal domein',
  'Wmo-voorziening', 'jeugdhulpvoorziening', 'gemeentelijk sociaal domein',
  of wanneer de gebruiker een systeem wil bouwen voor het gemeentelijke
  sociaal domein of wil koppelen met ketenpartners.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# Sociaal Domein — iStandaarden & Ketenintegratie

Bouw systemen voor het gemeentelijke sociaal domein met iStandaarden (iWmo, iJw, iEb) en integraties met ketenpartners.

Bron: [iStandaarden](https://istandaarden.nl/) | [VNG Sociaal Domein](https://vng.nl/rubrieken/onderwerpen/sociaal-domein) | [BKWI/Suwinet](https://www.bkwi.nl/)

## Overzicht sociaal domein

Sinds de decentralisaties (2015) zijn gemeenten verantwoordelijk voor drie wetten:

| Wet | Doelgroep | Voorzieningen | Berichtenstandaard |
|-----|-----------|--------------|-------------------|
| **Wmo 2015** | Burgers met beperking | Hulp bij huishouden, begeleiding, dagbesteding, beschermd wonen, hulpmiddelen | **iWmo** |
| **Jeugdwet** | Jeugdigen (0-18/23) | Jeugdhulp, jeugd-GGZ, jeugdbescherming, jeugdreclassering | **iJw** |
| **Participatiewet** | Werkzoekenden, bijstand | Bijstandsuitkering, re-integratie, beschut werk, loonkostensubsidie | **iEb** |

### Ketenpartners

| Partner | Rol | Koppeling |
|---------|-----|-----------|
| **Zorgaanbieders** | Leveren Wmo- en jeugdhulp | iWmo/iJw berichten |
| **CAK** | Eigen bijdrage Wmo | iWmo berichten (CAK-route) |
| **UWV** | Uitkeringen, werkgelegenheid | Suwinet, iEb |
| **SVB** | Persoonsgebonden budgetten (PGB), AOW | iWmo/iJw, SVB-berichten |
| **CBS** | Statistiek | Beleidsinformatie sociaal domein |
| **Gecertificeerde instellingen** | Jeugdbescherming, jeugdreclassering | iJw berichten |

## iStandaarden — berichtenstandaarden

De iStandaarden definiëren het berichtenverkeer tussen gemeenten en zorgaanbieders/ketenpartners.

### iWmo — berichtenverkeer

| Bericht | Richting | Beschrijving |
|---------|---------|-------------|
| **wmo301** | Gemeente → Aanbieder | Toewijzing: gemeente wijst voorziening toe aan aanbieder |
| **wmo302** | Aanbieder → Gemeente | Melding aanvang: aanbieder meldt start levering |
| **wmo303** | Gemeente → Aanbieder | Verzoek om wijziging toewijzing |
| **wmo305** | Aanbieder → Gemeente | Declaratie: maandelijkse declaratie van geleverde zorg |
| **wmo315** | Aanbieder → Gemeente | Verantwoording: verantwoording van geleverde zorg |
| **wmo317** | Gemeente → Aanbieder | Retourbericht verantwoording |

### iJw — berichtenverkeer

| Bericht | Richting | Beschrijving |
|---------|---------|-------------|
| **jw301** | Gemeente → Aanbieder | Toewijzing jeugdhulp |
| **jw302** | Aanbieder → Gemeente | Melding aanvang jeugdhulp |
| **jw303** | Gemeente → Aanbieder | Verzoek wijziging |
| **jw305** | Aanbieder → Gemeente | Declaratie jeugdhulp |
| **jw315** | Aanbieder → Gemeente | Verantwoording jeugdhulp |

### Berichtstructuur (XML)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<WMO301
  xmlns="http://www.istandaarden.nl/iwmo/3_2/basisschema/schema"
  xmlns:iwmo="http://www.istandaarden.nl/iwmo/3_2/wmo301/schema">

  <Header>
    <BerichtCode>428</BerichtCode>
    <BerichtVersie>3</BerichtVersie>
    <BerichtSubversie>2</BerichtSubversie>
    <Afzender>
      <Gemeente>0363</Gemeente>
    </Afzender>
    <Ontvanger>
      <Zorgaanbieder>12345678</Zorgaanbieder>
    </Ontvanger>
    <BerichtIdentificatie>MSG-2026-001234</BerichtIdentificatie>
    <DagtekeningBericht>20260225</DagtekeningBericht>
  </Header>

  <Client>
    <Bsn>123456789</Bsn>
    <Geboortedatum>19800115</Geboortedatum>

    <ToewijzingWmo>
      <ToewijzingNummer>TW-2026-5678</ToewijzingNummer>
      <Toewijzingsdatum>20260225</Toewijzingsdatum>
      <ProductCategorie>01</ProductCategorie>
      <ProductCode>01A01</ProductCode>
      <Eenheid>14</Eenheid>
      <Frequentie>6</Frequentie>
      <Volume>4.00</Volume>
      <Ingangsdatum>20260301</Ingangsdatum>
      <Einddatum>20270228</Einddatum>
      <Budget>5200.00</Budget>
      <RedenWijziging>1</RedenWijziging>
    </ToewijzingWmo>
  </Client>
</WMO301>
```

### Productcategorieën Wmo

| Code | Categorie | Voorbeelden |
|------|-----------|------------|
| **01** | Begeleiding | Individuele begeleiding, groepsbegeleiding |
| **02** | Persoonlijke verzorging | Hulp bij ADL |
| **03** | Hulp bij het huishouden | Schoonmaak, wasverzorging |
| **04** | Verblijf (kort) | Kortdurend verblijf, logeren |
| **05** | Dagbesteding | Dagactiviteiten |
| **06** | Vervoer | Vervoersvoorzieningen |
| **07** | Hulpmiddel/woningaanpassing | Rolstoel, traplift |
| **10** | Beschermd wonen | Wonen met 24-uurs begeleiding |

### Eenheden

| Code | Eenheid | Gebruik |
|------|---------|---------|
| **14** | Uur | Begeleiding, verzorging |
| **16** | Dagdeel | Dagbesteding |
| **71** | Stuks | Hulpmiddelen |
| **81** | Euro | PGB, resultaatbekostiging |
| **82** | Etmaal | Verblijf |

## iEb — Participatiewet berichten

| Bericht | Richting | Beschrijving |
|---------|---------|-------------|
| **iEb301** | Gemeente → Dienstverlener | Toewijzing re-integratietraject |
| **iEb302** | Dienstverlener → Gemeente | Melding aanvang traject |
| **iEb305** | Dienstverlener → Gemeente | Declaratie |
| **iEb315** | Dienstverlener → Gemeente | Verantwoording |

## Suwinet — gegevensuitwisseling

Suwinet is het beveiligde netwerk voor gegevensuitwisseling in de keten Werk en Inkomen.

| Component | Beschrijving |
|-----------|-------------|
| **Suwinet-Inkijk** | Webapplicatie voor medewerkers om gegevens op te vragen (BRP, UWV, RDW, etc.) |
| **Suwinet-Inlezen** | Geautomatiseerde gegevensuitwisseling (system-to-system) |
| **Suwinet-Melden** | Signalen sturen tussen ketenpartners |

### Suwinet-Inkijk beschikbare bronnen

| Bron | Gegevens | Gebruik |
|------|----------|--------|
| **BRP** | Persoonsgegevens, adres, relaties | Identiteitsverificatie |
| **UWV polisadministratie** | Dienstverbanden, inkomen | Inkomensbepaling |
| **Belastingdienst** | Inkomen, vermogen | Draagkrachtbepaling |
| **RDW** | Voertuigregistratie | Vermogenstoets |
| **DUO** | Studiefinanciering | Inkomenstoets |
| **SVB** | AOW, Anw, AKW | Uitkeringsgegevens |
| **Kadaster** | Onroerend goed | Vermogenstoets |

### Suwinet beveiligingseisen

| Eis | Detail |
|-----|--------|
| **Toegang** | Alleen geautoriseerde medewerkers; RBAC op functieniveau |
| **Logging** | Elke raadpleging gelogd (wie, wanneer, welk gegeven, welk doel) |
| **Doelbinding** | Alleen opvragen voor uitvoering wettelijke taak |
| **Audit** | Jaarlijkse controle door BKWI op onrechtmatig gebruik |
| **Bewaartermijn logs** | 5 jaar |
| **Privacy** | Medewerkers mogen geen gegevens van bekenden opvragen |

## Procesflow: Wmo-aanvraag tot declaratie

```
Burger          Gemeente              Zorgaanbieder         CAK
  │                │                       │                  │
  ├── Melding ────→│                       │                  │
  │                ├── Onderzoek           │                  │
  │                ├── Beschikking ──────→ (burger)            │
  │                │                       │                  │
  │                ├── wmo301 ───────────→│                  │
  │                │   (toewijzing)        │                  │
  │                │                       │                  │
  │                │←─── wmo302 ──────────┤                  │
  │                │   (melding aanvang)   │                  │
  │                │                       │                  │
  │                │                       │── Levering ────→ (burger)
  │                │                       │                  │
  │                │←─── wmo305 ──────────┤                  │
  │                │   (declaratie)        │                  │
  │                │                       │                  │
  │                ├── CAK-bericht ──────────────────────────→│
  │                │   (eigen bijdrage)    │                  │
```

## Implementatiepatronen

### Berichtverwerking

```python
from dataclasses import dataclass
from datetime import date
from enum import Enum
import xml.etree.ElementTree as ET

class BerichtType(Enum):
    WMO301 = "wmo301"  # Toewijzing
    WMO302 = "wmo302"  # Melding aanvang
    WMO305 = "wmo305"  # Declaratie
    WMO315 = "wmo315"  # Verantwoording

@dataclass
class Toewijzing:
    toewijzing_nummer: str
    bsn: str  # Versleuteld opslaan!
    product_categorie: str
    product_code: str
    ingangsdatum: date
    einddatum: date
    volume: float
    eenheid: str

def parse_wmo301(xml_content: str) -> Toewijzing:
    """Parse een iWmo 301 toewijzingsbericht."""
    ns = {"iwmo": "http://www.istandaarden.nl/iwmo/3_2/wmo301/schema"}
    root = ET.fromstring(xml_content)

    client = root.find(".//Client")
    toewijzing = client.find(".//ToewijzingWmo")

    return Toewijzing(
        toewijzing_nummer=toewijzing.findtext("ToewijzingNummer"),
        bsn=client.findtext("Bsn"),
        product_categorie=toewijzing.findtext("ProductCategorie"),
        product_code=toewijzing.findtext("ProductCode"),
        ingangsdatum=date.fromisoformat(
            f"{toewijzing.findtext('Ingangsdatum')[:4]}-"
            f"{toewijzing.findtext('Ingangsdatum')[4:6]}-"
            f"{toewijzing.findtext('Ingangsdatum')[6:]}"
        ),
        einddatum=date.fromisoformat(
            f"{toewijzing.findtext('Einddatum')[:4]}-"
            f"{toewijzing.findtext('Einddatum')[4:6]}-"
            f"{toewijzing.findtext('Einddatum')[6:]}"
        ),
        volume=float(toewijzing.findtext("Volume")),
        eenheid=toewijzing.findtext("Eenheid"),
    )
```

### Koppeling met zaaksysteem (ZGW)

```python
async def koppel_toewijzing_aan_zaak(toewijzing: Toewijzing, zaak_url: str):
    """Koppel een iWmo-toewijzing aan een zaak in het zaaksysteem."""
    async with httpx.AsyncClient() as client:
        # Status bijwerken
        await client.post(
            f"{OPENZAAK_URL}/zaken/api/v1/statussen",
            json={
                "zaak": zaak_url,
                "statustype": STATUSTYPE_TOEGEWEZEN,
                "datumStatusGezet": toewijzing.ingangsdatum.isoformat(),
                "statustoelichting": f"Toewijzing {toewijzing.toewijzing_nummer} verstuurd"
            },
            headers={"Authorization": f"Bearer {get_zgw_token()}"}
        )
```

## Privacy in het sociaal domein

| Aandachtspunt | Maatregel |
|--------------|-----------|
| **BSN** | Versleuteld opslaan; alleen bij wettelijke grondslag |
| **Bijzondere gegevens** | Gezondheidsdata (Wmo/Jeugdwet) = bijzondere persoonsgegevens (Art. 9 AVG) |
| **Doelbinding** | Wmo-gegevens NIET gebruiken voor fraudedetectie Participatiewet |
| **Dataminimalisatie** | Alleen gegevens uitwisselen die nodig zijn voor het specifieke bericht |
| **Suwinet** | Elke raadpleging loggen; jaarlijkse audit |
| **DPIA** | Verplicht voor elk systeem dat sociaal-domeingegevens verwerkt |

## Implementatie-checklist

- [ ] **iStandaarden versie**: meest recente versie van iWmo, iJw en/of iEb geimplementeerd
- [ ] **Berichtvalidatie**: inkomende berichten gevalideerd tegen XSD-schema
- [ ] **Foutafhandeling**: retourberichten correct verwerkt bij afkeur
- [ ] **BSN-bescherming**: BSN versleuteld in opslag; niet in logs
- [ ] **Bijzondere gegevens**: gezondheidsdata extra beveiligd (BIO BBN2+)
- [ ] **Suwinet**: raadplegingen gelogd; doelbinding gecontroleerd; jaarlijkse audit
- [ ] **Zaakkoppeling**: iStandaarden-berichten gekoppeld aan zaak in ZGW
- [ ] **CAK-route**: eigen-bijdrage-berichten correct verstuurd aan CAK
- [ ] **Declaratieverwerking**: maandelijkse declaraties verwerkt en gecontroleerd
- [ ] **DPIA**: uitgevoerd voor alle sociaal-domein-gegevensverwerkingen
- [ ] **Privacy by Design**: doelbinding tussen Wmo, Jeugdwet en Participatiewet gewaarborgd
- [ ] **Testen**: berichten getest met iStandaarden testplatform

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **avg-privacy** | AVG-eisen voor bijzondere persoonsgegevens in het sociaal domein |
| **dpia-assessment** | DPIA uitvoeren voor sociaal-domein-systemen (verplicht bij bijzondere gegevens) |
| **zgw-apis** | ZGW API's voor zaakgericht werken en koppeling met iStandaarden |
| **gemma-common-ground** | GEMMA architectuur en Common Ground voor gemeentelijke systemen |
| **overheid-authenticatie** | DigiD voor burgerportalen in het sociaal domein |

## Meer informatie

- [iStandaarden](https://istandaarden.nl/) | [iStandaarden portaal](https://portaal.istandaarden.nl/)
- [iWmo 3.2](https://istandaarden.nl/istandaarden/iwmo) | [iJw 3.2](https://istandaarden.nl/istandaarden/ijw)
- [BKWI / Suwinet](https://www.bkwi.nl/) — ketengegevensuitwisseling
- [VNG — Sociaal Domein](https://vng.nl/rubrieken/onderwerpen/sociaal-domein)
- [Gemeentelijk Gegevensknooppunt (GGK)](https://www.bkwi.nl/producten/ggk)
- [CBS Beleidsinformatie](https://www.cbs.nl/nl-nl/maatwerk/beleidsinformatie) — sociaal domein statistiek
