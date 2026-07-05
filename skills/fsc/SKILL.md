---
name: fsc
version: 1.0.0
description: >
  Federated Service Connect (FSC) voor de Nederlandse overheid.
  Standaard-framework voor veilige verbindingen tussen overheidsorganisaties.
  Gebruik bij API-koppelingen, mTLS, PKIoverheid, of Digikoppeling migratie.
triggers:
  keywords: [FSC, Federated Service Connect, PKIoverheid, mTLS, Digikoppeling migratie, API gateway]
tools: [Read, Glob, Grep, Bash]
---

# Federated Service Connect (FSC)

FSC is het nieuwe standaard-framework voor veilige verbindingen tussen Nederlandse overheidsorganisaties.

## Wanneer deze skill gebruiken

- API-koppeling tussen overheidsorganisaties
- mTLS configuratie voor service-to-service
- PKIoverheid certificaten beheren
- Migratie van Digikoppeling naar FSC
- API gateway configuratie

## FSC Architectuur

| Component | Functie | Standaard |
|-----------|---------|-----------|
| FSC Core | Identiteit en autorisatie | OAuth 2.0, OIDC |
| FSC Connect | Berichtenuitwisseling | eDelivery |
| FSC Gateway | API gateway | OAuth |
| FSC Trust | Vertrouwensrelaties | PKIoverheid |
| FSC Metadata | Service discovery | SAML, OIDC |

## PKIoverheid Certificaatketen

| Type | Gebruik | Verlener |
|------|---------|----------|
| Domein SSL | HTTPS voor overheidsdomeinen | PKIoverheid EV |
| Server | Service-authenticatie | PKIoverheid OV |
| Client | Client-authenticatie | PKIoverheid Client |
| Organisatie | Organisatie-verificatie | PKIoverheid Org |

## Digikoppeling naar FSC Migratie

| Fase | Activiteit | Duur |
|------|-----------|------|
| 1. Inventarisatie | Bestaande verbindingen in kaart | 2 weken |
| 2. PKIoverheid | Certificaten aanvragen | 1 week |
| 3. FSC Gateway | Gateway installeren | 2 weken |
| 4. Per-verbinding | Migratie per verbinding | 4 weken |
| 5. Validatie | End-to-end testing | 1 week |
| 6. Uitschakeling | Digikoppeling decommissioneren | 1 week |

## BIO2 Mapping

| BIO2 Domein | FSC Maatregel |
|-------------|---------------|
| 8.1 Cryptografie | TLS 1.3, PKIoverheid |
| 8.2 Netwerkbeveiliging | mTLS, netwerksegmentatie |
| 9.1 Toegangsbeheer | OAuth scopes, OIN |
| 10.1 Communicatie | Versleutelde verbindingen |

## Gerelateerde skills

- digikoppeling: Digikoppeling standaarden
- overheid-authenticatie: Authenticatie
- bio-security-baseline: BIO2 beveiliging
- zgw-apis: API standaarden
- eu-interoperability: EU interoperabiliteit

## Bronnen

- FSC: logius.nl
- PKIoverheid: pkioverheid.nl
- NCSC: ncsc.nl
