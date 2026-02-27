---
name: logboek-dataverwerkingen
description: >-
  Helpt bij het implementeren van het Logboek Dataverwerkingen conform de
  Logius-standaard voor het transparant loggen van gegevensverwerkingen
  door overheidsorganisaties. Biedt richtlijnen voor de API-specificatie,
  logregels, vertrouwelijkheidsniveaus en integratie met bestaande systemen.
  Gebruik deze skill wanneer de gebruiker vraagt over
  'Logboek Dataverwerkingen', 'logboek dataverwerkingen',
  'verwerkingenlogging', 'verwerkingslog', 'logging dataverwerkingen',
  'data processing log', 'verwerkingenregister logging',
  'AVG logging', 'GDPR logging', 'transparantie logging',
  'gegevensverwerking loggen', 'data processing transparency',
  'logboek API', 'verwerkingsactiviteit loggen',
  'inzageverzoek logging', 'betrokkene inzage verwerking',
  'wie heeft mijn gegevens bekeken', 'wie heeft mijn data gebruikt',
  'logboek register', 'verwerkingslogboek',
  'Logius logboek', 'logging standaard overheid',
  of wanneer de gebruiker gegevensverwerkingen transparant wil
  loggen conform de AVG en de Logius-standaard.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(curl *)
  - Bash(gh api *)
  - Bash(gh search *)
---

# Logboek Dataverwerkingen — Transparant Loggen van Gegevensverwerkingen

Implementeer transparante logging van gegevensverwerkingen conform de Logius-standaard.

Bron: [Logboek Dataverwerkingen (Logius)](https://logius-standaarden.github.io/logboek-dataverwerkingen/) | [GitHub](https://github.com/Logius-standaarden/logboek-dataverwerkingen)

## Wat is het Logboek Dataverwerkingen?

| Aspect | Detail |
|--------|--------|
| **Doel** | Transparant vastleggen welke gegevensverwerkingen hebben plaatsgevonden |
| **Waarom** | AVG-transparantieplicht (Art. 5, 12-14); burgers recht op inzage |
| **Beheerder** | Logius |
| **Status** | In ontwikkeling; wordt verplichte standaard |
| **Scope** | Elke verwerking van persoonsgegevens door overheidsorganisaties |
| **Relatie** | Aanvulling op het verwerkingsregister (Art. 30 AVG) |
| **Verschil** | Verwerkingsregister = welke verwerkingen bestaan; Logboek = welke verwerkingen daadwerkelijk hebben plaatsgevonden |

### Verwerkingsregister vs. Logboek

| Aspect | Verwerkingsregister (Art. 30) | Logboek Dataverwerkingen |
|--------|------------------------------|--------------------------|
| **Wat** | Beschrijving van verwerkingsactiviteiten | Feitelijke logregels per verwerking |
| **Wanneer** | Vooraf (design-time) | Runtime (elke verwerking wordt gelogd) |
| **Granulariteit** | Verwerkingsactiviteit-niveau | Individuele verwerking-niveau |
| **Voorbeeld** | "Wij verwerken BSN voor belastingaangifte" | "Op 27-02-2026 om 14:30 is BSN X verwerkt voor belastingaangifte Y" |
| **Doel** | Verantwoording aan AP | Transparantie naar betrokkene |

## Architectuur

```
                    Logboek API
                        |
    +-------------------+-------------------+
    |                   |                   |
Applicatie A      Applicatie B       Applicatie C
(zaaksysteem)     (portaal)          (analytics)
    |                   |                   |
    +-- logregel -------+-- logregel -------+-- logregel
    |                   |                   |
    v                   v                   v
+---------------------------------------------------+
|           Logboek Dataverwerkingen                 |
|           (centraal of per applicatie)             |
+---------------------------------------------------+
    |
    v
+-------------------+
| Inzage-portaal    |  <-- Burger vraagt: "wie heeft
| (betrokkene)      |      mijn gegevens verwerkt?"
+-------------------+
```

## API-specificatie

### Logregel aanmaken

```http
POST /api/v1/logregels HTTP/1.1
Content-Type: application/json
Authorization: Bearer <token>

{
  "verwerkingsactiviteitId": "5f0bef4c-f66f-4311-84a5-19e8bf359eaf",
  "verwerkingsactiviteitUrl": "https://verwerkingsregister.org.nl/api/v1/verwerkingsactiviteiten/5f0bef4c",
  "vertrouwelijkheid": "normaal",
  "bewaartermijn": "P5Y",
  "uitvoerder": {
    "organisatieId": "00000001234567890000",
    "applicatieId": "zaaksysteem-v2",
    "gebruikerId": "medewerker-12345"
  },
  "tijdstip": "2026-02-27T14:30:00Z",
  "verwerkteObjecten": [
    {
      "objecttype": "persoon",
      "soortObjectId": "BSN",
      "objectId": "999990019",
      "betrokkenheid": "betrokkene"
    }
  ],
  "verwerking": {
    "doel": "Behandeling zaak ZK-2026-001234",
    "grondslag": "Uitvoering wettelijke taak (Art. 6.1.e AVG)",
    "categorie": "opvragen"
  }
}
```

### Response

```json
{
  "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "verwerkingsactiviteitId": "5f0bef4c-f66f-4311-84a5-19e8bf359eaf",
  "tijdstip": "2026-02-27T14:30:00Z",
  "status": "vastgelegd"
}
```

### Logregels opvragen (inzageverzoek betrokkene)

```http
GET /api/v1/logregels?objecttype=persoon&soortObjectId=BSN&objectId=999990019&van=2026-01-01&tot=2026-02-28
Authorization: Bearer <token>
```

## Logregel-model

| Veld | Type | Verplicht | Beschrijving |
|------|------|-----------|-------------|
| **verwerkingsactiviteitId** | UUID | Ja | Verwijzing naar verwerkingsregister |
| **vertrouwelijkheid** | Enum | Ja | `normaal`, `vertrouwelijk`, `opgeheven` |
| **bewaartermijn** | ISO 8601 duration | Ja | Hoe lang de logregel bewaard wordt |
| **tijdstip** | ISO 8601 datetime | Ja | Wanneer de verwerking plaatsvond |
| **uitvoerder.organisatieId** | String (OIN) | Ja | OIN van de verwerkende organisatie |
| **uitvoerder.applicatieId** | String | Ja | Identificatie van het systeem |
| **uitvoerder.gebruikerId** | String | Nee | Medewerker (NIET loggen als niet nodig) |
| **verwerkteObjecten** | Array | Ja | Welke objecten zijn verwerkt |
| **verwerkteObjecten[].objecttype** | String | Ja | Type object (persoon, zaak, etc.) |
| **verwerkteObjecten[].soortObjectId** | String | Ja | Type identificatie (BSN, zaaknummer) |
| **verwerkteObjecten[].objectId** | String | Ja | De identificatie zelf |
| **verwerking.doel** | String | Ja | Concreet doel van deze verwerking |
| **verwerking.grondslag** | String | Ja | AVG-grondslag |
| **verwerking.categorie** | Enum | Ja | Zie categorietabel hieronder |

### Verwerkingscategorieen

| Categorie | Beschrijving | Voorbeeld |
|-----------|-------------|-----------|
| **verzamelen** | Gegevens ophalen uit bron | BRP-bevraging, Suwinet-inkijk |
| **opvragen** | Gegevens raadplegen | Dossier inzien, zaak bekijken |
| **gebruiken** | Gegevens gebruiken in proces | Besluit nemen, berekening uitvoeren |
| **verstrekken** | Gegevens delen met derde | Gegevens leveren aan ketenpartner |
| **wijzigen** | Gegevens aanpassen | Adreswijziging, statusupdate |
| **verwijderen** | Gegevens verwijderen | Verwijdering na bewaartermijn |

### Vertrouwelijkheidsniveaus

| Niveau | Wanneer | Inzage door betrokkene |
|--------|---------|----------------------|
| **normaal** | Standaard | Ja, altijd |
| **vertrouwelijk** | Lopend onderzoek, handhaving, fraude | Nee, tijdelijk afgeschermd |
| **opgeheven** | Vertrouwelijkheid is opgeheven | Ja, weer inzichtelijk |

## Implementatiepatronen

### Middleware-patroon (aanbevolen)

```python
from dataclasses import dataclass, field
from datetime import datetime, timezone
from enum import Enum
from uuid import uuid4
import httpx


class VerwerkingsCategorie(Enum):
    VERZAMELEN = "verzamelen"
    OPVRAGEN = "opvragen"
    GEBRUIKEN = "gebruiken"
    VERSTREKKEN = "verstrekken"
    WIJZIGEN = "wijzigen"
    VERWIJDEREN = "verwijderen"


class Vertrouwelijkheid(Enum):
    NORMAAL = "normaal"
    VERTROUWELIJK = "vertrouwelijk"
    OPGEHEVEN = "opgeheven"


@dataclass
class VerwerkteObject:
    objecttype: str
    soort_object_id: str
    object_id: str
    betrokkenheid: str = "betrokkene"


@dataclass
class Logregel:
    verwerkingsactiviteit_id: str
    uitvoerder_organisatie_id: str
    uitvoerder_applicatie_id: str
    verwerkte_objecten: list[VerwerkteObject]
    doel: str
    grondslag: str
    categorie: VerwerkingsCategorie
    vertrouwelijkheid: Vertrouwelijkheid = Vertrouwelijkheid.NORMAAL
    bewaartermijn: str = "P5Y"
    tijdstip: datetime = field(default_factory=lambda: datetime.now(timezone.utc))
    uitvoerder_gebruiker_id: str | None = None

    def to_api_payload(self) -> dict:
        payload = {
            "verwerkingsactiviteitId": self.verwerkingsactiviteit_id,
            "vertrouwelijkheid": self.vertrouwelijkheid.value,
            "bewaartermijn": self.bewaartermijn,
            "tijdstip": self.tijdstip.isoformat(),
            "uitvoerder": {
                "organisatieId": self.uitvoerder_organisatie_id,
                "applicatieId": self.uitvoerder_applicatie_id,
            },
            "verwerkteObjecten": [
                {
                    "objecttype": obj.objecttype,
                    "soortObjectId": obj.soort_object_id,
                    "objectId": obj.object_id,
                    "betrokkenheid": obj.betrokkenheid,
                }
                for obj in self.verwerkte_objecten
            ],
            "verwerking": {
                "doel": self.doel,
                "grondslag": self.grondslag,
                "categorie": self.categorie.value,
            },
        }
        if self.uitvoerder_gebruiker_id:
            payload["uitvoerder"]["gebruikerId"] = self.uitvoerder_gebruiker_id
        return payload


class LogboekClient:
    """Client voor het Logboek Dataverwerkingen API."""

    def __init__(self, base_url: str, api_token: str):
        self.client = httpx.AsyncClient(
            base_url=base_url,
            headers={"Authorization": f"Bearer {api_token}"},
        )

    async def log_verwerking(self, logregel: Logregel) -> str:
        """Log een gegevensverwerking."""
        response = await self.client.post(
            "/api/v1/logregels",
            json=logregel.to_api_payload(),
        )
        response.raise_for_status()
        return response.json()["id"]

    async def opvragen_logregels(
        self, bsn: str, van: datetime, tot: datetime
    ) -> list[dict]:
        """Haal logregels op voor een betrokkene (inzageverzoek)."""
        response = await self.client.get(
            "/api/v1/logregels",
            params={
                "objecttype": "persoon",
                "soortObjectId": "BSN",
                "objectId": bsn,
                "van": van.isoformat(),
                "tot": tot.isoformat(),
            },
        )
        response.raise_for_status()
        return response.json()["logregels"]
```

### Django middleware voorbeeld

```python
# middleware.py
from logboek_client import LogboekClient, Logregel, VerwerkteObject, VerwerkingsCategorie

logboek = LogboekClient(
    base_url="https://logboek.organisatie.nl",
    api_token="...",
)

class LogboekMiddleware:
    """Django middleware die gegevensverwerkingen automatisch logt."""

    VERWERKINGSACTIVITEIT_MAP = {
        "/api/zaken/": "zaakbehandeling-uuid",
        "/api/personen/": "persoonsbevraging-uuid",
    }

    async def __call__(self, request, call_next):
        response = await call_next(request)

        # Alleen loggen bij succesvolle verwerking van persoonsgegevens
        if response.status_code < 400 and self._bevat_persoonsgegevens(request):
            await self._log_verwerking(request)

        return response

    async def _log_verwerking(self, request):
        activiteit_id = self._bepaal_verwerkingsactiviteit(request.path)
        if not activiteit_id:
            return

        logregel = Logregel(
            verwerkingsactiviteit_id=activiteit_id,
            uitvoerder_organisatie_id="00000001234567890000",
            uitvoerder_applicatie_id="zaaksysteem-v2",
            uitvoerder_gebruiker_id=getattr(request.user, "username", None),
            verwerkte_objecten=self._extract_objecten(request),
            doel=f"Behandeling via {request.method} {request.path}",
            grondslag="Uitvoering wettelijke taak (Art. 6.1.e AVG)",
            categorie=self._bepaal_categorie(request.method),
        )
        await logboek.log_verwerking(logregel)

    def _bepaal_categorie(self, method: str) -> VerwerkingsCategorie:
        return {
            "GET": VerwerkingsCategorie.OPVRAGEN,
            "POST": VerwerkingsCategorie.VERZAMELEN,
            "PUT": VerwerkingsCategorie.WIJZIGEN,
            "PATCH": VerwerkingsCategorie.WIJZIGEN,
            "DELETE": VerwerkingsCategorie.VERWIJDEREN,
        }.get(method, VerwerkingsCategorie.GEBRUIKEN)
```

## Privacy-eisen voor het logboek zelf

| Eis | Toelichting |
|-----|-------------|
| **Doelbinding** | Logboek alleen gebruiken voor transparantie, niet voor personeelsmonitoring |
| **Dataminimalisatie** | Alleen loggen wat nodig is; geen inhoudelijke gegevens in de logregel |
| **Bewaartermijn** | Logregels verwijderen na de bewaartermijn |
| **Toegang** | Alleen geautoriseerd personeel; betrokkene via inzageverzoek |
| **Integriteit** | Logregels mogen niet achteraf gewijzigd worden (append-only) |
| **BSN in logboek** | BSN mag als objectId maar moet versleuteld worden opgeslagen |
| **DPIA** | DPIA uitvoeren voor het logboek zelf |

## Implementatie-checklist

- [ ] **Verwerkingsregister**: verwerkingsactiviteiten gedefinieerd met UUID's
- [ ] **API geimplementeerd**: Logboek Dataverwerkingen API conform specificatie
- [ ] **Logregels bij elke verwerking**: middleware of interceptor logt automatisch
- [ ] **Vertrouwelijkheidsniveaus**: normaal/vertrouwelijk/opgeheven correct toegepast
- [ ] **Bewaartermijnen**: automatische verwijdering na bewaartermijn
- [ ] **Inzage-endpoint**: betrokkenen kunnen eigen logregels opvragen
- [ ] **BSN-versleuteling**: BSN in objectId versleuteld opgeslagen
- [ ] **Append-only**: logregels onwijzigbaar na vastlegging
- [ ] **Geen inhoudelijke data**: logregels bevatten geen persoonsgegevens behalve objectId
- [ ] **DPIA**: DPIA uitgevoerd voor het logboek zelf
- [ ] **Koppeling verwerkingsregister**: elke logregel verwijst naar verwerkingsactiviteit

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **avg-privacy** | AVG-grondslagen, verwerkingsregister, rechten betrokkenen |
| **dpia-assessment** | DPIA uitvoeren voor het logboek zelf |
| **zgw-apis** | ZGW API-integratie voor zaakgericht loggen |
| **nora-architectuur** | BIO-logging-eisen (BIO 12.4) |

## Meer informatie

- [Logboek Dataverwerkingen (Logius)](https://logius-standaarden.github.io/logboek-dataverwerkingen/)
- [GitHub — Logboek Dataverwerkingen](https://github.com/Logius-standaarden/logboek-dataverwerkingen)
- [VNG — Verwerkingenlogging](https://vng-realisatie.github.io/gemma-verwerkingenlogging/)
- [AVG Art. 5, 12-14](https://eur-lex.europa.eu/eli/reg/2016/679/oj) — transparantieverplichtingen
- [Verwerkingsregister (Art. 30 AVG)](https://www.autoriteitpersoonsgegevens.nl/themas/basis-avg/praktisch-avg/verwerkingsregister)
