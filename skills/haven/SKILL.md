---
name: haven
version: 1.0.0
description: >
  Haven - Rijkscloud platform voor de Nederlandse overheid.
  Cloud Service Broker, Cloud Service Point, exit-strategie.
  Gebruik bij cloud-migratie, SaaS-beoordeling, of rijkscloud architectuur.
triggers:
  keywords: [Haven, rijkscloud, cloud service broker, cloud service point, SaaS beoordeling, exit strategie, cloud migratie]
tools: [Read, Glob, Grep, Bash]
---

# Haven (Rijkscloud)

Haven is het gedeelde cloud-platform voor de Nederlandse overheid.

## Wanneer deze skill gebruiken

- Cloud-migratie van overheidsapplicaties
- SaaS-beoordeling voor overheidsgebruik
- Haven architectuur ontwerpen
- Exit-strategie voor cloud-diensten
- BIO2 cloud-specifieke maatregelen

## Haven Architectuur

| Laag | Componenten | Verantwoordelijkheid |
|------|-------------|---------------------|
| 1. Strategie | Cloudbeleid, architectuur | Organisatie |
| 2. Organisatie | Governance, rollen | Organisatie |
| 3. Informatie | Data-classificatie | Organisatie |
| 4. Applicaties | Workloads, services | CSP / Organisatie |
| 5. Techniek | Infrastructuur, netwerk | CSP / CSB |

## Cloud Service Broker (CSB)

Functies: Service Discovery, Beoordeling, Afnemerschap, Monitoring, Governance.

## SaaS-Beoordelingskader

| Criterium | Gewicht |
|-----------|---------|
| BIO2 compliance | Kritiek |
| AVG compliance | Kritiek |
| Data-classificatie | Hoog |
| Exit-strategie | Hoog |
| Certificering | Middel |
| SLA | Middel |

## Exit-Strategie

1. Data-export (alle data in open format)
2. Data-migratie (naar nieuwe omgeving)
3. Verificatie (data-integriteit)
4. Wiping (veilige verwijdering bij CSP)
5. Certificatie (bevestiging van verwijdering)
6. Contractbeindiging

## BIO2 Cloud-Specifieke Maatregelen

| BIO2 Domein | Cloud Maatregel |
|-------------|-----------------|
| 5.1 Toegangsbeheer | MFA, RBAC, just-in-time |
| 6.1 Cryptografie | Versleuteling in rust en transit |
| 8.1 Operationeel | Logging, monitoring |
| 9.1 Externe partijen | CSP assessment |
| 10.1 Continuiteit | Multi-region, backup, DR |

## Gerelateerde skills

- cloud-overheid: Rijkscloudbeleid
- bio-security-baseline: BIO2
- digitale-soevereiniteit: Soevereiniteit
- avg-privacy: AVG
- eu-interoperability: EU

## Bronnen

- Haven: haven.logius.nl
- Cloudbeleid: rijksoverheid.nl
