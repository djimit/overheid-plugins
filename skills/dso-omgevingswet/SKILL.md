---
name: dso-omgevingswet
description: >-
  Helpt bij het ontwikkelen van applicaties voor het Digitaal Stelsel
  Omgevingswet (DSO), inclusief STOP/TPOD, STAM, STTR, IMOW en
  OW-objecten. Biedt richtlijnen voor het publiceren van omgevingsdocumenten,
  vergunningaanvragen, toepasbare regels en ruimtelijke plannen. Gebruik deze
  skill wanneer de gebruiker vraagt over 'DSO', 'Omgevingswet',
  'Digitaal Stelsel Omgevingswet', 'omgevingsloket', 'STOP', 'TPOD',
  'STAM', 'STTR', 'IMOW', 'OW-object', 'omgevingsplan',
  'omgevingsvisie', 'omgevingsverordening', 'omgevingsdocument',
  'activiteit', 'juridische regel', 'annotatie',
  'werkingsgebied', 'locatie', 'GIO', 'geometrisch informatieobject',
  'toepasbare regel', 'vragenboom', 'indieningsvereiste',
  'vergunningcheck', 'aanvraag omgevingsvergunning',
  'LVBB', 'Landelijke Voorziening Bekendmaken en Beschikbaar stellen',
  'OZON', 'bruidsschat', 'Omgevingswet API',
  'omgevingsplan wijzigen', 'besluit omgevingswet',
  of wanneer de gebruiker wil aansluiten op het Digitaal Stelsel
  Omgevingswet of omgevingsdocumenten wil publiceren.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
  - Bash(curl *)
---

# DSO — Digitaal Stelsel Omgevingswet

Ontwikkel applicaties die aansluiten op het Digitaal Stelsel Omgevingswet (DSO) voor het publiceren van omgevingsdocumenten, vergunningchecks en aanvragen.

Bron: [Aan de slag met de Omgevingswet](https://aandeslagmetdeomgevingswet.nl/) | [DSO Ontwikkelaarsportaal](https://aandeslagmetdeomgevingswet.nl/digitaal-stelsel/technisch-aansluiten/) | [STOP standaard](https://koop.gitlab.io/STOP/standaard/)

## Wettelijk kader

| Aspect | Detail |
|--------|--------|
| **Wet** | Omgevingswet (in werking sinds 1 januari 2024) |
| **Doel** | Bundeling van 26 wetten over de fysieke leefomgeving |
| **Digitaal stelsel** | DSO: digitale ondersteuning voor het werken met de Omgevingswet |
| **Loket** | Omgevingsloket (omgevingswet.overheid.nl) |
| **Beheerder** | Ministerie van BZK; technisch beheer door diverse partijen |
| **Scope** | Gemeenten, provincies, waterschappen, Rijk |

### Instrumenten Omgevingswet

| Instrument | Vastgesteld door | Voorbeeld |
|------------|-----------------|-----------|
| **Omgevingsvisie** | Gemeente, provincie, Rijk | Strategische langetermijnvisie |
| **Omgevingsplan** | Gemeente | Vervangt bestemmingsplannen + verordeningen |
| **Omgevingsverordening** | Provincie | Provinciale regels fysieke leefomgeving |
| **Waterschapsverordening** | Waterschap | Regels waterbeheer |
| **AMvB's** | Rijk | Bal, Bbl, Bkl, Ob |
| **Programma** | Alle overheden | Maatregelen om omgevingswaarden te bereiken |
| **Projectbesluit** | Provincie, Rijk | Grote projecten van publiek belang |

## DSO-architectuur

```
┌─────────────────────────────────────────────────────────────┐
│                    OMGEVINGSLOKET                            │
│  Vergunningcheck │ Aanvragen │ Regels raadplegen │ Melden  │
└──────────┬───────────────────────────────┬──────────────────┘
           │                               │
    ┌──────▼──────┐                 ┌──────▼──────┐
    │    STTR     │                 │    LVBB     │
    │ Toepasbare  │                 │ Bekendmaken │
    │   Regels    │                 │ & Beschik-  │
    │             │                 │ baar stellen│
    └──────┬──────┘                 └──────┬──────┘
           │                               │
    ┌──────▼──────┐                 ┌──────▼──────┐
    │    OZON     │                 │  STOP/TPOD  │
    │ OW-objecten │ ◄──────────────│ Juridische  │
    │ Registratie │                 │ documenten  │
    └─────────────┘                 └─────────────┘
```

### DSO-componenten

| Component | Functie |
|-----------|---------|
| **Omgevingsloket** | Portaal voor burgers/bedrijven: vergunningcheck, aanvragen, melden |
| **LVBB** | Landelijke Voorziening Bekendmaken en Beschikbaar stellen (publicatie) |
| **OZON** | Object-georiënteerde ontsluiting van OW-objecten (registratie) |
| **DSO-verzoekafhandeling** | Routering van vergunningaanvragen naar bevoegd gezag |
| **Stelselcatalogus** | Overzicht van alle activiteiten, documenten, bevoegde gezagen |
| **Registratie toepasbare regels** | Opslag van vragenbomen en indieningsvereisten |

## STOP/TPOD — Documentstandaard

STOP (Standaard voor Officiële Publicaties) en TPOD (Toepassingsprofiel Omgevingsdocumenten) zijn de XML-standaarden voor omgevingsdocumenten.

### STOP — juridische tekst

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Regeling xmlns="https://standaarden.overheid.nl/stop/imop/tekst/">
  <RegelingOpschrift>
    <Al>Omgevingsplan Gemeente Amsterdam</Al>
  </RegelingOpschrift>

  <Lichaam>
    <Hoofdstuk eId="chp_1" wId="gm0363_1__chp_1">
      <Kop><Nummer>1</Nummer><Opschrift>Algemene bepalingen</Opschrift></Kop>

      <Artikel eId="art_1.1" wId="gm0363_1__art_1.1">
        <Kop><Nummer>1.1</Nummer><Opschrift>Begripsbepalingen</Opschrift></Kop>
        <Lid eId="art_1.1__lid_1" wId="gm0363_1__art_1.1__lid_1">
          <LidNummer>1</LidNummer>
          <Inhoud>
            <Al>In dit omgevingsplan wordt verstaan onder:</Al>
            <Lijst>
              <Li>
                <LiNummer>a.</LiNummer>
                <Al><IntRef ref="trm_bouwwerk">bouwwerk</IntRef>: constructie van enige omvang...</Al>
              </Li>
            </Lijst>
          </Inhoud>
        </Lid>
      </Artikel>
    </Hoofdstuk>
  </Lichaam>
</Regeling>
```

### Identificatie (eId en wId)

| Type | Formaat | Voorbeeld |
|------|---------|-----------|
| **eId** (expression-level) | `{type}_{nummer}` | `art_1.1`, `chp_2` |
| **wId** (work-level) | `{bevoegd_gezag}_{versie}__{eId}` | `gm0363_1__art_1.1` |
| **AKN-identifier** | `/akn/nl/act/{bg}/{jaar}/{naam}` | `/akn/nl/act/gm0363/2024/omgevingsplan` |

## IMOW — OW-objecten

IMOW (Informatiemodel Omgevingswet) definieert de objecten die gekoppeld worden aan juridische regels.

### OW-objecttypen

| OW-object | Beschrijving | Voorbeeld |
|-----------|-------------|-----------|
| **Regeltekst** | Verwijzing naar juridische tekst (artikel/lid) | Link naar `art_2.1__lid_1` |
| **Juridische Regel** | Regel met type (instructieregel, omgevingswaarderegel, regel voor iedereen) | "Het is verboden te bouwen zonder vergunning" |
| **Activiteit** | Handeling in de fysieke leefomgeving | "Bouwen van een bouwwerk" |
| **Locatie** | Geometrisch gebied waar regel geldt | Polygoon van een wijk |
| **Gebiedsaanwijzing** | Aanwijzing van een gebied met specifieke functie | "Woongebied", "Bedrijventerrein" |
| **Omgevingswaarde** | Meetbare kwaliteitseis | "Geluidbelasting max 50 dB" |
| **Omgevingsnorm** | Kwantitatieve norm | "Bouwhoogte max 12 meter" |

### OW-object XML (IMOW)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ow-dc:owBestand
  xmlns:ow-dc="http://www.geostandaarden.nl/imow/deelcollecties"
  xmlns:r="http://www.geostandaarden.nl/imow/regels"
  xmlns:l="http://www.geostandaarden.nl/imow/locatie"
  xmlns:ga="http://www.geostandaarden.nl/imow/gebiedsaanwijzing">

  <!-- Activiteit -->
  <r:Activiteit>
    <r:identificatie>nl.imow-gm0363.activiteit.BouwenBouwwerk</r:identificatie>
    <r:naam>Bouwen van een bouwwerk</r:naam>
    <r:groep>ConstructieActiviteit</r:groep>
    <r:bovenliggendeActiviteit>
      <r:ActiviteitRef>/join/id/regdata/gm0363/2024/activiteit/OmgevingsplanActiviteit</r:ActiviteitRef>
    </r:bovenliggendeActiviteit>
  </r:Activiteit>

  <!-- Juridische Regel -->
  <r:RegelVoorIedereen>
    <r:identificatie>nl.imow-gm0363.juridischeregel.001</r:identificatie>
    <r:idealisatie>exact</r:idealisatie>
    <r:artikelOfLid>
      <r:RegeltekstRef>/akn/nl/act/gm0363/2024/omgevingsplan/art_2.1__lid_1</r:RegeltekstRef>
    </r:artikelOfLid>
    <r:locatieaanduiding>
      <l:LocatieRef>/join/id/regdata/gm0363/2024/locatie/Grondgebied</l:LocatieRef>
    </r:locatieaanduiding>
    <r:activiteitaanduiding>
      <r:ActiviteitRef>nl.imow-gm0363.activiteit.BouwenBouwwerk</r:ActiviteitRef>
      <r:activiteitregelkwalificatie>vergunningplicht</r:activiteitregelkwalificatie>
    </r:activiteitaanduiding>
  </r:RegelVoorIedereen>

  <!-- Locatie (verwijzing naar GIO) -->
  <l:Gebied>
    <l:identificatie>nl.imow-gm0363.gebied.Grondgebied</l:identificatie>
    <l:noemer>Grondgebied gemeente Amsterdam</l:noemer>
  </l:Gebied>
</ow-dc:owBestand>
```

## GIO — Geometrisch Informatieobject

Geometrieën worden als apart informatieobject (GIO) aangeleverd in GML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<geo:GeoInformatieObjectVaststelling
  xmlns:geo="https://standaarden.overheid.nl/stop/imop/geo/"
  xmlns:gml="http://www.opengis.net/gml/3.2">

  <geo:FRBRWork>/join/id/regdata/gm0363/2024/locatie/Grondgebied</geo:FRBRWork>
  <geo:FRBRExpression>/join/id/regdata/gm0363/2024/locatie/Grondgebied/nld@2024-01-01</geo:FRBRExpression>

  <geo:locaties>
    <geo:Locatie>
      <geo:naam>Grondgebied gemeente Amsterdam</geo:naam>
      <geo:geometrie>
        <gml:MultiSurface srsName="urn:ogc:def:crs:EPSG::28992">
          <gml:surfaceMember>
            <gml:Polygon>
              <gml:exterior>
                <gml:LinearRing>
                  <gml:posList>119000 483000 120000 483000 120000 484000 119000 484000 119000 483000</gml:posList>
                </gml:LinearRing>
              </gml:exterior>
            </gml:Polygon>
          </gml:surfaceMember>
        </gml:MultiSurface>
      </geo:geometrie>
    </geo:Locatie>
  </geo:locaties>
</geo:GeoInformatieObjectVaststelling>
```

**Coordinatenstelsel**: altijd **EPSG:28992** (Rijksdriehoekscoordinaten / Amersfoort RD New).

## STTR — Toepasbare Regels

STTR (Standaard Toepasbare Regels) definieert vragenbomen voor de vergunningcheck in het Omgevingsloket.

### Structuur

| Element | Beschrijving |
|---------|-------------|
| **Activiteit** | De handeling waarvoor regels gelden |
| **Conclusie** | Uitkomst: vergunningplicht, meldingsplicht, verbod, toegestaan |
| **Vraag** | Vraag aan de gebruiker (ja/nee, keuzelijst, invoerveld) |
| **Regel** | Logische regel die antwoorden evalueert |
| **Indieningsvereiste** | Documenten/gegevens die bij een aanvraag moeten worden ingediend |

### STTR XML-voorbeeld

```xml
<RegelBeheerObject>
  <Activiteit>
    <identificatie>nl.imow-gm0363.activiteit.BouwenBouwwerk</identificatie>
    <naam>Bouwen van een bouwwerk</naam>
  </Activiteit>

  <Vraag id="vraag_01">
    <tekst>Wat is de hoogte van het bouwwerk?</tekst>
    <type>numeriek</type>
    <eenheid>meter</eenheid>
  </Vraag>

  <Vraag id="vraag_02">
    <tekst>Ligt het bouwwerk in een beschermd stadsgezicht?</tekst>
    <type>boolean</type>
  </Vraag>

  <Regel>
    <als>
      <en>
        <kleinerDan><vraagRef>vraag_01</vraagRef><waarde>5</waarde></kleinerDan>
        <gelijkAan><vraagRef>vraag_02</vraagRef><waarde>false</waarde></gelijkAan>
      </en>
    </als>
    <dan>
      <conclusie>vergunningvrij</conclusie>
    </dan>
  </Regel>

  <Regel>
    <anders/>
    <dan>
      <conclusie>vergunningplicht</conclusie>
      <indieningsvereisten>
        <document>Situatietekening</document>
        <document>Constructieve berekening</document>
      </indieningsvereisten>
    </dan>
  </Regel>
</RegelBeheerObject>
```

## LVBB — Publicatieproces

Het publiceren van een omgevingsdocument (besluit) verloopt via de LVBB:

| Stap | Actie | Systeem |
|------|-------|---------|
| 1 | **Besluit opstellen** | Plansoftware (lokaal) |
| 2 | **STOP/TPOD XML genereren** | Plansoftware |
| 3 | **OW-objecten koppelen** | Plansoftware (IMOW) |
| 4 | **GIO's aanmaken** | GIS-systeem (GML) |
| 5 | **Valideren** | LVBB validatie-API of lokale validator |
| 6 | **Aanleveren** | LVBB aanlever-API (HTTPS + mTLS) |
| 7 | **Bekendmaken** | LVBB publiceert op officielebekendmakingen.nl |
| 8 | **Consolideren** | LVBB consolideert in geconsolideerde regeling |
| 9 | **OW-objecten registreren** | OZON neemt OW-objecten op |

### LVBB aanlever-API

```http
POST /lvbb/api/v1/publicaties HTTP/1.1
Host: lvbb.overheid.nl
Content-Type: application/zip
Authorization: mTLS (PKIoverheid certificaat)

[ZIP-bestand met STOP XML, IMOW XML, GIO's, bijlagen]
```

## DSO API's

| API | Beschrijving | Gebruik |
|-----|-------------|--------|
| **Regels op de kaart** | Bevraag welke regels gelden op een locatie | `GET /regelsopdekaart/v4/regels?locatie=...` |
| **Activiteiten** | Zoek activiteiten in de stelselcatalogus | `GET /activiteiten/v1?zoek=bouwen` |
| **Documenten** | Raadpleeg omgevingsdocumenten | `GET /documenten/v3/{akn-id}` |
| **Vergunningaanvraag** | Dien aanvraag/melding in | `POST /verzoeken/v1/aanvragen` |
| **Toepasbare regels** | Voer vergunningcheck uit | Via Omgevingsloket |

## Implementatie-checklist

- [ ] **STOP/TPOD**: omgevingsdocumenten conform STOP XML-standaard en juist toepassingsprofiel
- [ ] **IMOW OW-objecten**: juridische regels, activiteiten, locaties correct gemodelleerd
- [ ] **GIO's**: geometrieën in GML met EPSG:28992 (RD New)
- [ ] **eId/wId**: correcte identificatie van tekstonderdelen
- [ ] **AKN-identifier**: persistente identificatie van besluiten en regelingen
- [ ] **LVBB-validatie**: documenten gevalideerd via LVBB validator voor aanlevering
- [ ] **PKIoverheid-certificaat**: mTLS-certificaat voor LVBB aanlever-API
- [ ] **Toepasbare regels**: vragenbomen conform STTR voor vergunningcheck
- [ ] **Activiteitenboom**: activiteiten gekoppeld aan bovenliggende activiteiten
- [ ] **Werkingsgebieden**: locaties correct gekoppeld aan juridische regels
- [ ] **Consolidatie**: wijzigingsbesluiten correct gestructureerd voor automatische consolidatie
- [ ] **Testen**: aansluiting getest op pre-productieomgeving DSO

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **tooi-metadata** | TOOI-thesauri en KOOP-publicaties voor overheidsdocumenten |
| **mdto-archivering** | MDTO voor archivering van omgevingsdocumenten |
| **digitoegankelijk** | WCAG-toegankelijkheid voor het Omgevingsloket |
| **overheid-authenticatie** | DigiD/eHerkenning voor authenticatie op het Omgevingsloket |

## Meer informatie

- [Aan de slag met de Omgevingswet](https://aandeslagmetdeomgevingswet.nl/) | [Ontwikkelaarsportaal](https://aandeslagmetdeomgevingswet.nl/digitaal-stelsel/technisch-aansluiten/)
- [STOP standaard](https://koop.gitlab.io/STOP/standaard/) | [TPOD](https://koop.gitlab.io/STOP/TPOD/)
- [IMOW](https://geonovum.github.io/TPOD/CIMOW/) — Informatiemodel Omgevingswet
- [STTR](https://aandeslagmetdeomgevingswet.nl/digitaal-stelsel/technisch-aansluiten/standaarden/sttr/) — Standaard Toepasbare Regels
- [LVBB](https://aandeslagmetdeomgevingswet.nl/digitaal-stelsel/technisch-aansluiten/lvbb/) — aanleverspecificatie
- [Omgevingsloket](https://omgevingswet.overheid.nl/) — portaal voor burgers en bedrijven
- [Geonovum](https://www.geonovum.nl/geo-standaarden/omgevingswet) — geo-standaarden Omgevingswet
