---
name: digitale-soevereiniteit
description: >-
  Helpt bij het implementeren van digitale soevereiniteit voor
  AI- en cloudsystemen bij de Nederlandse overheid. Biedt
  CLOUD Act risicoanalyse, soevereine hosting beslisboom,
  BIV-classificatie voor AI-data, data residency enforcement,
  on-premise LLM opties, mTLS voor soevereine endpoints,
  en verwerkersovereenkomst-clausules.
  Gebruik deze skill wanneer de gebruiker vraagt over
  'digitale soevereiniteit', 'digital sovereignty',
  'CLOUD Act', 'Cloud Act risico',
  'soevereine cloud', 'sovereign cloud',
  'data soevereiniteit', 'data sovereignty',
  'data residency', 'data localisatie',
  'BIV classificatie', 'BIV-classificatie',
  'beschikbaarheid integriteit vertrouwelijkheid',
  'soeverein model', 'sovereign model',
  'on-premise LLM', 'on-prem LLM', 'self-hosted LLM',
  'Ollama', 'vLLM overheid',
  'CLOUD Act beslisboom', 'CLOUD Act decision tree',
  'verwerkersovereenkomst AI', 'DPA AI',
  'US jurisdictie', 'Schrems',
  'data residency EU', 'data locatie overheid',
  'Diginetwerk hosting', 'Haagse Ring',
  'soevereine verwerking', 'sovereign processing',
  of wanneer de gebruiker wil beoordelen waar AI-workloads
  mogen draaien op basis van dataclassificatie en jurisdictie.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# Digitale Soevereiniteit — AI & Cloud bij de overheid

Data-soevereiniteit voor AI- en cloudsystemen bij de Nederlandse overheid. CLOUD Act risicoanalyse, soevereine hosting, BIV-classificatie en verwerkersovereenkomsten.

Bron: [Rijkscloudbeleid](https://www.rijksoverheid.nl/onderwerpen/digitale-overheid) | [BIO2](https://bio-overheid.nl/) | [NCSC](https://www.ncsc.nl/)

## Waarom digitale soevereiniteit voor AI?

| Risico | Toelichting | Regulering |
|--------|------------|------------|
| **CLOUD Act** | US-gevestigde providers kunnen door de US overheid gedwongen worden data te verstrekken, ook als deze in de EU is opgeslagen | CLOUD Act 2018 |
| **Schrems II** | Adequaatheidsbesluit EU-US DPF biedt geen garantie voor overheidsdata | HvJEU C-311/18, EU-US DPF |
| **Data residency** | Overheidsdata mag niet buiten de EU verwerkt worden zonder adequate waarborgen | AVG Art. 44-49 |
| **AI Act** | Hoog-risico AI vereist logging, audit trail en transparantie — extra risico bij externe hosting | EU AI Act Art. 12 |
| **NIS2** | Essentiële diensten moeten supply chain risico's beheersen | NIS2 / Cyberbeveiligingswet Art. 21 |

## CLOUD Act Beslisboom

```
Is data geclassificeerd als VERTROUWELIJK of hoger?
│
├── JA → Soeverein model (on-prem / EU-soeverein)
│        Geen US-provider, geen CLOUD Act risico
│
└── NEE → Bevat de data AVG bijzondere categorieen?
          │
          ├── JA → Soeverein model (on-prem / EU-soeverein)
          │        Art. 9 AVG: extra bescherming vereist
          │
          └── NEE → Is EU data residency contractueel gegarandeerd?
                    │
                    ├── JA → EU-gehoste provider toegestaan
                    │        (bijv. Azure EU, Anthropic EU)
                    │        MET verwerkersovereenkomst + DPIA
                    │
                    └── NEE → BLOKKEER — escaleer naar CISO
                             Geen verwerking zonder waarborgen
```

## BIV-classificatie voor AI-data

### Classificatieniveaus

| Niveau | Label | Beschrijving | AI-verwerking |
|--------|-------|-------------|---------------|
| **BBN1** | OPENBAAR | Openbare informatie | Elk model toegestaan |
| **BBN2** | INTERN | Interne informatie, niet openbaar | EU-gehost model met DPA |
| **BBN2+** | VERTROUWELIJK | Gevoelig, beperkte toegang | Soeverein model of EU met strikte DPA |
| **BBN3** | GEHEIM | Staatsgeheim of vergelijkbaar | Alleen on-prem soeverein model |

### Data-classificatiematrix voor LLM-input

| Datatype | Voorbeeld | Classificatie | Toegestaan model |
|----------|-----------|--------------|-----------------|
| Openbare informatie | Gepubliceerd beleid, wetteksten | OPENBAAR | Elk model |
| Interne documenten | Interne notities, conceptbeleid | INTERN | EU-gehost |
| Persoonsgegevens | Naam + adres, BSN | VERTROUWELIJK | Soeverein of EU met DPA |
| Bijzondere categorieen | Gezondheid, strafrechtelijk | GEHEIM | Alleen soeverein |
| Gerechtelijke stukken | Rechterlijke uitspraken (ongepubl.) | GEHEIM | Alleen soeverein |
| Staatsgeheimen | Gerubriceerde informatie | GEHEIM | NIET via LLM |

## Soevereine Model Routing

### Architectuur

```
┌─────────────────────────────────────────────────────────┐
│                   Model Router                           │
│                                                          │
│  Input: data + classificatie                             │
│       │                                                  │
│       ├── OPENBAAR ──────────→ Claude / Azure OpenAI     │
│       │                        (EU region)               │
│       │                                                  │
│       ├── INTERN ────────────→ Azure OpenAI              │
│       │                        (NL/SE region + DPA)      │
│       │                                                  │
│       ├── VERTROUWELIJK ─────→ On-prem Llama / Mistral   │
│       │                        (Ollama / vLLM)           │
│       │                                                  │
│       └── GEHEIM ────────────→ Air-gapped on-prem       │
│                                (Diginetwerk / Haagse     │
│                                 Ring)                    │
└─────────────────────────────────────────────────────────┘
```

### Implementatie

```python
"""Soevereine model router — routeert LLM-verzoeken op basis van dataclassificatie."""

from dataclasses import dataclass
from enum import Enum
from typing import Any

import httpx


class Classificatie(str, Enum):
    OPENBAAR = "OPENBAAR"
    INTERN = "INTERN"
    VERTROUWELIJK = "VERTROUWELIJK"
    GEHEIM = "GEHEIM"


class ModelEndpoint(str, Enum):
    CLAUDE_EU = "claude_eu"
    AZURE_OAI_EU = "azure_oai_eu"
    SOVEREIGN_OLLAMA = "sovereign_ollama"
    SOVEREIGN_VLLM = "sovereign_vllm"
    GEBLOKKEERD = "geblokkeerd"


@dataclass
class RoutingBesluit:
    endpoint: ModelEndpoint
    reden: str
    cloud_act_risico: bool
    dpa_vereist: bool


# Routing-regels per classificatie
ROUTING_REGELS: dict[Classificatie, list[ModelEndpoint]] = {
    Classificatie.OPENBAAR: [
        ModelEndpoint.CLAUDE_EU,
        ModelEndpoint.AZURE_OAI_EU,
        ModelEndpoint.SOVEREIGN_OLLAMA,
    ],
    Classificatie.INTERN: [
        ModelEndpoint.AZURE_OAI_EU,
        ModelEndpoint.SOVEREIGN_OLLAMA,
    ],
    Classificatie.VERTROUWELIJK: [
        ModelEndpoint.SOVEREIGN_OLLAMA,
        ModelEndpoint.SOVEREIGN_VLLM,
    ],
    Classificatie.GEHEIM: [
        ModelEndpoint.SOVEREIGN_VLLM,  # Air-gapped
    ],
}


def bepaal_routing(classificatie: Classificatie) -> RoutingBesluit:
    """Bepaal welk model-endpoint te gebruiken op basis van classificatie."""
    toegestane_endpoints = ROUTING_REGELS.get(classificatie, [])

    if not toegestane_endpoints:
        return RoutingBesluit(
            endpoint=ModelEndpoint.GEBLOKKEERD,
            reden=f"Geen model toegestaan voor classificatie {classificatie}",
            cloud_act_risico=False,
            dpa_vereist=False,
        )

    endpoint = toegestane_endpoints[0]  # Eerste voorkeur

    cloud_act = endpoint in (ModelEndpoint.CLAUDE_EU, ModelEndpoint.AZURE_OAI_EU)
    dpa = endpoint in (ModelEndpoint.CLAUDE_EU, ModelEndpoint.AZURE_OAI_EU)

    return RoutingBesluit(
        endpoint=endpoint,
        reden=f"Classificatie {classificatie} → {endpoint.value}",
        cloud_act_risico=cloud_act,
        dpa_vereist=dpa,
    )


@dataclass
class EndpointConfig:
    naam: str
    base_url: str
    model_id: str
    cloud_act_risico: bool
    hosting_locatie: str
    soevereiniteit: str


ENDPOINTS: dict[ModelEndpoint, EndpointConfig] = {
    ModelEndpoint.CLAUDE_EU: EndpointConfig(
        naam="Claude (EU)",
        base_url="https://api.anthropic.com",
        model_id="claude-sonnet-4-20250514",
        cloud_act_risico=True,  # Anthropic is US-gevestigd
        hosting_locatie="EU",
        soevereiniteit="beperkt",
    ),
    ModelEndpoint.AZURE_OAI_EU: EndpointConfig(
        naam="Azure OpenAI (EU)",
        base_url="https://nl-openai.openai.azure.com",
        model_id="gpt-4o",
        cloud_act_risico=True,  # Microsoft is US-gevestigd
        hosting_locatie="Netherlands West",
        soevereiniteit="beperkt",
    ),
    ModelEndpoint.SOVEREIGN_OLLAMA: EndpointConfig(
        naam="Ollama (on-prem)",
        base_url="https://llm.intern.gemeente.nl",
        model_id="llama3.1:70b",
        cloud_act_risico=False,
        hosting_locatie="on-prem datacenter",
        soevereiniteit="volledig",
    ),
    ModelEndpoint.SOVEREIGN_VLLM: EndpointConfig(
        naam="vLLM (air-gapped)",
        base_url="https://llm.diginetwerk.gemeente.nl",
        model_id="mistral-large-2",
        cloud_act_risico=False,
        hosting_locatie="Diginetwerk / air-gapped",
        soevereiniteit="volledig",
    ),
}
```

## On-premise LLM Opties

### Vergelijking soevereine LLM-platformen

| Platform | Model | Licentie | Hardware | Geschikt voor |
|----------|-------|----------|----------|--------------|
| **Ollama** | Llama 3.x, Mistral, Gemma | Apache 2.0 (Ollama), model-specifiek | 1x GPU (RTX 4090+) | PoC, kleine workloads |
| **vLLM** | Alle HuggingFace modellen | Apache 2.0 | Multi-GPU cluster | Productie, hoge doorvoer |
| **llama.cpp** | GGUF-modellen | MIT | CPU of GPU | Lichte workloads, edge |
| **TGI** (Text Gen Inference) | HuggingFace modellen | Apache 2.0 | GPU cluster | Productie (HF ecosystem) |
| **LocalAI** | Diverse formaten | MIT | CPU of GPU | Multi-model gateway |

### Ollama deployment (soeverein)

```yaml
# docker-compose.yml — Ollama op gemeentelijk datacenter
services:
  ollama:
    image: ollama/ollama:latest
    container_name: ollama-sovereign
    ports:
      - "11434:11434"
    volumes:
      - ollama_data:/root/.ollama
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all
              capabilities: [gpu]
    environment:
      - OLLAMA_HOST=0.0.0.0
      # Geen telemetrie naar buiten
      - OLLAMA_NOPRUNE=1
    networks:
      - internal
    restart: unless-stopped

  # Reverse proxy met mTLS
  nginx:
    image: nginx:alpine
    ports:
      - "443:443"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf:ro
      - ./certs/server.crt:/etc/ssl/server.crt:ro
      - ./certs/server.key:/etc/ssl/server.key:ro
      - ./certs/ca.crt:/etc/ssl/ca.crt:ro   # PKIoverheid CA
    networks:
      - internal
    depends_on:
      - ollama

networks:
  internal:
    driver: bridge
    internal: true  # Geen directe internettoegang

volumes:
  ollama_data:
```

### vLLM deployment (productie, soeverein)

```yaml
# kubernetes/vllm-deployment.yaml — vLLM op Haven/K8s
apiVersion: apps/v1
kind: Deployment
metadata:
  name: vllm-sovereign
  namespace: ai-platform
  labels:
    app: vllm
    security.bio2/bbn: "BBN2"
    data.classificatie: "VERTROUWELIJK"
spec:
  replicas: 2
  selector:
    matchLabels:
      app: vllm
  template:
    metadata:
      labels:
        app: vllm
    spec:
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        fsGroup: 1000
      containers:
        - name: vllm
          image: vllm/vllm-openai:latest
          args:
            - "--model"
            - "/models/mistral-large-2"
            - "--tensor-parallel-size"
            - "2"
            - "--max-model-len"
            - "32768"
            - "--port"
            - "8000"
          ports:
            - containerPort: 8000
          resources:
            limits:
              nvidia.com/gpu: 2
              memory: "64Gi"
            requests:
              nvidia.com/gpu: 2
              memory: "48Gi"
          volumeMounts:
            - name: model-storage
              mountPath: /models
              readOnly: true
          securityContext:
            readOnlyRootFilesystem: true
            allowPrivilegeEscalation: false
      volumes:
        - name: model-storage
          persistentVolumeClaim:
            claimName: sovereign-model-pvc
---
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: vllm-network-policy
  namespace: ai-platform
spec:
  podSelector:
    matchLabels:
      app: vllm
  policyTypes:
    - Ingress
    - Egress
  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              name: application-ns
      ports:
        - port: 8000
  egress: []  # Geen uitgaand verkeer — volledig geisoleerd
```

## mTLS voor Soevereine Endpoints

```python
"""mTLS client — beveiligde communicatie met soevereine LLM-endpoints."""

import ssl
from pathlib import Path

import httpx


def maak_mtls_client(
    client_cert: Path,
    client_key: Path,
    ca_bundle: Path,   # PKIoverheid CA-keten
    base_url: str,
) -> httpx.Client:
    """
    Maak een httpx client met mutual TLS (mTLS).

    Gebruik PKIoverheid-certificaten voor authenticatie
    op het Diginetwerk of interne netwerken.
    """
    ssl_context = ssl.create_default_context(
        purpose=ssl.Purpose.SERVER_AUTH,
        cafile=str(ca_bundle),
    )
    ssl_context.load_cert_chain(
        certfile=str(client_cert),
        keyfile=str(client_key),
    )
    # Minimaal TLS 1.2 (NCSC TLS-richtlijn)
    ssl_context.minimum_version = ssl.TLSVersion.TLSv1_2

    return httpx.Client(
        base_url=base_url,
        verify=ssl_context,
        headers={"Content-Type": "application/json"},
        timeout=httpx.Timeout(connect=5.0, read=120.0),
    )


# Gebruik:
# client = maak_mtls_client(
#     client_cert=Path("/etc/pki/gemeente/client.crt"),
#     client_key=Path("/etc/pki/gemeente/client.key"),
#     ca_bundle=Path("/etc/pki/pkioverheid/ca-bundle.crt"),
#     base_url="https://llm.diginetwerk.gemeente.nl",
# )
# response = client.post("/v1/chat/completions", json={...})
```

## Verwerkersovereenkomst — AI-specifieke clausules

Bij gebruik van externe LLM-providers (niet-soeverein) zijn deze clausules essentieel:

### Verplichte clausules

| Clausule | Doel | Juridische basis |
|----------|------|-----------------|
| **Geen training op input** | Provider mag input niet gebruiken voor modeltraining | AVG Art. 28 |
| **Data residency EU** | Verwerking uitsluitend in EU-datacenters | AVG Art. 44-49 |
| **Subverwerkers EU** | Alle subverwerkers in EU gevestigd | AVG Art. 28(2) |
| **Geen CLOUD Act medewerking** | Provider stelt klant op de hoogte bij US-verzoeken | Contractueel |
| **Recht op audit** | Klant mag (laten) auditen | AVG Art. 28(3)(h) |
| **Logging en transparantie** | Provider levert audit logs per verzoek | EU AI Act Art. 12 |
| **Incident response** | Melding binnen 72 uur bij datalek | AVG Art. 33 |
| **Data-verwijdering** | Verwijdering van alle data bij beeidiging | AVG Art. 28(3)(g) |
| **Bewaarbeleid** | Prompts/responses niet langer bewaard dan nodig | AVG Art. 5(1)(e) |

### Template clausule (voorbeeld)

```text
Artikel X — Specifieke voorwaarden AI-verwerking

X.1 Verwerker verwerkt persoonsgegevens uitsluitend in datacenters
    gelegen binnen de Europese Economische Ruimte (EER).

X.2 Verwerker gebruikt de door verwerkingsverantwoordelijke aangeboden
    data (prompts, context, bijlagen) niet voor het trainen,
    fine-tunen of evalueren van AI-modellen.

X.3 Verwerker informeert verwerkingsverantwoordelijke onverwijld,
    en in ieder geval binnen 48 uur, indien een overheidsinstantie
    van een derde land (waaronder de Verenigde Staten) verzoekt
    om toegang tot data van verwerkingsverantwoordelijke.

X.4 Verwerker stelt audit logs beschikbaar per API-verzoek,
    inclusief tijdstip, model-versie, input-tokens, output-tokens
    en verwerkte dataclassificatie.
```

## Soevereiniteit per provider

| Provider | Land | CLOUD Act | EU data residency | Soevereiniteit | Geschikt voor |
|----------|------|-----------|-------------------|---------------|--------------|
| **Anthropic** (Claude) | US | Ja | Beschikbaar (EU) | Beperkt | OPENBAAR, INTERN |
| **OpenAI / Azure** | US | Ja | NL/SE regions | Beperkt | OPENBAAR, INTERN |
| **Mistral** | FR | Nee | Ja (EU-native) | Hoog | Tot VERTROUWELIJK |
| **Aleph Alpha** | DE | Nee | Ja (EU-native) | Hoog | Tot VERTROUWELIJK |
| **Ollama** (self-hosted) | N.v.t. | Nee | N.v.t. (on-prem) | Volledig | Alle niveaus |
| **vLLM** (self-hosted) | N.v.t. | Nee | N.v.t. (on-prem) | Volledig | Alle niveaus |

## Implementatie-checklist

- [ ] **Classificatie**: alle AI-datastromen geclassificeerd (BIV)
- [ ] **Routing**: model-routing op basis van classificatie geimplementeerd
- [ ] **CLOUD Act**: risicobeoordeling per provider uitgevoerd
- [ ] **DPA**: verwerkersovereenkomst met AI-specifieke clausules
- [ ] **Data residency**: EU-only verwerking contractueel en technisch afgedwongen
- [ ] **Soeverein model**: on-prem LLM operationeel voor VERTROUWELIJK+
- [ ] **mTLS**: mutual TLS voor interne LLM-endpoints
- [ ] **Network isolation**: LLM-pods geen uitgaand internetverkeer
- [ ] **Monitoring**: logging van routing-besluiten en classificaties
- [ ] **DPIA**: uitgevoerd voor elke externe LLM-verwerking
- [ ] **Exit-strategie**: gedocumenteerd plan voor migratie naar ander model/provider

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **cloud-overheid** | Rijkscloudbeleid, BIO cloud controls, SaaS-beoordeling, Haven |
| **genai-governance** | EU AI Act governance: model registry, audit trail, HITL |
| **llm-security** | OWASP LLM Top 10: prompt injection, DLP, output sanitization |
| **avg-privacy** | AVG/GDPR compliance, verwerkingsovereenkomst, DPIA-verplichting |
| **dpia-assessment** | Data Protection Impact Assessment voor AI-verwerkingen |
| **nora-architectuur** | BIO2, verplichte standaarden, GDI |
| **overheid-authenticatie** | PKIoverheid certificaten voor mTLS |
| **digikoppeling** | Digikoppeling voor MSH-communicatie op Diginetwerk |

## Meer informatie

- [Rijkscloudbeleid](https://www.rijksoverheid.nl/onderwerpen/digitale-overheid) — beleidskader
- [US CLOUD Act](https://www.congress.gov/bill/115th-congress/house-bill/4943) — volledige tekst
- [EU-US Data Privacy Framework](https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/eu-us-data-transfers_en) — adequaatheidsbesluit
- [NCSC Cloudrichtlijnen](https://www.ncsc.nl/) — NCSC beveiligingsadvies
- [Ollama](https://ollama.com/) — self-hosted LLM platform
- [vLLM](https://docs.vllm.ai/) — high-throughput LLM serving
