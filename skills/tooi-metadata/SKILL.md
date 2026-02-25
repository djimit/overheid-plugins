---
name: tooi-metadata
description: >-
  Helpt bij het werken met TOOI (Thesauri en Ontologieen voor
  Overheidsinformatie), de Woo (Wet open overheid) en het publiceren van
  overheidsdocumenten volgens het KOOP-publicatieplatform. Biedt richtlijnen
  voor metadata-standaarden, waardelijsten, identificatie-URI's en
  Woo-categorisering. Gebruik deze skill wanneer de gebruiker vraagt
  over 'TOOI', 'Woo', 'Wet open overheid', 'WOB', 'openbaarheid',
  'overheidsinformatie publiceren', 'KOOP', 'publicatieplatform overheid',
  'officielebekendmakingen', 'wetten.overheid.nl', 'open.overheid.nl',
  'overheid.nl metadata', 'BWB', 'JCDR', 'CVDR',
  'waardelijst overheid', 'thesaurus overheid',
  'informatiecategorie Woo', 'actieve openbaarmaking',
  'TOP-lijst', 'register Woo', 'Woo-verzoek', 'Woo-besluit',
  'publicatieplicht', 'Staatscourant', 'Gemeenteblad', 'Provinciaal blad',
  'STOP standaard', 'TPOD', 'juriconnect', 'overheidsidentificatie',
  'identifier overheid', 'URI-strategie overheid',
  of wanneer de gebruiker overheidsdocumenten wil publiceren of
  metadata wil structureren volgens Nederlandse overheidsstandaarden.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
  - Bash(curl *)
---

# TOOI & Wet open overheid (Woo) — Overheidsinformatie publiceren

Structureer, categoriseer en publiceer overheidsinformatie conform TOOI-standaarden en de Wet open overheid.

Bron: [TOOI — KOOP](https://tardis.gitbook.io/tooi) | [Woo (wetten.overheid.nl)](https://wetten.overheid.nl/BWBR0045754) | [open.overheid.nl](https://open.overheid.nl/)

## Wettelijk kader — Wet open overheid (Woo)

| Aspect | Detail |
|--------|--------|
| **Wet** | Wet open overheid (Woo), in werking sinds 1 mei 2022 (vervangt Wob) |
| **Doel** | Transparante overheid; actieve en passieve openbaarmaking van overheidsinformatie |
| **Scope** | Alle bestuursorganen: Rijk, provincies, gemeenten, waterschappen, ZBO's |
| **Beheerder** | Ministerie van BZK; uitvoering via KOOP (Kennis- en Exploitatiecentrum Officiele Overheidspublicaties) |
| **Platform** | open.overheid.nl (Woo-index), officielebekendmakingen.nl, wetten.overheid.nl |

### Woo-informatiecategorieen (Art. 3.3)

De Woo definieert 17 informatiecategorieen voor actieve openbaarmaking:

| # | Categorie | Voorbeeld |
|---|-----------|-----------|
| 1 | **Wet- en regelgeving** | Wetten, AMvB's, verordeningen |
| 2 | **Organisatiegegevens** | Organogrammen, taken, bevoegdheden |
| 3 | **Raadsstukken** | Agenda's, verslagen gemeenteraad |
| 4 | **Bestuursstukken** | College- en GS-besluiten |
| 5 | **Stukken van adviescolleges** | Adviezen, rapporten |
| 6 | **Convenanten** | Samenwerkingsafspraken |
| 7 | **Jaarplannen en -verslagen** | Begrotingen, jaarrekeningen |
| 8 | **Woo-verzoeken en -besluiten** | Verzoeken en besluiten tot openbaarmaking |
| 9 | **Onderzoeksrapporten** | Beleidsonderzoeken, evaluaties |
| 10 | **Beschikkingen** | Vergunningen, subsidiebesluiten |
| 11 | **Klachten** | Klachtoordelen |
| 12 | **Bereikbaarheidsgegevens** | Contactinformatie bestuursorgaan |
| 13 | **Vergaderstukken decentraal** | Stukken gemeenteraad, provinciale staten, waterschapsbestuur |
| 14 | **Agenda's en besluitenlijsten** | Bestuursvergaderingen |
| 15 | **WOB/Woo-verzoeken** | Historische verzoeken |
| 16 | **ECER-adviezen** | Europees-rechtelijke adviezen |
| 17 | **Overige bij AMvB aangewezen** | Nader te bepalen categorieën |

### Woo-verzoek afhandeling

| Stap | Termijn | Beschrijving |
|------|---------|-------------|
| Ontvangst | Dag 0 | Registratie en bevestiging ontvangst |
| Beoordeling | — | Reikwijdte bepalen; eventueel verduidelijking vragen |
| Besluit | **4 weken** | Besluit tot (gedeeltelijke) openbaarmaking of weigering |
| Verlenging | +2 weken | Mogelijk bij omvangrijk/complex verzoek |
| Bezwaar | 6 weken | Bezwaartermijn na besluit |

### Uitzonderingsgronden (Art. 5.1-5.5)

| Type | Grond | Toelichting |
|------|-------|-------------|
| **Absoluut** | Eenheid van de Kroon | Nooit openbaar |
| **Absoluut** | Veiligheid van de Staat | Nooit openbaar |
| **Relatief** | Persoonlijke levenssfeer | Afweging openbaar belang vs privacy |
| **Relatief** | Bedrijfs- en fabricagegegevens | Vertrouwelijk meegedeeld |
| **Relatief** | Opsporing en vervolging | Lopende onderzoeken |
| **Relatief** | Inspectie en toezicht | Effectiviteit toezicht |
| **Relatief** | Persoonlijke beleidsopvattingen | In documenten voor intern beraad |

## TOOI — Thesauri en Ontologieen

TOOI is het stelsel van identificatiesystemen, thesauri en waardelijsten voor overheidsinformatie, beheerd door KOOP.

### Kerncomponenten

| Component | Beschrijving | Voorbeeld |
|-----------|-------------|-----------|
| **Organisatie-register** | Alle overheidsorganisaties met unieke identifier | `tooi-org:mnre1034` (Min. van BZK) |
| **Waardelijsten** | Gestandaardiseerde lijsten voor metadatawaarden | Informatiecategorieën, documentsoorten, thema's |
| **Thesaurus** | Gecontroleerde trefwoordenlijst voor overheidsonderwerpen | `tooi:c_0001` (Bestuur) |
| **Identifier-stelsel** | URI's voor overheidsdocumenten en -organisaties | BWB-id, CVDR-id, JCDR-id |

### TOOI-identifiers

| Type | Patroon | Voorbeeld |
|------|---------|-----------|
| **Organisatie** | `tooi-org:{code}` | `tooi-org:gem0363` (Amsterdam) |
| **BWB** (wet/regelgeving) | `bwb-id:{BWBR-nummer}` | `BWBR0045754` (Woo) |
| **CVDR** (decentrale regelgeving) | `cvdr-id:{nummer}` | `CVDR123456_1` |
| **Bekendmaking** | `gmb-{jaar}-{nummer}` | `gmb-2026-12345` |
| **Work-identifier** | `/tooi/id/work/{type}/{nummer}` | `/tooi/id/work/beschikking/2026/001` |

### TOOI API — organisaties opvragen

```http
GET /tooi/api/v1/organisaties?type=gemeente&naam=Amsterdam HTTP/1.1
Host: identifier.overheid.nl
Accept: application/json
```

**Response:**
```json
{
  "organisaties": [
    {
      "identifier": "tooi-org:gem0363",
      "naam": "Gemeente Amsterdam",
      "type": "gemeente",
      "cbsCode": "0363",
      "provincie": "Noord-Holland"
    }
  ]
}
```

### TOOI waardelijsten gebruiken

```python
# Informatiecategorieen Woo (waardelijst)
WOO_CATEGORIEEN = {
    "c_01": "Wet- en regelgeving",
    "c_02": "Organisatiegegevens",
    "c_03": "Raadsstukken",
    "c_04": "Bestuursstukken",
    "c_05": "Stukken adviescolleges",
    "c_06": "Convenanten",
    "c_07": "Jaarplannen en -verslagen",
    "c_08": "Woo-verzoeken en -besluiten",
    "c_09": "Onderzoeksrapporten",
    "c_10": "Beschikkingen",
    "c_11": "Klachten",
}

# Documentsoorten
DOCUMENT_SOORTEN = {
    "beschikking": "Beschikking",
    "verordening": "Verordening",
    "beleidsregel": "Beleidsregel",
    "convenant": "Convenant",
    "rapport": "Rapport",
    "brief": "Brief",
    "vergaderstuk": "Vergaderstuk",
}
```

## Publiceren op overheidsplatforms

### Publicatiekanalen

| Platform | Type publicaties | Standaard |
|----------|-----------------|-----------|
| **officielebekendmakingen.nl** | Staatscourant, Gemeenteblad, Provinciaal Blad, Waterschapsblad | STOP/TPOD XML |
| **wetten.overheid.nl** | Geconsolideerde wet- en regelgeving | BWB XML |
| **open.overheid.nl** | Woo-documenten (actieve openbaarmaking) | TOOI-metadata + PDF |
| **zoek.officielebekendmakingen.nl** | Zoekinterface voor alle bekendmakingen | — |

### Metadata voor Woo-publicatie

```json
{
  "document": {
    "identifier": "/tooi/id/work/beschikking/gem0363/2026/001",
    "titel": "Omgevingsvergunning Hoofdstraat 1",
    "creatiedatum": "2026-02-25",
    "informatiecategorie": "c_10",
    "documentsoort": "beschikking",
    "publisher": {
      "identifier": "tooi-org:gem0363",
      "naam": "Gemeente Amsterdam"
    },
    "onderwerp": ["omgevingsvergunning", "bouwen"],
    "taal": "nld",
    "format": "application/pdf",
    "openbaarheid": "openbaar",
    "geldigheid": {
      "begindatum": "2026-02-25"
    }
  }
}
```

### Officiele Bekendmakingen — STOP XML

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Bekendmaking xmlns="https://standaarden.overheid.nl/stop/imop/tekst/">
  <RegelingMetadata>
    <informatieobjectRef>/tooi/id/work/verordening/gem0363/2026/001</informatieobjectRef>
    <eindverantwoordelijke>tooi-org:gem0363</eindverantwoordelijke>
    <maker>tooi-org:gem0363</maker>
    <soortWork>/tooi/def/thes/kern/verordening</soortWork>
    <officieleTitel>Verordening fysieke leefomgeving Gemeente Amsterdam</officieleTitel>
  </RegelingMetadata>
</Bekendmaking>
```

## URI-strategie Nederlandse overheid

De [URI-strategie](https://aandeslagmetdeomgevingswet.nl/digitaal-stelsel/technisch-aansluiten/standaarden/uri-strategie/) voor persistente identificatie:

| Patroon | Gebruik | Voorbeeld |
|---------|---------|-----------|
| `http://standaarden.overheid.nl/owms/terms/{term}` | OWMS-termen | Informatiecategorieen, thema's |
| `https://identifier.overheid.nl/tooi/id/{type}/{code}` | TOOI-identifiers | Organisaties, documenten |
| `https://zoek.officielebekendmakingen.nl/{publicatie-id}` | Bekendmakingen | gmb-2026-12345 |
| `https://wetten.overheid.nl/{BWB-id}` | Wet- en regelgeving | BWBR0045754 |

## Implementatie-checklist

- [ ] **Woo-categorie**: elk document gekoppeld aan juiste informatiecategorie (Art. 3.3)
- [ ] **TOOI-identifier**: unieke, persistente identifier per document en organisatie
- [ ] **Metadata**: alle verplichte velden ingevuld (titel, creatiedatum, categorie, publisher, taal)
- [ ] **Organisatie-register**: eigen organisatie correct geidentificeerd met TOOI-org code
- [ ] **Waardelijsten**: gebruik standaard TOOI-waardelijsten voor documentsoort, thema, categorie
- [ ] **Publicatiekanaal**: juist platform gekozen (open.overheid.nl voor Woo, officielebekendmakingen.nl voor regelgeving)
- [ ] **Openbaarheid**: uitzonderingsgronden correct toegepast en gedocumenteerd
- [ ] **Woo-register**: index van openbaar gemaakte documenten gepubliceerd
- [ ] **Feedbackmechanisme**: mogelijkheid voor burgers om verzoeken in te dienen
- [ ] **Duurzame formaten**: documenten in PDF/A voor langetermijntoegankelijkheid
- [ ] **Taalcode**: ISO 639-2 taalcode (nld, eng, fry) bij elk document
- [ ] **Doorzoekbaarheid**: full-text zoeken op gepubliceerde documenten

## Meer informatie

- [TOOI — KOOP](https://tardis.gitbook.io/tooi) | [TOOI identifier-register](https://identifier.overheid.nl/)
- [Wet open overheid](https://wetten.overheid.nl/BWBR0045754) | [Woo uitleg Rijksoverheid](https://www.rijksoverheid.nl/onderwerpen/wet-open-overheid-woo)
- [open.overheid.nl](https://open.overheid.nl/) — platform voor actieve openbaarmaking
- [KOOP](https://www.koopoverheid.nl/) — Kennis- en Exploitatiecentrum Officiele Overheidspublicaties
- [STOP standaard](https://koop.gitlab.io/STOP/standaard/) — Standaard voor Officiële Publicaties
- [OWMS](https://standaarden.overheid.nl/owms) — Overheid.nl Web Metadata Standaard
