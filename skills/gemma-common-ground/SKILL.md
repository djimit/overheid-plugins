---
name: gemma-common-ground
description: >-
  Helpt bij het ontwerpen en bouwen van applicaties volgens de GEMMA
  referentiearchitectuur, Common Ground principes en het Gemeentelijk
  Gegevensmodel (GGM) voor Nederlandse gemeenten. Biedt richtlijnen voor
  informatielagen, componentencatalogus, API-first ontwikkeling en
  gegevenslandschap. Gebruik deze skill wanneer de gebruiker vraagt
  over 'GEMMA', 'Common Ground', 'GGM', 'Gemeentelijk Gegevensmodel',
  'gemeentelijke architectuur', 'municipal architecture',
  'informatielagen', 'vijflagenmodel', 'five layer model',
  'GEMMA componentencatalogus', 'softwarecatalogus overheid',
  'referentiecomponent', 'applicatiefunctie',
  'NLX', 'Haven', 'FSC', 'Federated Service Connectivity',
  'zaakgericht werken architectuur', 'register component',
  'verwerking component', 'interactie component',
  'data bij de bron', 'data at the source',
  'Open Regels', 'OpenZaak', 'Open Formulieren', 'Open Notificaties',
  'Open Klant', 'Open Inwoner', 'Haal Centraal architectuur',
  'VNG Realisatie architectuur', 'GIBIT', 'gemeentelijke IT',
  of wanneer de gebruiker een applicatie wil ontwerpen of bouwen
  conform gemeentelijke standaarden en Common Ground principes.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# GEMMA & Common Ground — Gemeentelijke Architectuur

Ontwerp en bouw applicaties conform de GEMMA referentiearchitectuur en Common Ground principes voor Nederlandse gemeenten.

Bron: [GEMMA Online](https://www.gemmaonline.nl/) | [Common Ground](https://commonground.nl/) | [VNG Realisatie](https://vng.nl/rubrieken/onderwerpen/common-ground)

## Common Ground — principes

Common Ground is de informatiekundige visie van Nederlandse gemeenten voor een moderne, open, gegevensgedreven informatievoorziening.

### Kernprincipes

| Principe | Beschrijving | Praktijk |
|----------|-------------|---------|
| **Component-based** | Kleine, herbruikbare componenten i.p.v. monolithische suites | Microservices, containers |
| **Open** | Open standaarden, open source, open data | API Design Rules, EUPL-licentie |
| **Data bij de bron** | Gegevens eenmalig opslaan, meervoudig gebruiken | Geen kopieën; bevragen via API's |
| **Gelaagd** | Scheiding van interactie, proces, integratie, services en data | Vijflagenmodel |
| **Federatief** | Samenwerking zonder centralisatie | Gemeenten beheren eigen data |

### Vijflagenmodel

```
┌─────────────────────────────────────────────────┐
│  Laag 5: INTERACTIE                             │
│  Portalen, apps, formulieren (Open Formulieren) │
├─────────────────────────────────────────────────┤
│  Laag 4: PROCES                                 │
│  Zaakafhandeling, workflow (Open Zaak)          │
├─────────────────────────────────────────────────┤
│  Laag 3: INTEGRATIE                             │
│  API Gateway, notificaties, autorisatie (NLX)   │
├─────────────────────────────────────────────────┤
│  Laag 2: SERVICES                               │
│  API's, ZGW API's, Haal Centraal               │
├─────────────────────────────────────────────────┤
│  Laag 1: DATA                                   │
│  Registers, brondata (BRP, BAG, BRK)           │
└─────────────────────────────────────────────────┘
```

## GEMMA referentiearchitectuur

GEMMA (GEMeentelijke Model Architectuur) is de enterprise-architectuur voor gemeenten, gebaseerd op NORA.

### Bedrijfsfuncties

| Domein | Bedrijfsfuncties |
|--------|-----------------|
| **Dienstverlening** | Klantcontact, kanaalintegratie, formulieren |
| **Sociaal domein** | WMO, Jeugdzorg, Participatiewet, schuldhulp |
| **Ruimtelijk domein** | Vergunningen, toezicht, handhaving, omgevingsplan |
| **Publiekszaken** | Burgerzaken, reisdocumenten, rijbewijzen |
| **Bestuur & organisatie** | Raadsinformatie, besluitvorming, archivering |
| **Bedrijfsvoering** | Financien, HR, inkoop, informatiebeveiliging |

### Referentiecomponenten

| Component | Laag | Functie | Open-source implementatie |
|-----------|------|---------|--------------------------|
| **e-Formulieren** | Interactie | Online formulieren | Open Formulieren |
| **Zaakafhandelcomponent** | Proces | Zaakbehandeling | Open Zaak |
| **Klantinteractie** | Interactie | Klantcontact registreren | Open Klant |
| **Notificatiecomponent** | Integratie | Event-notificaties | Open Notificaties |
| **Portaal** | Interactie | Persoonlijke omgeving burger | Open Inwoner |
| **Regels** | Services | Bedrijfsregels-engine | Open Regels |
| **Objectregistratie** | Data | Generiek objectenregister | Objects API |
| **Documenten** | Data | Documentopslag | Documenten API (Open Zaak) |

## Open-source componenten

### Open Zaak

Referentie-implementatie van alle ZGW API's.

```yaml
# docker-compose.yml
services:
  openzaak:
    image: openzaak/open-zaak:latest
    ports:
      - "8000:8000"
    environment:
      - DB_HOST=db
      - DB_NAME=openzaak
      - SECRET_KEY=${SECRET_KEY}
      - ALLOWED_HOSTS=*
      - NOTIFICATIONS_DISABLED=false
    depends_on:
      - db
      - redis

  db:
    image: postgis/postgis:15-3.4
    environment:
      - POSTGRES_DB=openzaak
      - POSTGRES_PASSWORD=${DB_PASSWORD}

  redis:
    image: redis:7
```

### Open Formulieren

Low-code formulierenplatform met ZGW-integratie:

```yaml
services:
  openformulieren:
    image: openformulieren/open-forms:latest
    ports:
      - "9000:8000"
    environment:
      - DB_HOST=db
      - SECRET_KEY=${SECRET_KEY}
      - ALLOWED_HOSTS=*
      # Koppelingen
      - ZGW_ZAKEN_API=https://openzaak.gemeente.nl/zaken/api/v1/
      - ZGW_DOCUMENTEN_API=https://openzaak.gemeente.nl/documenten/api/v1/
      - ZGW_CATALOGI_API=https://openzaak.gemeente.nl/catalogi/api/v1/
      # DigiD
      - DIGID_METADATA_URL=https://was-preprod1.digid.nl/saml/idp/metadata
```

### Open Notificaties

Notificatie-routing voor event-driven architectuur:

```python
# Abonneren op notificaties
import httpx

async def subscribe_to_notifications():
    """Abonneer op zaakstatuswijzigingen."""
    await httpx.AsyncClient().post(
        "https://notificaties.gemeente.nl/api/v1/abonnementen",
        json={
            "callbackUrl": "https://mijn-app.gemeente.nl/webhooks/notificaties",
            "auth": "Token mijn-token",
            "kanaal": "zaken",
            "filters": {
                "zaaktype": "https://catalogi.gemeente.nl/api/v1/zaaktypen/{uuid}",
                "vertrouwelijkheidaanduiding": "openbaar"
            }
        },
        headers={"Authorization": "Token notificatie-token"}
    )
```

## Gemeentelijk Gegevensmodel (GGM)

Het GGM is het informatiemodel voor alle gemeentelijke gegevens, afgeleid van GEMMA en landelijke registraties.

### Kernentiteiten

| Entiteit | Bron | Beschrijving |
|----------|------|-------------|
| **Ingeschreven Persoon** | BRP | Natuurlijke personen (burgers) |
| **Adres** | BAG | Verblijfsobjecten, nummeraanduidingen |
| **Kadastraal Onroerende Zaak** | BRK | Percelen, appartementsrechten |
| **Maatschappelijke Activiteit** | HR | Bedrijven, KvK-registratie |
| **Zaak** | ZGW | Samenhangende hoeveelheid werk met gedefinieerde aanleiding en resultaat |
| **Document** | ZGW | Informatieobject bij een zaak |
| **Medewerker** | Eigen | Gemeentelijke medewerkers |
| **Organisatorische Eenheid** | Eigen | Afdelingen, teams |

### Relaties

```
Ingeschreven Persoon ──── woont op ────→ Adres
         │                                  │
         │                                  │
    dient in ──→ Zaak ←── betreft ──→ Kadastraal Object
                  │
                  ├── heeft ──→ Document
                  ├── heeft ──→ Status
                  └── heeft ──→ Resultaat
```

## NLX — Federated Service Connectivity

NLX (nu FSC — Federated Service Connectivity) is de integratielaag voor veilige API-communicatie tussen organisaties.

### Architectuur

```
┌──────────────┐     TLS + PKI     ┌──────────────┐
│  Gemeente A  │                   │  Gemeente B  │
│              │                   │              │
│  Applicatie  │                   │  API/Service │
│      │       │                   │      ↑       │
│  Outway ─────┼───────────────────┼── Inway      │
│  (proxy)     │                   │  (proxy)     │
└──────────────┘                   └──────────────┘
```

| Component | Functie |
|-----------|---------|
| **Inway** | Ontvangt inkomende API-verzoeken; autorisatie en logging |
| **Outway** | Verstuurt uitgaande API-verzoeken; service discovery |
| **Directory** | Centraal register van beschikbare services |
| **Management API** | Beheer van autorisaties en configuratie |

## Haven — Kubernetes-platform

Haven is de containerplatform-standaard voor gemeenten:

| Aspect | Specificatie |
|--------|-------------|
| **Basis** | Kubernetes (K8s) conform Haven-complianceprofiel |
| **Doel** | Vendor-onafhankelijk containerplatform voor Common Ground-componenten |
| **Certificering** | Haven-compliant platforms zijn uitwisselbaar |
| **Voorbeelden** | Azure AKS, AWS EKS, on-premise K8s (mits Haven-compliant) |

## Ontwikkelstandaarden

### API-standaarden

| Standaard | Beschrijving | Verplicht |
|-----------|-------------|-----------|
| **NL API Design Rules** | REST API-ontwerp (Logius) | Ja (pas-toe-of-leg-uit) |
| **OpenAPI 3.x** | API-specificatie | Ja |
| **JSON** | Standaard content-type | Ja |
| **RFC 7807** | Foutresponses (Problem Details) | Ja |
| **HAL/JSON** | Hypermedia links in responses | Aanbevolen |
| **Paginering** | Page-number of cursor-based | Ja |

### Open-source licentie

Common Ground-componenten gebruiken standaard de **EUPL-1.2** (European Union Public Licence):

| Kenmerk | EUPL-1.2 |
|---------|----------|
| Copyleft | Zwak (alleen bij distributie als geheel) |
| Compatibel met | GPL v2/v3, LGPL, MPL, AGPL |
| Juridisch | Geldig in alle 23 EU-talen |
| Gemeenschappelijk | Standaard voor Nederlandse overheid |

## Implementatie-checklist

- [ ] **Vijflagenmodel**: architectuur conform Common Ground lagenmodel
- [ ] **API-first**: alle functionaliteit ontsloten via REST API's (NL API Design Rules)
- [ ] **OpenAPI-specificatie**: API's gedocumenteerd met OpenAPI 3.x
- [ ] **Data bij de bron**: geen onnodige gegevenskopieën; bevragen via API's
- [ ] **ZGW API's**: zaakgericht werken via standaard ZGW API's
- [ ] **Notificaties**: event-driven via Open Notificaties voor asynchrone koppelingen
- [ ] **Containerisatie**: applicatie draait in containers (Docker/OCI) op Haven-compliant platform
- [ ] **Open source**: broncode beschikbaar onder EUPL-1.2 of compatibele licentie
- [ ] **GEMMA-mapping**: componenten gemapped op GEMMA referentiecomponenten
- [ ] **GGM-alignment**: gegevensmodel aansluitend op Gemeentelijk Gegevensmodel
- [ ] **NLX/FSC**: inter-organisatorische API-communicatie via NLX/FSC
- [ ] **Softwarecatalogus**: component geregistreerd in VNG softwarecatalogus
- [ ] **developer.overheid.nl**: API gepubliceerd op developer.overheid.nl

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **zgw-apis** | ZGW API-standaarden, Haal Centraal voor zaakgericht werken |
| **nora-architectuur** | NORA-principes, BIO-beveiliging, verplichte open standaarden |
| **overheid-authenticatie** | DigiD/eHerkenning voor burgerportalen en bedrijfsportalen |
| **sociaal-domein** | iStandaarden en Suwinet voor gemeentelijk sociaal domein |
| **nl-design-system** | Toegankelijke UI-componenten voor gemeentelijke applicaties |

## Meer informatie

- [GEMMA Online](https://www.gemmaonline.nl/) | [GEMMA Softwarecatalogus](https://www.softwarecatalogus.nl/)
- [Common Ground](https://commonground.nl/) | [Common Ground GitHub](https://github.com/CommonGround)
- [VNG Realisatie](https://vng.nl/rubrieken/onderwerpen/common-ground) | [VNG GitHub](https://github.com/VNG-Realisatie)
- [NLX / FSC](https://fsc.nlx.io/) — Federated Service Connectivity
- [Haven](https://haven.commonground.nl/) — containerplatform-standaard
- [Open Zaak](https://github.com/open-zaak/open-zaak) | [Open Formulieren](https://github.com/open-formulieren/open-forms)
- [Open Notificaties](https://github.com/open-zaak/open-notificaties) | [Open Klant](https://github.com/maykinmedia/open-klant)
- [Gemeentelijk Gegevensmodel](https://www.gemmaonline.nl/wiki/Gemeentelijk_Gegevensmodel)
