---
name: common-ground
version: 1.0.0
description: >
  Common Ground implementatie voor gemeenten. Open Zaak, Open Formulieren,
  Open Notificaties, Objecten API. Gebruik bij gemeentelijke
  zaakafhandeling, formulieren, of notificatie-uitwisseling.
triggers:
  keywords:
    - Common Ground
    - Open Zaak
    - Open Formulieren
    - Open Notificaties
    - Objecten API
    - Objecttypen API
    - VNG Realisatie
    - zaakafhandeling
    - gemeentelijke formulieren
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# Common Ground

Common Ground is de gemeentelijke platformstrategie voor herbruikbare,
open-source software componenten. Dit skill biedt richtlijnen voor
implementatie binnen gemeentelijke organisaties.

## Wanneer deze skill gebruiken

- Open Zaak implementatie voor zaakafhandeling
- Open Formulieren voor gemeentelijke formulieren
- Open Notificaties voor notificatie-uitwisseling
- Objecten API voor objectbeheer
- Migratie van legacy systemen naar Common Ground
- Intergemeentelijke samenwerking via Common Ground

## Componenten

### Open Zaak

Zaafhandeling conform ZGW API-standaarden:

- **Zaken API**: CRUD operaties voor zaken
- **Documenten API**: Documentbeheer bij zaken
- **Catalogi API**: Zaaktypen, documenttypen, statustypen
- **Besluiten API**: Besluiten bij zaken
- **Autorisaties API**: Toegangscontrole

Implementatie:
```yaml
# docker-compose fragment
services:
  openzaak:
    image: openzaak/openzaak:latest
    environment:
      DB_HOST: db
      DB_NAME: openzaak
      OPENZAA_SIGNING_KEY: "set-in-env-or-vault"
      ALLOWED_HOSTS: mijngemeente.nl
      OPENZAAK_DOMAIN: mijngemeente.nl:8001
      CORS_ALLOWED_ORIGINS: https://mijngemeente.nl
      IS_HTTPS: "True"
```

### Open Formulieren

Formulieren voor gemeentelijke dienstverlening:

- **Formulier-builder**: Drag-and-drop formulierontwerp
- **Multi-step formulieren**: Meerstroom formulieren
- **Betalingen**: Integratie met betalingsproviders
- **Authenticatie**: DigiD, eHerkenning, eIDAS
- **Submissie**: Automatische zaakcreatie in Open Zaak

### Open Notificaties

Notificatie-uitwisseling tussen overheidsystemen:

- **Kanalen**: email, SMS, webhook
- **Abonnementen**: Gebaseerd op gebeurtenistypen
- **Berichten**: Gestructureerde notificatie-berichten
- **Replicatie**: Multi-instance synchronisatie

### Objecten API / Objecttypen API

Beheer van objecten en objecttypen:

- **Objecten**: Wegen, panden, terreinen, monumenten
- **Objecttypen**: Definitie van object-eigenschappen
- **Geo-ondersteuning**: GeoJSON voor ruimtelijke objecten
- **Relaties**: Koppeling naar BAG, BRK, etc.

## Architectuur

```
┌─────────────────────────────────────────┐
│           Gemeentelijke Website         │
│         (Open Formulieren frontend)     │
└─────────────┬───────────────────────────┘
              │
┌─────────────▼───────────────────────────┐
│           Open Formulieren              │
│    (Formulieren + authenticatie)        │
└─────────────┬───────────────────────────┘
              │ zaak creatie
┌─────────────▼───────────────────────────┐
│             Open Zaak                   │
│   (Zaakafhandeling + Documenten)        │
└─────────────┬───────────────────────────┘
              │ notificatie
┌─────────────▼───────────────────────────┐
│          Open Notificaties              │
│     (Notificatie-uitwisseling)          │
└─────────────┬───────────────────────────┘
              │
┌─────────────▼───────────────────────────┐
│        Objecten API / Objecttypen       │
│         (Objectbeheer)                  │
└─────────────────────────────────────────┘
```

## Implementatie Stappen

### 1. Infrastructuur
- Docker Compose of Kubernetes
- PostgreSQL database
- Redis voor caching
- Reverse proxy (nginx/traefik)

### 2. Configuratie
- Domein en TLS-certificaten
- DigiD/eHerkenning koppeling
- Notificatie-kanaal configureren
- Autorisatie-profielen

### 3. Zaaktypen
- Zaaktypen definiëren in Catalogi API
- Statustypen en resultatentypen
- Documenttypen en eigenschappen
- Roltypen en behandelaars

### 4. Formulieren
- Formulieren ontwerpen in Open Formulieren
- Authenticatie-profielen koppelen
- Zaak-creatie configureren
- Betalingsflows (indien nodig)

### 5. Migratie
- Legacy data migratie
- Zaaktype-mapping
- Document-conversie
- Parallel draaien

## Compliance

### AVG
- Verwerkingsregister bijwerken
- DPIA voor nieuwe formulieren
- Data minimisation in formulieren
- Bewaartermijnen configureren

### Toegankelijkheid
- Formulieren conform WCAG 2.2
- Toegankelijkheidsverklaring
- Testen met screen readers

### Open Source
- EUPL-1.2 licentie
- Bijdragen aan upstream
- Community participatie

## Gerelateerde skills

- [gemeentelijke-iv](../gemeentelijke-iv/SKILL.md) — Gemeentelijke IV
- [zgw-apis](../zgw-apis/SKILL.md) — ZGW API-standaarden
- [digikoppeling](../digikoppeling/SKILL.md) — Digikoppeling
- [overheid-authenticatie](../overheid-authenticatie/SKILL.md) — Authenticatie
- [digitoegankelijk](../digitoegankelijk/SKILL.md) — Toegankelijkheid
- [publieke-code](../publieke-code/SKILL.md) — Open source
- [gemma-common-ground](../gemma-common-ground/SKILL.md) — GEMMA architectuur

## Bronnen

- Common Ground: commonground.nl
- Open Zaak: open-zaak.readthedocs.io
- Open Formulieren: open-forms.readthedocs.io
- VNG Realisatie: vngrealisatie.nl
- Documentatie: commonground.nl/documentatie
