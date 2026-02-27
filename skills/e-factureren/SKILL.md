---
name: e-factureren
description: >-
  Helpt bij het implementeren van e-facturering voor de Nederlandse overheid
  conform Peppol, SI-UBL 2.0, EN 16931 en de Europese e-factureringsrichtlijn.
  Biedt richtlijnen voor het versturen en ontvangen van elektronische facturen
  via het Peppol-netwerk. Gebruik deze skill wanneer de gebruiker vraagt
  over 'e-factureren', 'e-facturering', 'e-invoicing', 'Peppol',
  'PEPPOL', 'SI-UBL', 'UBL factuur', 'UBL invoice', 'UBL creditnota',
  'elektronische factuur', 'electronic invoice', 'EN 16931',
  'e-factureringsrichtlijn', 'e-invoicing directive',
  'Peppol Access Point', 'Peppol SMP', 'Peppol SML',
  'CIUS', 'NLCIUS', 'Simplerinvoicing',
  'OIN', 'Organisatie-identificatienummer',
  'Digipoort factuur', 'factuur overheid',
  'government invoice', 'B2G factuur',
  'inkoopfactuur overheid', 'purchase invoice',
  of wanneer de gebruiker e-facturering wil implementeren
  voor overheidstransacties of Peppol-aansluiting wil realiseren.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# E-factureren — Peppol & SI-UBL

Implementeer e-facturering voor de Nederlandse overheid conform Peppol, SI-UBL 2.0 en de Europese standaard EN 16931.

Bron: [Simplerinvoicing](https://www.simplerinvoicing.org/) | [Peppol](https://peppol.org/) | [Logius — e-Factureren](https://www.logius.nl/domeinen/e-factureren)

## Wettelijk kader

| Aspect | Detail |
|--------|--------|
| **EU-richtlijn** | Richtlijn 2014/55/EU — e-facturering bij overheidsopdrachten |
| **EU-norm** | EN 16931 — kernfactuurelementen |
| **Nederlandse CIUS** | SI-UBL 2.0 (Simplerinvoicing) — NL-specifiek profiel van EN 16931 |
| **Verplicht sinds** | April 2019 — aanbestedende diensten moeten e-facturen kunnen ontvangen |
| **Scope** | B2G (bedrijf → overheid) verplicht; B2B aanbevolen |
| **Netwerk** | Peppol — internationaal e-procurement netwerk |
| **Beheerder NL** | Logius (Peppol Authority Nederland) |

### Verplichtingen

| Wie | Verplichting |
|-----|-------------|
| **Aanbestedende diensten** (Rijk, gemeenten, provincies, waterschappen) | Moeten e-facturen kunnen **ontvangen** via Peppol |
| **Leveranciers aan overheid** | Mogen e-facturen **sturen** (niet verplicht, maar sterk aangeraden) |
| **B2B** | Niet verplicht in NL (wel in sommige EU-landen); verwachting: EU B2B-mandaat ~2028 |

## Architectuur

```
┌──────────────┐    Peppol netwerk    ┌──────────────┐
│  Leverancier │                      │   Overheid   │
│              │                      │              │
│  ERP/Boek-   │    SI-UBL 2.0       │  Financieel  │
│  houding     │                      │  systeem     │
│      │       │                      │      ↑       │
│  Access ─────┼──────────────────────┼── Access     │
│  Point (AP)  │   via SMP/SML       │  Point (AP)  │
│  (verzender) │                      │  (ontvanger) │
└──────────────┘                      └──────────────┘
```

### Peppol-componenten

| Component | Functie |
|-----------|---------|
| **Access Point (AP)** | Verstuurt en ontvangt documenten; gecertificeerd door Peppol Authority |
| **SMP** (Service Metadata Publisher) | Register: welke organisatie kan welke documenten ontvangen |
| **SML** (Service Metadata Locator) | DNS-achtig systeem dat verwijst naar de juiste SMP |
| **Peppol Directory** | Zoekservice voor deelnemers |

### Identificatie

| Type | Formaat | Voorbeeld | Gebruik |
|------|---------|-----------|--------|
| **OIN** (Organisatie-identificatienummer) | 20 cijfers | `00000001234567890000` | Overheidsorganisaties (verplicht) |
| **KvK-nummer** | 8 cijfers | `12345678` | Bedrijven |
| **BTW-nummer** | NL + 9 cijfers + B + 2 cijfers | `NL123456789B01` | Alternatief voor bedrijven |

## SI-UBL 2.0 — Factuurstandaard

SI-UBL 2.0 is het Nederlandse profiel (CIUS) van de Europese norm EN 16931, gebaseerd op UBL 2.1.

### Documenttypen

| Document | UBL-type | SI-UBL ID | Beschrijving |
|----------|---------|-----------|-------------|
| **Factuur** | `Invoice` | `urn:cen.eu:en16931:2017#compliant#urn:fdc:nen.nl:nlcius:v1.0` | Standaardfactuur |
| **Creditnota** | `CreditNote` | `urn:cen.eu:en16931:2017#compliant#urn:fdc:nen.nl:nlcius:v1.0` | Creditering |

### Verplichte elementen

| Element | XPath | Beschrijving | Voorbeeld |
|---------|-------|-------------|-----------|
| **Factuurnummer** | `cbc:ID` | Uniek factuurnummer | "INV-2026-001234" |
| **Factuurdatum** | `cbc:IssueDate` | Datum factuur | "2026-02-25" |
| **Valuta** | `cbc:DocumentCurrencyCode` | ISO 4217 | "EUR" |
| **Verkoper** | `cac:AccountingSupplierParty` | Leverancier | Naam, adres, KvK, BTW |
| **Koper** | `cac:AccountingCustomerParty` | Afnemer (overheid) | Naam, adres, OIN |
| **Factuurregel** | `cac:InvoiceLine` | Minimaal 1 regel | Omschrijving, aantal, prijs, BTW |
| **Totaalbedragen** | `cac:LegalMonetaryTotal` | Subtotaal, BTW, totaal | Rekenkundig correct |
| **BTW-uitsplitsing** | `cac:TaxTotal` | Per BTW-tarief | 21%, 9%, 0% |
| **Betaalinstructie** | `cac:PaymentMeans` | IBAN, betalingsreferentie | NL00BANK0123456789 |

### SI-UBL factuur (XML)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Invoice
  xmlns="urn:oasis:names:specification:ubl:schema:xsd:Invoice-2"
  xmlns:cac="urn:oasis:names:specification:ubl:schema:xsd:CommonAggregateComponents-2"
  xmlns:cbc="urn:oasis:names:specification:ubl:schema:xsd:CommonBasicComponents-2">

  <cbc:CustomizationID>urn:cen.eu:en16931:2017#compliant#urn:fdc:nen.nl:nlcius:v1.0</cbc:CustomizationID>
  <cbc:ProfileID>urn:fdc:peppol.eu:2017:poacc:billing:01:1.0</cbc:ProfileID>

  <cbc:ID>INV-2026-001234</cbc:ID>
  <cbc:IssueDate>2026-02-25</cbc:IssueDate>
  <cbc:DueDate>2026-03-27</cbc:DueDate>
  <cbc:InvoiceTypeCode>380</cbc:InvoiceTypeCode>
  <cbc:DocumentCurrencyCode>EUR</cbc:DocumentCurrencyCode>
  <cbc:BuyerReference>BESTELLING-2026-5678</cbc:BuyerReference>

  <!-- Verkoper (leverancier) -->
  <cac:AccountingSupplierParty>
    <cac:Party>
      <cbc:EndpointID schemeID="0106">12345678</cbc:EndpointID>
      <cac:PartyIdentification>
        <cbc:ID schemeID="0106">12345678</cbc:ID>
      </cac:PartyIdentification>
      <cac:PartyName>
        <cbc:Name>IT Leverancier B.V.</cbc:Name>
      </cac:PartyName>
      <cac:PostalAddress>
        <cbc:StreetName>Keizersgracht 100</cbc:StreetName>
        <cbc:CityName>Amsterdam</cbc:CityName>
        <cbc:PostalZone>1015AA</cbc:PostalZone>
        <cac:Country><cbc:IdentificationCode>NL</cbc:IdentificationCode></cac:Country>
      </cac:PostalAddress>
      <cac:PartyTaxScheme>
        <cbc:CompanyID>NL123456789B01</cbc:CompanyID>
        <cac:TaxScheme><cbc:ID>VAT</cbc:ID></cac:TaxScheme>
      </cac:PartyTaxScheme>
      <cac:PartyLegalEntity>
        <cbc:RegistrationName>IT Leverancier B.V.</cbc:RegistrationName>
        <cbc:CompanyID schemeID="0106">12345678</cbc:CompanyID>
      </cac:PartyLegalEntity>
    </cac:Party>
  </cac:AccountingSupplierParty>

  <!-- Koper (overheid) -->
  <cac:AccountingCustomerParty>
    <cac:Party>
      <cbc:EndpointID schemeID="0190">00000001234567890000</cbc:EndpointID>
      <cac:PartyName>
        <cbc:Name>Gemeente Amsterdam</cbc:Name>
      </cac:PartyName>
      <cac:PostalAddress>
        <cbc:StreetName>Amstel 1</cbc:StreetName>
        <cbc:CityName>Amsterdam</cbc:CityName>
        <cbc:PostalZone>1011PN</cbc:PostalZone>
        <cac:Country><cbc:IdentificationCode>NL</cbc:IdentificationCode></cac:Country>
      </cac:PostalAddress>
      <cac:PartyLegalEntity>
        <cbc:RegistrationName>Gemeente Amsterdam</cbc:RegistrationName>
      </cac:PartyLegalEntity>
    </cac:Party>
  </cac:AccountingCustomerParty>

  <!-- Betaling -->
  <cac:PaymentMeans>
    <cbc:PaymentMeansCode>30</cbc:PaymentMeansCode>
    <cac:PayeeFinancialAccount>
      <cbc:ID>NL00BANK0123456789</cbc:ID>
    </cac:PayeeFinancialAccount>
  </cac:PaymentMeans>

  <!-- BTW -->
  <cac:TaxTotal>
    <cbc:TaxAmount currencyID="EUR">2100.00</cbc:TaxAmount>
    <cac:TaxSubtotal>
      <cbc:TaxableAmount currencyID="EUR">10000.00</cbc:TaxableAmount>
      <cbc:TaxAmount currencyID="EUR">2100.00</cbc:TaxAmount>
      <cac:TaxCategory>
        <cbc:ID>S</cbc:ID>
        <cbc:Percent>21</cbc:Percent>
        <cac:TaxScheme><cbc:ID>VAT</cbc:ID></cac:TaxScheme>
      </cac:TaxCategory>
    </cac:TaxSubtotal>
  </cac:TaxTotal>

  <!-- Totalen -->
  <cac:LegalMonetaryTotal>
    <cbc:LineExtensionAmount currencyID="EUR">10000.00</cbc:LineExtensionAmount>
    <cbc:TaxExclusiveAmount currencyID="EUR">10000.00</cbc:TaxExclusiveAmount>
    <cbc:TaxInclusiveAmount currencyID="EUR">12100.00</cbc:TaxInclusiveAmount>
    <cbc:PayableAmount currencyID="EUR">12100.00</cbc:PayableAmount>
  </cac:LegalMonetaryTotal>

  <!-- Factuurregels -->
  <cac:InvoiceLine>
    <cbc:ID>1</cbc:ID>
    <cbc:InvoicedQuantity unitCode="HUR">100</cbc:InvoicedQuantity>
    <cbc:LineExtensionAmount currencyID="EUR">10000.00</cbc:LineExtensionAmount>
    <cac:Item>
      <cbc:Description>Software-ontwikkeling zaaksysteem</cbc:Description>
      <cbc:Name>Consultancy-uren</cbc:Name>
      <cac:ClassifiedTaxCategory>
        <cbc:ID>S</cbc:ID>
        <cbc:Percent>21</cbc:Percent>
        <cac:TaxScheme><cbc:ID>VAT</cbc:ID></cac:TaxScheme>
      </cac:ClassifiedTaxCategory>
    </cac:Item>
    <cac:Price>
      <cbc:PriceAmount currencyID="EUR">100.00</cbc:PriceAmount>
    </cac:Price>
  </cac:InvoiceLine>
</Invoice>
```

### Identifier-schemes

| SchemeID | Beschrijving | Gebruik |
|----------|-------------|--------|
| **0106** | KvK-nummer (8 cijfers) | Bedrijven in NL |
| **0190** | OIN (20 cijfers) | Overheidsorganisaties |
| **9944** | NL BTW-nummer | Alternatief voor bedrijven |
| **0088** | GLN (EAN) | Internationaal |

## Validatie

```bash
# Valideer SI-UBL met de officiële validator
# https://github.com/SimplerInvoicing/validation
npx si-ubl-validate factuur.xml

# Of via de online validator
# https://www.simplerinvoicing.org/validate
```

```python
from lxml import etree

def valideer_si_ubl(xml_path: str, xsd_path: str) -> list[str]:
    """Valideer een SI-UBL factuur tegen het XSD-schema."""
    schema = etree.XMLSchema(etree.parse(xsd_path))
    doc = etree.parse(xml_path)

    fouten = []
    if not schema.validate(doc):
        for error in schema.error_log:
            fouten.append(f"Regel {error.line}: {error.message}")

    # Aanvullende bedrijfsregels
    root = doc.getroot()
    ns = {"cbc": "urn:oasis:names:specification:ubl:schema:xsd:CommonBasicComponents-2"}

    # BR-NL-1: CustomizationID moet NLCIUS bevatten
    customization = root.findtext("cbc:CustomizationID", namespaces=ns)
    if customization and "nlcius" not in customization:
        fouten.append("BR-NL-1: CustomizationID moet NLCIUS-profiel bevatten")

    return fouten
```

## Peppol-aansluiting

### Aansluitopties

| Optie | Beschrijving | Geschikt voor |
|-------|-------------|---------------|
| **Via Access Point provider** | Aansluiten bij gecertificeerde AP-provider | Meeste organisaties |
| **Eigen Access Point** | Zelf Peppol AP certificeren en beheren | Grote organisaties, softwareleveranciers |
| **Via Digipoort** | Overheidsbreed ontvangsplatform (Logius) | Rijksoverheid |

### Gecertificeerde Access Points (NL)

Logius publiceert een lijst van gecertificeerde AP-providers. Kies een provider op basis van:
- SI-UBL 2.0 ondersteuning
- Volumecapaciteit
- Integratiemogelijkheden (API, SFTP, e-mail)
- SLA en support

## Implementatie-checklist

- [ ] **SI-UBL 2.0**: facturen conform SI-UBL 2.0 / EN 16931 / NLCIUS
- [ ] **Peppol-aansluiting**: gecertificeerd Access Point gekozen en aangesloten
- [ ] **OIN**: Organisatie-identificatienummer aangevraagd en geregistreerd in SMP
- [ ] **Ontvangen**: systeem kan SI-UBL facturen ontvangen en verwerken
- [ ] **Versturen**: systeem kan SI-UBL facturen genereren en versturen via Peppol
- [ ] **Validatie**: facturen gevalideerd voor verzending (XSD + bedrijfsregels)
- [ ] **Rekenkundige controle**: totalen en BTW-berekening correct
- [ ] **Identifier-schemes**: juiste schemeID's (0190 voor OIN, 0106 voor KvK)
- [ ] **Creditnota**: ondersteuning voor creditnota's (UBL CreditNote)
- [ ] **Matching**: facturen automatisch gekoppeld aan inkooporders/contracten
- [ ] **Archivering**: facturen gearchiveerd conform fiscale bewaarplicht (7 jaar)
- [ ] **Testen**: facturen getest met Peppol testomgeving en SI-UBL validator

## Meer informatie

- [Simplerinvoicing](https://www.simplerinvoicing.org/) | [SI-UBL specificatie](https://www.simplerinvoicing.org/specificatie)
- [Peppol](https://peppol.org/) | [Peppol Directory](https://directory.peppol.eu/)
- [Logius — e-Factureren](https://www.logius.nl/domeinen/e-factureren)
- [EN 16931](https://www.nen.nl/en-16931-1-2017-en-236600) — Europese kernfactuurnorm
- [EU e-factureringsrichtlijn](https://eur-lex.europa.eu/eli/dir/2014/55/oj)
- [Digipoort](https://www.logius.nl/domeinen/interactie/digipoort) — overheidsbreed ontvangstplatform
- [OIN-register](https://portaal.digikoppeling.nl/) — aanvragen OIN
