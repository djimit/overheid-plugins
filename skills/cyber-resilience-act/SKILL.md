---
name: cyber-resilience-act
description: >-
  Helpt bij het implementeren van de EU Cyber Resilience Act (CRA,
  Verordening (EU) 2024/2847) voor producten met digitale elementen
  bij de Nederlandse overheid. Biedt essentiële cyberbeveiligingseisen
  (Annex I), productclassificatie (standaard, belangrijk, kritiek),
  conformiteitsbeoordeling, SBOM-generatie, kwetsbaarheidsbeheer,
  meldplicht (Art. 14), CE-markering en secure-by-design patronen.
  Gebruik deze skill wanneer de gebruiker vraagt over
  'Cyber Resilience Act', 'CRA', 'CRA compliance',
  'Verordening cyberweerbaarheid', 'cyberweerbaarheid',
  'cyber resilience', 'product cybersecurity',
  'producten met digitale elementen', 'products with digital elements',
  'CRA Annex I', 'essentiële cyberbeveiligingseisen',
  'essential cybersecurity requirements',
  'CRA conformiteitsbeoordeling', 'CRA conformity assessment',
  'CE-markering software', 'CE marking software',
  'SBOM', 'Software Bill of Materials',
  'kwetsbaarheidsbeheer', 'vulnerability handling',
  'vulnerability disclosure', 'coordinated vulnerability disclosure',
  'CRA meldplicht', 'CRA reporting', 'CRA Art. 14',
  'CRA belangrijk product', 'CRA important product',
  'CRA kritiek product', 'CRA critical product',
  'secure by design', 'security by default',
  'CRA open source', 'CRA open-source steward',
  'CRA boetes', 'CRA penalties',
  'CRA NIS2', 'CRA en BIO',
  'RDI toezicht', 'NCSC meldloket CRA',
  'veiligheidsupdates', 'security updates',
  'ondersteuningsperiode', 'support period',
  of wanneer de gebruiker een product met digitale elementen
  wil laten voldoen aan de CRA-vereisten.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# Cyber Resilience Act — Producten met digitale elementen

Cyberbeveiligingseisen voor producten met digitale elementen bij de Nederlandse overheid, conform Verordening (EU) 2024/2847.

Bron: [CRA volledige tekst](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) | [EC samenvatting](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act) | [RDI](https://www.rdi.nl/onderwerpen/draadloze-apparatuur/handel-en-apparatuur/cra)

## Overzicht

| Aspect | Detail |
|--------|--------|
| **Verordening** | (EU) 2024/2847 — Verordening cyberweerbaarheid |
| **Type** | Verordening (direct werkend in alle EU-lidstaten) |
| **Focus** | Horizontale cyberbeveiligingseisen voor producten met digitale elementen |
| **Scope** | Hardware en software die op de EU-markt worden aangeboden |
| **In werking** | 10 december 2024 |
| **Meldplicht** | Vanaf 11 september 2026 (Art. 14) |
| **Volledig van toepassing** | Vanaf 11 december 2027 |
| **Toezicht NL** | RDI (conformiteit) + NCSC (meldloket/CSIRT) |
| **Boetes** | Tot €15 mln of 2,5% wereldwijde jaaromzet |

## CRA in het regelgevingslandschap

```
┌──────────────────────────────────────────────────────────────┐
│                  EU Cyberbeveiligingskader                     │
│                                                               │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────────┐│
│  │ NIS2/Cbw     │  │ CRA          │  │ EU Cybersecurity Act ││
│  │ Organisaties │  │ Producten    │  │ Certificering        ││
│  │ & processen  │  │ met digitale │  │ (EUCC, EUCS)         ││
│  │              │  │ elementen    │  │                      ││
│  └──────┬───────┘  └──────┬───────┘  └──────────┬───────────┘│
│         │                 │                      │            │
│  ┌──────┴─────────────────┴──────────────────────┴──────────┐│
│  │                BIO2 (invulling zorgplicht overheid)       ││
│  └──────────────────────────────────────────────────────────┘│
│                                                               │
│  Aanvullend: AVG | AI Act | DORA | eIDAS 2.0                │
└──────────────────────────────────────────────────────────────┘
```

| Kader | Focus | Relatie met CRA |
|-------|-------|-----------------|
| **NIS2 / Cbw** | Organisatorische beveiliging | CRA vult aan: veilige producten voor NIS2-entiteiten |
| **BIO2** | Informatiebeveiliging overheid | BIO-controls implementeren CRA-eisen intern |
| **AVG** | Persoonsgegevens | CRA beveiligt producten die persoonsgegevens verwerken |
| **AI Act** | AI-systemen | AI-systemen zijn ook producten met digitale elementen |
| **DORA** | Financiële sector | CRA geldt voor ICT-producten in financiële sector |

## Tijdlijn

```
2024-12-10          2026-06-11           2026-09-11           2027-12-11
    │                   │                    │                    │
    ▼                   ▼                    ▼                    ▼
 In werking     Conformiteits-        Meldplicht           Volledig
 getreden       beoordelings-         Art. 14              van toepassing
                organen               van kracht           (alle eisen)
                (Hfdst. IV)
```

## Productclassificatie

### Beslisboom

```
Is het een product met digitale elementen
op de EU-markt?
│
├── NEE → Buiten scope CRA
│
└── JA → Staat het product in Annex III of IV?
          │
          ├── NEE → Standaardproduct (~ 90%)
          │         → Zelfbeoordeling (interne conformiteit)
          │
          └── JA → Annex III (Belangrijk)?
                    │
                    ├── JA → Klasse I of II?
                    │        │
                    │        ├── Klasse I → Zelfbeoordeling toegestaan
                    │        │              MET geharmoniseerde norm
                    │        │              (zonder norm: derde partij)
                    │        │
                    │        └── Klasse II → Verplichte derde-partij
                    │                        conformiteitsbeoordeling
                    │
                    └── Annex IV (Kritiek)?
                         │
                         └── JA → EUCC-certificering verplicht
                                  (door conformiteitsbeoordelingsorgaan)
```

### Productcategorieën

| Categorie | Voorbeelden | Conformiteit |
|-----------|-------------|-------------|
| **Standaard** (~90%) | Tekstverwerker, foto-app, game, webshop-CMS | Zelfbeoordeling (intern) |
| **Belangrijk Klasse I** (Annex III) | Wachtwoordmanagers, browsers, OS, routers, VPN, firewalls, SIEM, microcontrollers, netwerkswitches | Zelfbeoordeling MET norm, anders derde partij |
| **Belangrijk Klasse II** (Annex III) | Hypervisors, IDS/IPS, HSM's, PKI-systemen, beveiligde elementen | Verplicht derde partij |
| **Kritiek** (Annex IV) | Smartcards, slimme-metergateway, HSM's voor kritieke infra | EUCC-certificering |

### Relevantie voor overheidsproducten

| Overheidssoftware | Waarschijnlijke categorie | Toelichting |
|-------------------|--------------------------|-------------|
| Burger-webportaal | Standaard | Informatief, geen beveiligingsfunctie |
| DigiD-integratie (authenticatie) | Belangrijk Klasse I | Authenticatiesysteem |
| Zaaksysteem (ZGW) | Standaard | Informatiesysteem |
| PKI/certificaatbeheer | Belangrijk Klasse II | PKI-systeem |
| Netwerkapparatuur (routers/switches) | Belangrijk Klasse I | Basisinfrastructuur |
| Slimme-metergateway (nutsbedrijf) | Kritiek | Annex IV |

## Essentiële cyberbeveiligingseisen (Annex I)

### Deel 1 — Producteisen

Producten met digitale elementen moeten zodanig zijn ontworpen, ontwikkeld en geproduceerd dat zij een passend niveau van cyberbeveiliging waarborgen.

| # | Eis | BIO2 control | Implementatie |
|---|-----|-------------|---------------|
| **1** | Geen bekende exploiteerbare kwetsbaarheden | BIO 12.6 | Vulnerability scanning, pentesting |
| **2** | Veilige standaardconfiguratie (secure by default) | BIO 14.1 | Hardened defaults, geen standaard-wachtwoorden |
| **3** | Kwetsbaarheden verhelpen via beveiligingsupdates | BIO 12.6 | Patch management, automatische updates |
| **4** | Bescherming tegen ongeautoriseerde toegang | BIO 9.1 | Authenticatie, autorisatie, toegangscontrole |
| **5** | Vertrouwelijkheid van opgeslagen/verzonden data | BIO 10.1 | Encryptie at rest en in transit (TLS 1.2+) |
| **6** | Integriteit van data, commando's en configuratie | BIO 10.1 | Integrity checks, signing, hash-verificatie |
| **7** | Dataminimalisatie | BIO 8.1 / AVG Art. 5(1)(c) | Alleen noodzakelijke data verwerken |
| **8** | Beschikbaarheid van essentiële functies | BIO 12.3 | Resilience, DDoS-mitigatie, failover |
| **9** | Minimale negatieve impact op andere apparaten/netwerken | BIO 12.3 | Netwerk-isolatie, rate limiting |
| **10** | Beperking van impact bij incident | BIO 16.1 | Exploit-mitigatie (ASLR, sandboxing, SELinux) |
| **11** | Beveiligingslogging en monitoring | BIO 10.3 | Audit trail, detectie van wijzigingen |
| **12** | Veilige gegevensverwijdering | BIO 8.3 / AVG Art. 17 | Secure wipe, data-export |

### Deel 2 — Kwetsbaarheidsbeheer

Fabrikanten moeten gedurende de gehele ondersteuningsperiode kwetsbaarheden effectief beheren.

| # | Eis | Implementatie |
|---|-----|---------------|
| **1** | Kwetsbaarheden en componenten identificeren en documenteren (SBOM) | CycloneDX/SPDX SBOM genereren |
| **2** | Kwetsbaarheden zonder uitstel verhelpen | Patch SLA's (kritiek: 24u, hoog: 7d) |
| **3** | Effectieve en regelmatige beveiligingstests | SAST, DAST, pentests, fuzzing |
| **4** | Informatie over verholpen kwetsbaarheden publiceren | CVE publicatie, security advisories |
| **5** | Beleid voor gecoördineerde kwetsbaarheidsonthulling | security.txt, CSAF, VEX |
| **6** | Faciliteren van het delen van kwetsbaarhedsinformatie | Contactpunt, security.txt |
| **7** | Mechanismen voor veilige distributie van updates | Gesigneerde updates, reproducible builds |
| **8** | Beveiligingsupdates gratis en onverwijld verspreiden | Automatisch updatekanaal |

## SBOM (Software Bill of Materials)

### Verplichting

De CRA verplicht fabrikanten om een SBOM op te stellen en bij te houden als onderdeel van de technische documentatie (Annex VII). De SBOM documenteert alle componenten in het product.

### Formaten

| Formaat | Standaard | Geschikt voor |
|---------|-----------|---------------|
| **CycloneDX** | OWASP | Breed, security-gefocust, VEX-ondersteuning |
| **SPDX** | Linux Foundation / ISO 5962 | Licentie-compliance, ISO-erkend |

### Generatie

```bash
# CycloneDX SBOM genereren (Python-project)
pip install cyclonedx-bom
cyclonedx-py environment \
    --output-format json \
    --output-file sbom.cdx.json

# CycloneDX SBOM genereren (Node.js-project)
npx @cyclonedx/cyclonedx-npm \
    --output-file sbom.cdx.json \
    --output-format json

# SPDX SBOM genereren (via syft)
syft . --output spdx-json=sbom.spdx.json

# SBOM valideren
cyclonedx validate --input-file sbom.cdx.json --input-format json
```

### SBOM CI/CD-integratie

```yaml
# .github/workflows/sbom.yml
name: SBOM generatie

on:
  push:
    branches: [main]
  release:
    types: [published]

jobs:
  sbom:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Genereer CycloneDX SBOM
        uses: CycloneDX/gh-python-generate-sbom@v2
        with:
          input: requirements.txt
          output: sbom.cdx.json
          format: json

      - name: Scan kwetsbaarheden in SBOM
        uses: anchore/scan-action@v6
        with:
          sbom: sbom.cdx.json
          fail-build: true
          severity-cutoff: high

      - name: Upload SBOM als release-artefact
        if: github.event_name == 'release'
        uses: softprops/action-gh-release@v2
        with:
          files: sbom.cdx.json
```

### SBOM-metadata (CRA-compliant)

```python
"""SBOM-metadata conform CRA Annex VII."""

from dataclasses import dataclass, field
from datetime import date


@dataclass
class CRASBOMMetadata:
    """Metadata die de CRA vereist bij de SBOM."""

    # Product-identificatie
    product_naam: str
    product_versie: str
    fabrikant: str
    fabrikant_contact: str

    # CRA-classificatie
    product_categorie: str  # "standaard", "belangrijk_I", "belangrijk_II", "kritiek"
    ce_markering: bool = False

    # Ondersteuningsperiode
    ondersteuning_tot: date | None = None
    ondersteuning_jaren: int = 5  # Minimaal 5 jaar

    # SBOM-details
    sbom_formaat: str = "CycloneDX"
    sbom_versie: str = "1.6"
    gegenereerd_op: date = field(default_factory=date.today)
    gegenereerd_met: str = ""

    # Componenten
    aantal_directe_deps: int = 0
    aantal_transitieve_deps: int = 0
    bekende_kwetsbaarheden: int = 0

    def is_compliant(self) -> bool:
        """Controleer of SBOM-metadata voldoet aan CRA-minimumvereisten."""
        return all([
            self.product_naam,
            self.fabrikant,
            self.fabrikant_contact,
            self.ondersteuning_tot is not None,
            self.bekende_kwetsbaarheden == 0,  # Geen bekende exploiteerbare kwetsbaarheden
            self.sbom_formaat in ("CycloneDX", "SPDX"),
        ])
```

## Kwetsbaarheidsbeheer

### Coordinated Vulnerability Disclosure (CVD)

```python
"""Kwetsbaarheidsbeheer — CRA Art. 14 en Annex I Deel 2."""

from dataclasses import dataclass, field
from datetime import datetime, timezone
from enum import Enum


class Ernst(str, Enum):
    KRITIEK = "kritiek"     # CVSS 9.0-10.0
    HOOG = "hoog"           # CVSS 7.0-8.9
    MIDDEL = "middel"       # CVSS 4.0-6.9
    LAAG = "laag"           # CVSS 0.1-3.9


class MeldingStatus(str, Enum):
    ONTDEKT = "ontdekt"
    GEANALYSEERD = "geanalyseerd"
    GEMELD_CSIRT = "gemeld_csirt"       # Vroege waarschuwing (24u)
    VOLLEDIG_GEMELD = "volledig_gemeld"  # Volledige melding (72u)
    PATCH_BESCHIKBAAR = "patch_beschikbaar"
    EINDRAPPORT = "eindrapport"         # Eindrapport (14 dagen na patch)
    AFGESLOTEN = "afgesloten"


@dataclass
class Kwetsbaarheid:
    """Registratie van een kwetsbaarheid conform CRA."""

    # Identificatie
    id: str
    product_naam: str
    product_versie: str
    component: str  # Getroffen component uit SBOM

    # Classificatie
    ernst: Ernst
    cvss_score: float
    cve_id: str | None = None
    cwe_id: str | None = None

    # Tijdlijn
    ontdekt_op: str = field(
        default_factory=lambda: datetime.now(timezone.utc).isoformat()
    )
    gemeld_csirt_op: str | None = None
    patch_beschikbaar_op: str | None = None
    eindrapport_op: str | None = None

    # Status
    status: MeldingStatus = MeldingStatus.ONTDEKT
    actief_misbruikt: bool = False

    # Details
    beschrijving: str = ""
    impact: str = ""
    mitigatie: str = ""
    patch_versie: str | None = None

    def is_meldplichtig(self) -> bool:
        """Bepaal of deze kwetsbaarheid meldplichtig is onder CRA Art. 14."""
        return self.actief_misbruikt or self.ernst == Ernst.KRITIEK

    def meldtermijn_uren(self) -> int:
        """Geef de meldtermijn in uren (vroege waarschuwing)."""
        if self.actief_misbruikt:
            return 24  # Art. 14(2)(a): 24 uur vroege waarschuwing
        return 72      # Volledige melding


# Patch SLA's (aanbevolen, conform CRA-geest)
PATCH_SLAS: dict[Ernst, dict[str, int]] = {
    Ernst.KRITIEK: {"analyse_uren": 4, "patch_dagen": 1, "uitrol_dagen": 3},
    Ernst.HOOG:    {"analyse_uren": 24, "patch_dagen": 7, "uitrol_dagen": 14},
    Ernst.MIDDEL:  {"analyse_uren": 72, "patch_dagen": 30, "uitrol_dagen": 30},
    Ernst.LAAG:    {"analyse_uren": 168, "patch_dagen": 90, "uitrol_dagen": 90},
}
```

### security.txt (RFC 9116)

```text
# /.well-known/security.txt — verplicht contactpunt CRA
Contact: mailto:security@gemeente.nl
Contact: https://gemeente.nl/security/melden
Encryption: https://gemeente.nl/.well-known/pgp-key.txt
Acknowledgments: https://gemeente.nl/security/hall-of-fame
Policy: https://gemeente.nl/security/responsible-disclosure
Preferred-Languages: nl, en
Canonical: https://gemeente.nl/.well-known/security.txt
Expires: 2027-01-01T00:00:00.000Z
# CRA — Verordening (EU) 2024/2847
CSIRT: https://www.ncsc.nl/
```

## Meldplicht (Art. 14)

### Meldprocedure

```
Kwetsbaarheid ontdekt of ernstig incident
│
├── Actief misbruikt?
│   │
│   ├── JA → Vroege waarschuwing aan CSIRT: BINNEN 24 UUR
│   │        ┌─────────────────────────────────────────────┐
│   │        │ Via ENISA Single Reporting Platform (SRP)    │
│   │        │ Aan: NCSC (coördinerend CSIRT NL)           │
│   │        │ Inhoud: product, aard kwetsbaarheid,        │
│   │        │   eerste maatregelen                         │
│   │        └─────────────────────────────────────────────┘
│   │        │
│   │        ▼
│   │        Volledige melding: BINNEN 72 UUR
│   │        ┌─────────────────────────────────────────────┐
│   │        │ Aard, ernst, impact, getroffen versies,      │
│   │        │ mitigatiemaatregelen                         │
│   │        └─────────────────────────────────────────────┘
│   │        │
│   │        ▼
│   │        Eindrapport: BINNEN 14 DAGEN na patch
│   │        ┌─────────────────────────────────────────────┐
│   │        │ Oorzaakanalyse, genomen maatregelen,        │
│   │        │ patch-informatie, CVE-referentie             │
│   │        └─────────────────────────────────────────────┘
│   │
│   └── NEE → Ernstig incident met impact op productveiligheid?
│             │
│             ├── JA → Vroege waarschuwing: 24 UUR
│             │        Volledige melding: 72 UUR
│             │        Eindrapport: BINNEN 1 MAAND
│             │
│             └── NEE → Standaard kwetsbaarheidsbeheer
│                       (fix, adviseer gebruikers, publiceer CVE)
│
└── Gebruikers informeren
    ├── Adviseer mitigatiemaatregelen
    ├── Publiceer security advisory
    └── Bied gratis beveiligingsupdate aan
```

### Nederlandse meldstructuur

| Instantie | Rol | Contact |
|-----------|-----|---------|
| **NCSC** | Coördinerend CSIRT voor NL, meldloket CRA | [ncsc.nl](https://www.ncsc.nl/) |
| **RDI** | Toezicht op conformiteit, markttoezicht | [rdi.nl](https://www.rdi.nl/) |
| **ENISA** | EU Single Reporting Platform (SRP), EUVD | [enisa.europa.eu](https://www.enisa.europa.eu/) |

## Secure-by-Design Patronen

### Secure defaults

```python
"""Secure-by-design patronen — CRA Annex I, eis 2."""

from dataclasses import dataclass


@dataclass
class SecureDefaults:
    """Veilige standaardconfiguratie voor een product met digitale elementen."""

    # Authenticatie
    wachtwoord_min_lengte: int = 14
    mfa_standaard_ingeschakeld: bool = True
    standaard_wachtwoord: str | None = None  # NOOIT een standaardwachtwoord

    # Netwerk
    onnodige_poorten_open: bool = False
    tls_minimum_versie: str = "1.2"
    https_verplicht: bool = True

    # Logging
    beveiligingslogging_ingeschakeld: bool = True
    audit_trail_ingeschakeld: bool = True

    # Updates
    automatische_updates_ingeschakeld: bool = True
    update_opt_out_mogelijk: bool = True  # CRA vereist opt-out mogelijkheid

    # Data
    dataminimalisatie: bool = True
    encryptie_at_rest: bool = True
    encryptie_in_transit: bool = True

    # Privacy
    telemetrie_standaard_uit: bool = True  # Opt-in, niet opt-out

    def valideer(self) -> list[str]:
        """Controleer of defaults voldoen aan CRA-eisen."""
        problemen = []

        if self.standaard_wachtwoord is not None:
            problemen.append(
                "CRA Annex I eis 2: standaardwachtwoorden zijn verboden"
            )

        if self.onnodige_poorten_open:
            problemen.append(
                "CRA Annex I eis 2: onnodige poorten moeten standaard dicht zijn"
            )

        if self.tls_minimum_versie < "1.2":
            problemen.append(
                "CRA Annex I eis 5 / Forum Standaardisatie: minimaal TLS 1.2"
            )

        if not self.automatische_updates_ingeschakeld:
            problemen.append(
                "CRA Annex I eis 3: automatische updates standaard ingeschakeld"
            )

        if not self.beveiligingslogging_ingeschakeld:
            problemen.append(
                "CRA Annex I eis 11: beveiligingslogging standaard ingeschakeld"
            )

        if not self.encryptie_at_rest or not self.encryptie_in_transit:
            problemen.append(
                "CRA Annex I eis 5: encryptie at rest en in transit vereist"
            )

        return problemen
```

### Security headers (webapplicaties)

```python
"""Security headers — CRA Annex I eisen 4-6, 10."""

SECURITY_HEADERS: dict[str, str] = {
    # Vertrouwelijkheid en integriteit (eis 5, 6)
    "Strict-Transport-Security": "max-age=63072000; includeSubDomains; preload",
    "Content-Security-Policy": (
        "default-src 'self'; "
        "script-src 'self'; "
        "style-src 'self'; "
        "img-src 'self' data:; "
        "frame-ancestors 'none'; "
        "base-uri 'self'; "
        "form-action 'self'"
    ),

    # Bescherming tegen ongeautoriseerde toegang (eis 4)
    "X-Content-Type-Options": "nosniff",
    "X-Frame-Options": "DENY",
    "Referrer-Policy": "strict-origin-when-cross-origin",
    "Permissions-Policy": "camera=(), microphone=(), geolocation=()",

    # Beperking van impact bij incident (eis 10)
    "Cross-Origin-Opener-Policy": "same-origin",
    "Cross-Origin-Resource-Policy": "same-origin",
    "Cross-Origin-Embedder-Policy": "require-corp",
}


def pas_security_headers_toe(response) -> None:
    """Pas CRA-conforme security headers toe op HTTP-response."""
    for header, waarde in SECURITY_HEADERS.items():
        response.headers[header] = waarde
```

## Conformiteitsbeoordeling

### Procedure per categorie

| Categorie | Procedure | Norm/Schema | Wie beoordeelt |
|-----------|-----------|-------------|---------------|
| **Standaard** | Module A (intern) | Zelfbeoordeling | Fabrikant |
| **Belangrijk I** | Module A + norm | Geharmoniseerde EN-norm | Fabrikant (met norm) |
| **Belangrijk I** (zonder norm) | Module B+C of H | EU-type-onderzoek | Aangemelde instantie |
| **Belangrijk II** | Module B+C of H | EU-type-onderzoek | Aangemelde instantie |
| **Kritiek** | EUCC-certificering | EU Common Criteria | Conformiteitsbeoordelingsorgaan |

### Zelfbeoordelingschecklist (standaardproducten)

- [ ] **Producteisen (Annex I Deel 1)**
  - [ ] Geen bekende exploiteerbare kwetsbaarheden (vulnerability scan uitgevoerd)
  - [ ] Veilige standaardconfiguratie (geen standaardwachtwoorden, onnodige diensten uit)
  - [ ] Automatische beveiligingsupdates standaard ingeschakeld (met opt-out)
  - [ ] Authenticatie en toegangscontrole geïmplementeerd
  - [ ] Encryptie at rest en in transit (TLS 1.2+)
  - [ ] Integriteitscontrole van data en configuratie
  - [ ] Dataminimalisatie toegepast
  - [ ] Beschikbaarheid essentiële functies bij incident (DDoS-bescherming)
  - [ ] Exploitatiemitigatie (ASLR, sandboxing, secure coding)
  - [ ] Beveiligingslogging en monitoring ingeschakeld
  - [ ] Veilige gegevensverwijdering mogelijk
- [ ] **Kwetsbaarheidsbeheer (Annex I Deel 2)**
  - [ ] SBOM gegenereerd en actueel (CycloneDX of SPDX)
  - [ ] Kwetsbaarheidsbeleid en -proces gedocumenteerd
  - [ ] Regelmatige beveiligingstests (SAST, DAST, pentests)
  - [ ] Coordinated Vulnerability Disclosure beleid gepubliceerd
  - [ ] security.txt conform RFC 9116 gepubliceerd
  - [ ] Mechanisme voor veilige distributie van updates (gesigneerd)
  - [ ] Beveiligingsupdates gratis beschikbaar
- [ ] **Ondersteuningsperiode**
  - [ ] Minimaal 5 jaar beveiligingsupdates gegarandeerd
  - [ ] Ondersteuningsperiode duidelijk gecommuniceerd aan gebruikers
  - [ ] Updates beschikbaar voor minimaal 10 jaar na publicatie
- [ ] **Documentatie (Annex VII)**
  - [ ] Technische documentatie opgesteld
  - [ ] SBOM opgenomen in technische documentatie
  - [ ] Risicoanalyse (cyberbeveiligingsrisico's) uitgevoerd
  - [ ] EU-conformiteitsverklaring opgesteld
- [ ] **CE-markering**
  - [ ] CE-markering aangebracht op product of verpakking
  - [ ] EU-conformiteitsverklaring beschikbaar
- [ ] **Meldplicht (Art. 14)**
  - [ ] Meldproces voor NCSC/ENISA SRP ingericht
  - [ ] Incidentresponseplan bevat CRA-meldtermijnen
  - [ ] Team getraind op 24-uurs meldplicht

## Beveiligingstests (CI/CD)

```yaml
# .github/workflows/cra_security.yml
name: CRA Security Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  # CRA Annex I Deel 1, eis 1: geen bekende kwetsbaarheden
  vulnerability-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Dependency vulnerability scan
        run: |
          pip install pip-audit
          pip-audit -r requirements.txt --strict --desc on

      - name: Container scan
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: "${{ env.IMAGE }}"
          severity: "CRITICAL,HIGH"
          exit-code: "1"

  # CRA Annex I Deel 2, eis 3: regelmatige beveiligingstests
  sast:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: SAST — Bandit
        run: bandit -r src/ -ll --format json -o bandit-report.json
      - name: SAST — Semgrep
        uses: semgrep/semgrep-action@v1
        with:
          config: p/owasp-top-ten

  # CRA Annex I Deel 2, eis 1: SBOM
  sbom:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Genereer SBOM
        run: |
          pip install cyclonedx-bom
          cyclonedx-py environment -o json --output-file sbom.cdx.json
      - name: Valideer SBOM
        run: |
          pip install cyclonedx-python-lib
          cyclonedx validate --input-file sbom.cdx.json --input-format json

  # CRA Annex I Deel 1, eis 5: encryptie
  tls-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Controleer TLS-configuratie
        run: |
          # Controleer dat geen onveilige TLS-versies worden gebruikt
          grep -r "SSLv2\|SSLv3\|TLSv1_0\|TLSv1\.0\|TLSv1_1\|TLSv1\.1" \
            --include="*.py" --include="*.yaml" --include="*.yml" \
            --include="*.conf" --include="*.json" \
            && echo "FOUT: onveilige TLS-versie gevonden" && exit 1 \
            || echo "OK: geen onveilige TLS-versies"

  # CRA Annex I Deel 1, eis 2: geen standaardwachtwoorden
  secret-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Gitleaks secret scan
        uses: gitleaks/gitleaks-action@v2
      - name: Controleer standaardwachtwoorden
        run: |
          grep -ri "password\s*=\s*['\"]" --include="*.py" --include="*.yaml" \
            --include="*.yml" --include="*.json" --include="*.env" \
            | grep -v "test\|mock\|example\|placeholder\|TODO\|FIXME" \
            && echo "FOUT: mogelijke hardcoded wachtwoorden" && exit 1 \
            || echo "OK: geen hardcoded wachtwoorden gevonden"
```

## Open-source en CRA

### Wanneer geldt de CRA voor open-source software?

```
Is de open-source software op de EU-markt beschikbaar?
│
├── NEE → Buiten scope CRA
│
└── JA → Wordt het geleverd in het kader van een commerciële activiteit?
          │
          ├── NEE (puur niet-commercieel)
          │   → Buiten scope CRA
          │   → Geen boetes voor niet-commerciële ontwikkelaars
          │
          └── JA (commercieel / geïntegreerd in commercieel product)
                │
                ├── Fabrikant integreert OSS in eigen product
                │   → Fabrikant is verantwoordelijk voor CRA-compliance
                │   → OSS-componenten moeten in SBOM staan
                │
                └── Organisatie biedt systematische ondersteuning
                    voor OSS-ontwikkeling gericht op commercieel gebruik
                    │
                    └── Open-source steward verplichtingen:
                        ├── Cyberbeveiligingsbeleid opstellen
                        ├── Samenwerken met markttoezichtautoriteiten
                        ├── Actief misbruikte kwetsbaarheden melden
                        └── GEEN boetes (Art. 64(10))
```

### Overheidsspecifiek

Publieke overheden die producten uitsluitend voor eigen gebruik ontwikkelen zijn **uitgezonderd** van de CRA. Dit geldt echter **niet** wanneer:

- De software beschikbaar wordt gesteld aan andere organisaties
- De software op een publieke markt wordt geplaatst (bijv. als open-source publicatie met commercieel doel)

Bij publicatie als open-source (bijv. onder EUPL-1.2) zonder commercieel oogmerk valt de software buiten de CRA-scope.

## Boetes

| Overtreding | Maximale boete |
|-------------|---------------|
| Niet voldoen aan essentiële cyberbeveiligingseisen (Annex I) | **€15 miljoen of 2,5% wereldwijde omzet** |
| Niet voldoen aan overige CRA-verplichtingen | **€10 miljoen of 2% wereldwijde omzet** |
| Onjuiste/onvolledige informatie aan toezichthouder | **€5 miljoen of 1% wereldwijde omzet** |
| Open-source stewards | **Geen boetes** (Art. 64(10)) |
| Mkb/micro-ondernemingen | Proportionele boetes; geen boete bij te late 24-uursmelding |

Naast boetes kan de toezichthouder (RDI) producten van de markt laten halen of een recall gelasten.

## Projectstructuur (aanbevolen)

```
product_met_digitale_elementen/
├── docs/
│   ├── cra_conformity_assessment.md   # Zelfbeoordeling (Module A)
│   ├── cybersecurity_risk_assessment.md # Risicoanalyse
│   ├── eu_declaration_of_conformity.md # EU-conformiteitsverklaring
│   ├── support_period.md              # Ondersteuningsperiode
│   └── vulnerability_disclosure_policy.md # CVD-beleid
├── security/
│   ├── security.txt                   # RFC 9116 contactpunt
│   ├── sbom.cdx.json                  # CycloneDX SBOM
│   └── vex.cdx.json                   # Vulnerability Exploitability eXchange
├── src/
│   ├── security/
│   │   ├── secure_defaults.py         # Veilige standaardconfiguratie
│   │   ├── crypto.py                  # Encryptie at rest / in transit
│   │   ├── access_control.py          # Authenticatie en autorisatie
│   │   ├── audit_logger.py            # Beveiligingslogging
│   │   └── update_manager.py          # Veilige updatedistributie
│   └── ...
├── tests/
│   ├── security/
│   │   ├── test_secure_defaults.py
│   │   ├── test_crypto.py
│   │   ├── test_access_control.py
│   │   └── test_vulnerability_scan.py
│   └── ...
├── .github/workflows/
│   ├── cra_security.yml               # CRA security pipeline
│   └── sbom.yml                       # SBOM generatie
├── .well-known/
│   └── security.txt                   # Symlink naar security/security.txt
└── SECURITY.md                        # Beveiligingsbeleid (GitHub)
```

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **llm-security** | OWASP LLM Top 10, prompt injection, DLP — voor AI-producten onder CRA |
| **genai-governance** | EU AI Act governance: AI-systemen zijn ook producten met digitale elementen |
| **nora-architectuur** | BIO2 informatiebeveiliging, verplichte standaarden, Forum Standaardisatie |
| **cloud-overheid** | BIO cloud controls, SaaS-beoordeling van ingekochte producten |
| **digitale-soevereiniteit** | CLOUD Act risico, soevereine hosting, data residency |
| **publieke-code** | Open-source publicatie: CRA-implicaties bij publicatie als OSS |
| **avg-privacy** | AVG/GDPR compliance, dataminimalisatie (CRA Annex I eis 7) |

## Meer informatie

- [CRA volledige tekst (EUR-Lex)](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) — officieel
- [EC samenvatting CRA](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act) — overzicht
- [RDI — CRA toezicht](https://www.rdi.nl/onderwerpen/draadloze-apparatuur/handel-en-apparatuur/cra) — Nederlands toezicht
- [NCSC](https://www.ncsc.nl/) — meldloket en CSIRT
- [ENISA Single Reporting Platform](https://www.enisa.europa.eu/) — EU-meldplatform
- [CycloneDX](https://cyclonedx.org/) — SBOM-standaard
- [BSI CRA-richtlijn (SBOM)](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Informationen-und-Empfehlungen/Cyber_Resilience_Act/cyber_resilience_act.html) — BSI technische richtlijn
- [Forum Standaardisatie](https://www.forumstandaardisatie.nl/) — verplichte standaarden NL
