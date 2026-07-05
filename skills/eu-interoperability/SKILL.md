---
name: eu-interoperability
version: 1.0.0
description: >
  EU interoperabiliteit voor Nederlandse overheid. EIF mapping, EUDI Wallet,
  Once-Only Principle, en Europese standaarden. Gebruik bij cross-border
  dienstverlening, EU-funded projecten, of Europese compliance.
triggers:
  keywords:
    - EU
    - interoperability
    - EIF
    - EUDI
    - EUDI Wallet
    - once-only
    - cross-border
    - European
    - EUR-Lex
    - EIRA
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# EU Interoperabiliteit

Europese interoperabiliteit voor de Nederlandse overheid. Dit skill biedt
richtlijnen voor het voldoen aan Europese standaarden en het aansluiten
op EU-diensten.

## Wanneer deze skill gebruiken

- Cross-border dienstverlening (EU-burgers bedienen)
- EU-funded projecten (Horizon Europe, Digital Europe)
- EUDI Wallet implementatie
- Once-Only Principle compliance
- Europese architectuur-review (EIF/EIRA)
- EU-verordeningen implementeren

## European Interoperability Framework (EIF)

Het EIF is het Europese equivalent van NORA. De 4 lagen:

| Laag | EIF | Nederlandse equivalent |
|------|-----|----------------------|
| Juridisch | EU-verordeningen | Wetten, AMvB |
| Organisatief | Samenwerkingsafspraken | Beleidsafspraken |
| Semantisch | Data-uitwisseling | ZGW, Digikoppeling |
| Technisch | API's, standaarden | API Design Rules |

### EIF Principes

1. **Subsidiariteit en proportionaliteit**
2. **Openheid** — Open standaarden, open source
3. **Transparantie** — Hergebruik, open data
4. **Hergebruik** — Bestaande oplossingen prefereren
5. **Technologische neutraliteit**
6. **Gebruikersgerichtheid**
7. **Toegankelijkheid en inclusie**
8. **Veiligheid en privacy**
9. **Meertaligheid**
1. **Administratieve vereenvoudiging**

## EIRA (European Interoperability Reference Architecture)

EIRA is het Europese equivalent van GEMMA:
- **CAMSS** (Common Assessment Method for Standards and Specifications)
- **EIF Building Blocks**: Legal, Organisational, Semantic, Technical
- **NORA ↔ EIRA mapping**: 1-op-1 te vertalen

## EUDI Wallet (European Digital Identity Wallet)

Verordening (EU) 2024/1183 — elke EU-lidstaat moet een EUDI Wallet aanbieden.

### Wat het biedt

- **PID** (Person Identification Data): Naam, geboortedatum, nationaliteit
- **Attestations**: Diploma's, rijbewijzen, medische gegevens
- **Qualified Electronic Signatures**: QES voor juridische documenten
- **Selective Disclosure**: Alleen delen wat nodig is

### Nederlandse Implementatie

- **DigiD → EUDI Wallet**: Migratiepad van DigiD naar Wallet-gebaseerde auth
- **eHerkenning → EUDI Wallet**: Bedrijfsidentificatie via Wallet
- **Attributes**: BSN → PID, KvK-nummer → Attestatie

### Technische Standataarden

- **ISO 18013-5**: Mobile Driving License (mDL)
- **W3C Verifiable Credentials**: Voor attestaties
- **OpenID4VCI**: Credential Issuance
- **OpenID4VP**: Credential Presentation
- **SD-JWT**: Selective Disclosure JWT

## Once-Only Principle

EU verplichting: burgers en bedrijven hoeven informatie maar één keer
aan te leveren aan overheidsinstanties.

### Nederlandse Implementatie

- **Haal Centraal**: Basisregistraties (BRP, BAG, BRK, HR, WOZ)
- **Stelsel van Basisregistraties**: 13 basisregistraties
- **eHerkenning**: Eenmalig inloggen voor bedrijven
- **MijnOverheid**: Persoonlijk dossier voor burgers

### Technische Implementatie

- **eDelivery**: Veilige berichtuitwisseling
- **eID**: Europese elektronische identificatie
- **eSignature**: Elektronische handtekeningen
- **eInvoicing**: Peppol/SI-UBL (zie e-factureren skill)

## EU Verordeningen Relevant voor Nederland

| Verordening | Artikel | Relevantie |
|-------------|---------|------------|
| EU AI Act (2024/1689) | Hoog-risico AI | genai-governance, algoritmekader |
| GDPR (2016/679) | Data protection | avg-privacy, dpia-assessment |
| eIDAS 2.0 (2024/1183) | Digitale identiteit | overheid-authenticatie |
| Data Act (2023/2854) | Data deling | open-data |
| Cyber Resilience Act (2024/2847) | Productbeveiliging | bio-security-baseline |
| NIS2 (2022/2555) | Netwerkbeveiliging | bio-security-baseline |
| Digital Markets Act | Platformregulering | algoritmekader |
| Data Governance Act | Data gouvernance | open-data |

## EU Standaarden voor Overheidssoftware

| Standaard | Toepassing | Nederlandse mapping |
|-----------|-----------|-------------------|
| INSPIRE | Ruimtelijke data | geo-ruimtelijke-iv |
| DCAT-AP | Data catalogi | open-data |
| Core Vocabuliaries | Overheidsdata | open-data |
| ELI (European Legislation Identifier) | Wetgeving | tooi-metadata |
| ECLI (European Case Law Identifier) | Rechtspraak | tooi-metadata |
| Peppol | E-invoicing | e-factureren |
| eDelivery | Berichten | digikoppeling |
| CEF Digital | Building blocks | eu-interoperability |

## Cross-Border Dienstverlening

### Scenario: EU-burger wil in NL werken

1. **EUDI Wallet**: Burger toont attestatie arbeidsvergunning
2. **eID**: Identificatie via eigen lidstaat
3. **Cross-border API**: NL systeem valideert attestatie
4. **Once-Only**: Geen dubbele gegevenslevering

### Scenario: NL-bedrijf exporteert naar DE

1. **eInvoicing**: Peppol factuur naar Duitse klant
2. **EORI**: Economische Operateur Registratie Identificatie
3. **CE Marking**: Productcertificering
4. **GDPR**: Data transfer buiten EU (adequacy decision)

## Gerelateerde skills

- [nora-architectuur](../nora-architectuur/SKILL.md) — NORA principes
- [overheid-authenticatie](../overheid-authenticatie/SKILL.md) — DigiD/eHerkenning
- [open-data](../open-data/SKILL.md) — DCAT-AP
- [e-factureren](../e-factureren/SKILL.md) — Peppol
- [genai-governance](../genai-governance/SKILL.md) — EU AI Act
- [algoritmekader](../algoritmekader/SKILL.md) — Algoritme compliance
- [digikoppeling](../digikoppeling/SKILL.md) — Berichtenstandaarden
- [tooi-metadata](../tooi-metadata/SKILL.md) — ELI/ECLI
- [avg-privacy](../avg-privacy/SKILL.md) — GDPR

## Bronnen

- EIF: joinup.ec.europa.eu/solution/eif
- EUDI Wallet: digital-strategy.ec.europa.eu/en/policies/eudi-wallet
- EIRA: joinup.ec.europa.eu/solution/eira
- EUR-Lex: eur-lex.europa.eu
- CEF Digital: cefdigital.ec.europa.eu
- Peppol: peppol.eu
- INSPIRE: inspire.ec.europa.eu
