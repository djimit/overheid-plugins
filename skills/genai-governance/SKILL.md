---
name: genai-governance
description: >-
  Helpt bij het implementeren van technische governance-controls voor
  generatieve AI-systemen bij de Nederlandse overheid, conform de
  EU AI Act (hoog-risico), AVG en BIO2.
  Biedt model cards (Annex IV), conformiteitsbeoordeling (Art. 43),
  audit trails (Art. 12), menselijk toezicht (Art. 14),
  besluitregistratie, model registry en HITL-protocollen.
  Gebruik deze skill wanneer de gebruiker vraagt over
  'AI governance', 'GenAI governance', 'AI Act implementatie',
  'AI Act implementation', 'model card', 'model registry',
  'AI audit trail', 'AI audit log', 'AI besluitregistratie',
  'AI decision recording', 'menselijk toezicht AI',
  'human oversight AI', 'HITL', 'human-in-the-loop',
  'conformiteitsbeoordeling', 'conformity assessment',
  'AI Act Annex IV', 'AI Act artikel 9', 'AI Act artikel 14',
  'AI risicomanagement', 'AI risk management',
  'AI transparantie', 'AI transparency',
  'AI explainability', 'AI uitlegbaarheid',
  'prompt registry', 'prompt versioning',
  'AI verantwoording', 'AI accountability',
  'hoog-risico AI', 'high-risk AI',
  of wanneer de gebruiker technische governance-controls wil
  bouwen voor een AI/GenAI-systeem bij de overheid.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# GenAI Governance — EU AI Act technische implementatie

Technische governance-controls voor generatieve AI-systemen bij de Nederlandse overheid, conform EU AI Act (hoog-risico), AVG en BIO2.

Bron: [EU AI Act](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | [Algoritmekader](https://minbzk.github.io/Algoritmekader/) | [BIO2](https://bio-overheid.nl/)

## Overzicht governance-lagen

```
┌──────────────────────────────────────────────────────┐
│                  GenAI Applicatie                      │
├──────────────────────────────────────────────────────┤
│  Governance Layer                                     │
│  ┌────────────┐ ┌────────────┐ ┌──────────────────┐ │
│  │ Audit      │ │ Model      │ │ Conformiteits-   │ │
│  │ Logger     │ │ Registry   │ │ beoordeling      │ │
│  └────────────┘ └────────────┘ └──────────────────┘ │
│  ┌────────────┐ ┌────────────┐ ┌──────────────────┐ │
│  │ Besluit-   │ │ Prompt     │ │ Menselijk        │ │
│  │ registratie│ │ Registry   │ │ Toezicht (HITL)  │ │
│  └────────────┘ └────────────┘ └──────────────────┘ │
│  ┌────────────┐ ┌────────────┐                       │
│  │ Explain-   │ │ Drift      │                       │
│  │ ability    │ │ Detector   │                       │
│  └────────────┘ └────────────┘                       │
├──────────────────────────────────────────────────────┤
│  Security Layer  (→ zie skill llm-security)           │
├──────────────────────────────────────────────────────┤
│  LLM Client Layer                                     │
└──────────────────────────────────────────────────────┘
```

## EU AI Act — Hoog-risico verplichtingen

### Relevante artikelen voor GenAI-systemen

| Artikel | Onderwerp | Technische control |
|---------|-----------|-------------------|
| **Art. 9** | Risicomanagementsysteem | `risk_assessment.md` + continu monitoren |
| **Art. 10** | Data en datagovernance | `data_governance.md` + data lineage |
| **Art. 11** | Technische documentatie | `governance_docs/` (Annex IV) |
| **Art. 12** | Registratie van gebeurtenissen | `audit_logger.py` (WORM-compatible) |
| **Art. 13** | Transparantie | `model_card.md` + explainability |
| **Art. 14** | Menselijk toezicht | `human_oversight.py` + HITL protocol |
| **Art. 15** | Nauwkeurigheid en robuustheid | `tests/behavioural/` + drift detection |
| **Art. 43** | Conformiteitsbeoordeling | `conformity_assessment.md` |
| **Annex IV** | Technische documentatie-eisen | Volledige documentatieset |

### Annex IV — Verplichte documentatie (hoog-risico)

```
governance_docs/
├── risk_assessment.md           # FMEA / risicoregister per use case
├── data_governance.md           # Data lineage, kwaliteit, bewaarbeleid
├── model_card.md                # Modeltransparantiekaart (verplicht)
├── conformity_assessment.md     # Zelfbeoordelingschecklist (Art. 43)
├── human_oversight_protocol.md  # HITL-procedures en escalatiematrix
└── incident_response.md         # AI-specifiek incident response playbook
```

## Model Card (Annex IV §1)

### Template

```yaml
# model_card.yaml — EU AI Act Annex IV compliant
metadata:
  versie: "1.0"
  datum: "2026-02-27"
  auteur: "AI-team gemeente X"
  classificatie: "hoog-risico"

model:
  naam: "Claude Sonnet 4 (Anthropic)"
  versie: "claude-sonnet-4-20250514"
  type: "Large Language Model (generatief)"
  provider: "Anthropic"
  hosting: "EU-region (Anthropic EU)"
  parameters: "niet openbaar (closed-source)"

doel:
  beschrijving: >
    Samenvatten van juridische documenten ter ondersteuning
    van besluitvorming in bezwaarprocedures.
  beoogd_gebruik:
    - "Samenvatting van bezwaarschriften"
    - "Conceptvoorbereiding hoorbeschikking"
  niet_beoogd_gebruik:
    - "Autonome besluitvorming zonder menselijke review"
    - "Profilering van burgers"

risicoclassificatie:
  eu_ai_act: "hoog-risico (Annex III, punt 6: rechtsbedeling)"
  bio2_bbn: "BBN2"
  data_classificatie: "VERTROUWELIJK"

prestaties:
  evaluatie_methode: "Handmatige beoordeling door juridisch medewerker"
  nauwkeurigheid: "92% correcte samenvattingen (n=200, acc-omgeving)"
  beperkingen:
    - "Kan hallucineren bij obscure jurisprudentie"
    - "Niet geschikt voor bestuursrechtelijke interpretatie"
    - "Beperkte kennis van recente wetswijzigingen"

eerlijkheid:
  bias_analyse: "Getest op geslacht, leeftijd, etnische achtergrond"
  mitigatie: "Geanonimiseerde input, output review door medewerker"

data:
  training_data: "Niet beschikbaar (closed-source model)"
  input_data: "Bezwaarschriften (AVG bijzondere categorieen mogelijk)"
  data_governance: "Zie data_governance.md"

menselijk_toezicht:
  type: "human-in-the-loop"
  beschrijving: >
    Elke AI-output wordt beoordeeld door een juridisch medewerker
    voordat deze in het besluitproces wordt opgenomen.
  escalatie: "Zie human_oversight_protocol.md"

logging:
  audit_trail: "Ja — WORM-compatible, 10 jaar bewaard"
  besluitregistratie: "Per inferentie, gekoppeld aan zaaknummer"
```

## Audit Logger (Art. 12)

### Onveranderbaar audit trail

```python
"""Immutable audit logger voor AI-inferenties — EU AI Act Art. 12."""

import hashlib
import json
import logging
from datetime import datetime, timezone
from dataclasses import dataclass, field, asdict
from enum import Enum
from pathlib import Path
from typing import Any

logger = logging.getLogger(__name__)


class RisicoNiveau(str, Enum):
    LAAG = "laag"
    BEPERKT = "beperkt"
    HOOG = "hoog"
    ONAANVAARDBAAR = "onaanvaardbaar"


class BesluitType(str, Enum):
    GEAUTOMATISEERD = "geautomatiseerd"
    ONDERSTEUNEND = "ondersteunend"  # AI adviseert, mens beslist
    HITL = "human-in-the-loop"


@dataclass
class AuditRecord:
    """Enkelvoudig audit record voor een AI-inferentie."""

    # Identificatie
    record_id: str
    tijdstip: str = field(
        default_factory=lambda: datetime.now(timezone.utc).isoformat()
    )

    # Context
    zaak_id: str | None = None
    gebruiker_id: str | None = None  # Pseudoniem, geen BSN
    applicatie: str = ""
    omgeving: str = ""  # dev/tst/acc/prd

    # Model
    model_naam: str = ""
    model_versie: str = ""
    provider: str = ""

    # Inferentie
    prompt_template_id: str = ""
    prompt_template_versie: str = ""
    input_tokens: int = 0
    output_tokens: int = 0
    latency_ms: int = 0

    # Governance
    risico_niveau: RisicoNiveau = RisicoNiveau.HOOG
    besluit_type: BesluitType = BesluitType.ONDERSTEUNEND
    menselijk_toezicht: bool = True
    beoordelaar_id: str | None = None

    # Resultaat
    output_hash: str = ""  # SHA-256 van de output (niet de output zelf)
    vertrouwen_score: float | None = None
    hitl_status: str = ""  # "goedgekeurd" / "afgekeurd" / "aangepast"

    # Integriteit
    vorige_record_hash: str = ""  # Keten-hash voor tamper-detectie

    def bereken_hash(self) -> str:
        """Bereken SHA-256 hash van dit record (chain hash)."""
        data = json.dumps(asdict(self), sort_keys=True, default=str)
        return hashlib.sha256(data.encode()).hexdigest()


class AuditLogger:
    """WORM-compatible audit logger met chain hashing."""

    def __init__(self, output_dir: Path, omgeving: str = "prd"):
        self.output_dir = output_dir
        self.omgeving = omgeving
        self.output_dir.mkdir(parents=True, exist_ok=True)
        self._laatste_hash = ""

    def log(self, record: AuditRecord) -> str:
        """
        Schrijf een onveranderbaar audit record.

        Returns:
            Hash van het geschreven record.
        """
        record.omgeving = self.omgeving
        record.vorige_record_hash = self._laatste_hash
        record_hash = record.bereken_hash()

        # Schrijf naar append-only bestand (WORM in productie)
        bestand = self.output_dir / f"audit_{record.tijdstip[:10]}.jsonl"
        with open(bestand, "a") as f:
            entry = asdict(record)
            entry["_record_hash"] = record_hash
            f.write(json.dumps(entry, default=str) + "\n")

        self._laatste_hash = record_hash
        logger.info(
            "Audit record %s geschreven (hash: %s...)",
            record.record_id,
            record_hash[:12],
        )
        return record_hash

    def verifieer_keten(self, bestand: Path) -> bool:
        """Verifieer de integriteit van de audit keten."""
        vorige_hash = ""
        with open(bestand) as f:
            for regel_nr, regel in enumerate(f, 1):
                entry = json.loads(regel)
                opgeslagen_hash = entry.pop("_record_hash")
                record = AuditRecord(**{
                    k: v for k, v in entry.items()
                    if k in AuditRecord.__dataclass_fields__
                })
                record.vorige_record_hash = vorige_hash

                berekend = record.bereken_hash()
                if berekend != opgeslagen_hash:
                    logger.error(
                        "Keten-integriteit geschonden op regel %d", regel_nr
                    )
                    return False
                vorige_hash = opgeslagen_hash

        logger.info("Keten-integriteit geverifieerd: %d records", regel_nr)
        return True
```

### Gebruik

```python
from pathlib import Path
from uuid import uuid4

audit = AuditLogger(Path("data/audit"), omgeving="prd")

record = AuditRecord(
    record_id=str(uuid4()),
    zaak_id="ZAAK-2026-001234",
    gebruiker_id="usr-pseudoniem-abc",
    applicatie="bezwaar-samenvatting",
    model_naam="claude-sonnet-4",
    model_versie="20250514",
    provider="anthropic",
    prompt_template_id="samenvatting-bezwaar-v3",
    prompt_template_versie="3.1.0",
    input_tokens=2450,
    output_tokens=890,
    latency_ms=1200,
    risico_niveau=RisicoNiveau.HOOG,
    besluit_type=BesluitType.ONDERSTEUNEND,
    menselijk_toezicht=True,
    output_hash=hashlib.sha256(b"<de AI output>").hexdigest(),
    vertrouwen_score=0.87,
)

audit.log(record)
```

## Model Registry (Annex IV)

```python
"""Model Registry — registratie van alle AI-modellen in gebruik."""

from dataclasses import dataclass
from datetime import date
from enum import Enum


class ModelStatus(str, Enum):
    EXPERIMENTEEL = "experimenteel"  # Alleen dev/tst
    GEACCEPTEERD = "geaccepteerd"    # acc, na conformiteitsbeoordeling
    PRODUCTIE = "productie"          # prd, volledig goedgekeurd
    UITGEFASEERD = "uitgefaseerd"    # Niet meer gebruiken


@dataclass
class ModelRegistratie:
    """Registratie van een AI-model conform Annex IV."""

    # Identificatie
    model_id: str
    naam: str
    versie: str
    provider: str

    # Classificatie
    eu_ai_act_risico: str  # "hoog-risico", "beperkt-risico", "minimaal"
    bio2_bbn: str          # "BBN1", "BBN2", "BBN3"
    data_classificatie: str  # "OPENBAAR", "INTERN", "VERTROUWELIJK", "GEHEIM"

    # Hosting
    hosting_locatie: str   # "EU", "NL", "on-prem", "non-EU"
    cloud_act_risico: bool
    soevereiniteit: str    # "volledig", "beperkt", "geen"

    # Goedkeuring
    status: ModelStatus
    goedgekeurd_door: str
    goedkeuringsdatum: date | None
    conformiteitsbeoordeling: bool

    # Beperkingen
    toegestane_use_cases: list[str]
    verboden_use_cases: list[str]
    max_data_classificatie: str  # Hoogste classificatie die het model mag verwerken

    # Bewaarbeleid
    log_retentie_jaren: int = 10  # EU AI Act: minimaal levensduur + 10 jaar


# Voorbeeld registry
MODELLEN: dict[str, ModelRegistratie] = {
    "claude-sonnet-4": ModelRegistratie(
        model_id="claude-sonnet-4",
        naam="Claude Sonnet 4",
        versie="20250514",
        provider="Anthropic",
        eu_ai_act_risico="hoog-risico",
        bio2_bbn="BBN2",
        data_classificatie="VERTROUWELIJK",
        hosting_locatie="EU",
        cloud_act_risico=True,  # Anthropic is US-gevestigd
        soevereiniteit="beperkt",
        status=ModelStatus.GEACCEPTEERD,
        goedgekeurd_door="CISO + FG",
        goedkeuringsdatum=date(2026, 1, 15),
        conformiteitsbeoordeling=True,
        toegestane_use_cases=[
            "samenvatting-bezwaar",
            "conceptbrief-opstellen",
        ],
        verboden_use_cases=[
            "autonome-besluitvorming",
            "profilering-burgers",
            "verwerking-bijzondere-categorieen-zonder-hitl",
        ],
        max_data_classificatie="VERTROUWELIJK",
        log_retentie_jaren=10,
    ),
    "llama-3-sovereign": ModelRegistratie(
        model_id="llama-3-70b",
        naam="Llama 3 70B (on-prem)",
        versie="3.1-70b",
        provider="Meta (self-hosted via Ollama)",
        eu_ai_act_risico="hoog-risico",
        bio2_bbn="BBN2",
        data_classificatie="GEHEIM",
        hosting_locatie="on-prem",
        cloud_act_risico=False,
        soevereiniteit="volledig",
        status=ModelStatus.PRODUCTIE,
        goedgekeurd_door="CISO",
        goedkeuringsdatum=date(2026, 2, 1),
        conformiteitsbeoordeling=True,
        toegestane_use_cases=[
            "verwerking-bijzondere-categorieen",
            "gerechtelijke-documenten",
        ],
        verboden_use_cases=[
            "autonome-besluitvorming",
        ],
        max_data_classificatie="GEHEIM",
        log_retentie_jaren=10,
    ),
}
```

## Besluitregistratie (Art. 14)

```python
"""Decision Recorder — per-inferentie besluitregistratie."""

import json
from dataclasses import dataclass, asdict
from datetime import datetime, timezone
from enum import Enum
from pathlib import Path


class HITLBesluit(str, Enum):
    GOEDGEKEURD = "goedgekeurd"        # Output ongewijzigd overgenomen
    AANGEPAST = "aangepast"             # Output bewerkt door medewerker
    AFGEKEURD = "afgekeurd"             # Output niet gebruikt
    GEESCALEERD = "geescaleerd"         # Doorgestuurd naar senior/expert
    WACHT_OP_REVIEW = "wacht_op_review" # Nog niet beoordeeld


@dataclass
class BesluitRecord:
    """Registratie van een menselijk besluit over AI-output."""

    # Koppeling
    record_id: str
    audit_record_id: str  # Verwijzing naar AuditRecord
    zaak_id: str

    # Besluit
    besluit: HITLBesluit
    beoordelaar_id: str  # Pseudoniem
    beoordeeld_op: str = ""
    toelichting: str = ""

    # Aanpassing
    originele_output_hash: str = ""
    aangepaste_output_hash: str = ""  # Alleen bij AANGEPAST

    # Escalatie
    geescaleerd_naar: str = ""
    escalatie_reden: str = ""

    def __post_init__(self):
        if not self.beoordeeld_op:
            self.beoordeeld_op = datetime.now(timezone.utc).isoformat()


class BesluitRecorder:
    """Registreert menselijke besluiten over AI-output."""

    def __init__(self, output_dir: Path):
        self.output_dir = output_dir
        self.output_dir.mkdir(parents=True, exist_ok=True)

    def registreer(self, record: BesluitRecord) -> None:
        bestand = self.output_dir / f"besluiten_{record.beoordeeld_op[:10]}.jsonl"
        with open(bestand, "a") as f:
            f.write(json.dumps(asdict(record), default=str) + "\n")

    def wacht_op_review(self, zaak_id: str) -> list[BesluitRecord]:
        """Haal alle records op die wachten op review."""
        resultaten = []
        for bestand in self.output_dir.glob("besluiten_*.jsonl"):
            with open(bestand) as f:
                for regel in f:
                    data = json.loads(regel)
                    if (
                        data["zaak_id"] == zaak_id
                        and data["besluit"] == HITLBesluit.WACHT_OP_REVIEW
                    ):
                        resultaten.append(BesluitRecord(**data))
        return resultaten
```

## Menselijk Toezicht (HITL) Protocol

### Escalatiematrix

| Trigger | Actie | Escalatieniveau |
|---------|-------|----------------|
| Vertrouwenscore < 0.7 | Verplichte menselijke review | Medewerker |
| Bijzondere persoonsgegevens in input | Blokkeer niet-soeverein model | Systeem (automatisch) |
| Output bevat juridische conclusie | Verplichte juristenreview | Senior jurist |
| Output wijkt af van eerdere vergelijkbare output > 30% | Drift-alarm + review | Teamleider |
| Model niet in registry of status != PRODUCTIE | Blokkeer inferentie | Systeem (automatisch) |
| Eerste gebruik van nieuw prompt-template | Review door domeinexpert | Domeinexpert |

### Implementatie

```python
"""Human-in-the-Loop trigger engine."""

from dataclasses import dataclass
from enum import Enum


class EscalatieNiveau(str, Enum):
    AUTOMATISCH = "automatisch"     # Systeem blokkeert
    MEDEWERKER = "medewerker"       # Standaard review
    SENIOR = "senior"               # Senior/expert review
    TEAMLEIDER = "teamleider"       # Management review
    CISO = "ciso"                   # Security-escalatie


@dataclass
class HITLTrigger:
    naam: str
    conditie: str
    escalatie: EscalatieNiveau
    blokkeerend: bool  # True = output niet tonen tot review


TRIGGERS: list[HITLTrigger] = [
    HITLTrigger(
        naam="lage_vertrouwensscore",
        conditie="vertrouwen_score < 0.7",
        escalatie=EscalatieNiveau.MEDEWERKER,
        blokkeerend=True,
    ),
    HITLTrigger(
        naam="bijzondere_persoonsgegevens",
        conditie="data_classificatie in ('bijzondere_categorie', 'GEHEIM')",
        escalatie=EscalatieNiveau.AUTOMATISCH,
        blokkeerend=True,
    ),
    HITLTrigger(
        naam="juridische_conclusie",
        conditie="output_bevat_juridische_conclusie()",
        escalatie=EscalatieNiveau.SENIOR,
        blokkeerend=True,
    ),
    HITLTrigger(
        naam="output_drift",
        conditie="cosine_similarity(output, baseline) < 0.7",
        escalatie=EscalatieNiveau.TEAMLEIDER,
        blokkeerend=False,
    ),
    HITLTrigger(
        naam="model_niet_geregistreerd",
        conditie="model_id not in MODELLEN or status != PRODUCTIE",
        escalatie=EscalatieNiveau.AUTOMATISCH,
        blokkeerend=True,
    ),
]


def evalueer_triggers(
    vertrouwen_score: float,
    data_classificatie: str,
    model_status: str,
    drift_score: float,
) -> list[HITLTrigger]:
    """Evalueer welke HITL-triggers afgaan."""
    actieve_triggers = []

    if vertrouwen_score < 0.7:
        actieve_triggers.append(TRIGGERS[0])

    if data_classificatie in ("bijzondere_categorie", "GEHEIM"):
        actieve_triggers.append(TRIGGERS[1])

    if model_status != "productie":
        actieve_triggers.append(TRIGGERS[4])

    if drift_score < 0.7:
        actieve_triggers.append(TRIGGERS[3])

    return actieve_triggers
```

## Prompt Registry (versiebeheer)

```python
"""Prompt Registry — versiebeheer voor prompt-templates."""

from dataclasses import dataclass
from datetime import date


@dataclass
class PromptTemplate:
    template_id: str
    versie: str
    naam: str
    beschrijving: str
    auteur: str
    aangemaakt: date
    goedgekeurd_door: str | None
    goedgekeurd_op: date | None
    template: str
    variabelen: list[str]
    model_compatibiliteit: list[str]
    max_input_tokens: int
    verwachte_output_schema: dict | None  # JSON Schema


# Voorbeeld
PROMPTS: dict[str, PromptTemplate] = {
    "samenvatting-bezwaar-v3": PromptTemplate(
        template_id="samenvatting-bezwaar-v3",
        versie="3.1.0",
        naam="Samenvatting bezwaarschrift",
        beschrijving="Vat een bezwaarschrift samen in max 500 woorden",
        auteur="juridisch-team",
        aangemaakt=date(2026, 1, 10),
        goedgekeurd_door="sr-jurist-001",
        goedgekeurd_op=date(2026, 1, 15),
        template="""Je bent een juridisch assistent bij een Nederlandse gemeente.
Vat het volgende bezwaarschrift samen in maximaal 500 woorden.

Focus op:
1. De gronden van het bezwaar
2. De gevraagde voorziening
3. Relevante feiten en omstandigheden

Bezwaarschrift:
{bezwaarschrift_tekst}

Geef ALLEEN een feitelijke samenvatting. Geef GEEN juridisch oordeel.""",
        variabelen=["bezwaarschrift_tekst"],
        model_compatibiliteit=["claude-sonnet-4", "claude-haiku-4-5"],
        max_input_tokens=8000,
        verwachte_output_schema={
            "type": "object",
            "properties": {
                "samenvatting": {"type": "string", "maxLength": 3000},
            },
        },
    ),
}
```

## Conformiteitsbeoordeling (Art. 43) — Checklist

### Zelfbeoordeling hoog-risico AI-systeem

- [ ] **Risicomanagementsysteem (Art. 9)**
  - [ ] Risico-identificatie uitgevoerd (FMEA)
  - [ ] Restrisico's gedocumenteerd en geaccepteerd
  - [ ] Mitigatiemaatregelen geimplementeerd
  - [ ] Continu monitoringsplan opgesteld
- [ ] **Data governance (Art. 10)**
  - [ ] Trainingsdata gedocumenteerd (of: closed-source model — n.v.t.)
  - [ ] Inputdata-classificatie geimplementeerd
  - [ ] Bias-analyse uitgevoerd
  - [ ] Data lineage vastgelegd
- [ ] **Technische documentatie (Art. 11 / Annex IV)**
  - [ ] Model card ingevuld en actueel
  - [ ] Risicoregister bijgewerkt
  - [ ] Data governance document aanwezig
  - [ ] Incident response playbook opgesteld
- [ ] **Logging (Art. 12)**
  - [ ] Audit trail geimplementeerd (WORM-compatible)
  - [ ] Per-inferentie logging actief
  - [ ] Bewaarbeleid conform levensduur + 10 jaar
  - [ ] Keten-integriteitsverificatie werkt
- [ ] **Transparantie (Art. 13)**
  - [ ] Gebruikers geinformeerd dat AI wordt ingezet
  - [ ] Beperkingen van het systeem gecommuniceerd
  - [ ] Contactpunt voor vragen beschikbaar
- [ ] **Menselijk toezicht (Art. 14)**
  - [ ] HITL-protocol gedocumenteerd
  - [ ] Escalatiematrix opgesteld
  - [ ] Overridefunctionaliteit beschikbaar
  - [ ] Medewerkers getraind op AI-output beoordeling
- [ ] **Nauwkeurigheid en robuustheid (Art. 15)**
  - [ ] Behavioural tests geimplementeerd
  - [ ] Drift-detectie actief
  - [ ] Fallback-procedure bij model-uitval
  - [ ] Cybersecuritymaatregelen conform BIO2

## Projectstructuur (aanbevolen)

```
genai_project/
├── config/
│   ├── model_config.yaml         # Model parameters, routing
│   ├── prompt_templates.yaml     # Versiebeheerde prompts
│   ├── logging_config.yaml       # Structured logging (ECS)
│   ├── data_classification.yaml  # BIV-labels per domein
│   └── environments/             # DTAP-scheiding
│       ├── dev.yaml
│       ├── tst.yaml
│       ├── acc.yaml
│       └── prd.yaml
├── src/
│   ├── governance/               # EU AI Act controls
│   │   ├── audit_logger.py
│   │   ├── model_registry.py
│   │   ├── prompt_registry.py
│   │   ├── decision_recorder.py
│   │   ├── explainability.py
│   │   └── human_oversight.py
│   ├── security/                 # → zie skill llm-security
│   └── llm/                      # LLM client abstractie
├── governance_docs/              # Annex IV documentatie
├── tests/
│   ├── unit/
│   ├── integration/
│   ├── behavioural/              # LLM output gedragstests
│   └── security/                 # OWASP LLM Top 10
└── infrastructure/               # IaC, Helm, policies
```

## Rationale Matrix

| Module | Regelgeving | Risico | BIO2 control |
|--------|------------|--------|-------------|
| `audit_logger.py` | EU AI Act Art. 12, AVG Art. 5(2) | Non-repudiatie, verantwoording | BIO 10.3 |
| `decision_recorder.py` | EU AI Act Art. 14 | Traceerbaarheid besluiten | BIO 10.3 |
| `model_registry.py` | EU AI Act Annex IV | Ongedocumenteerd modelgebruik | BIO 12.1 |
| `prompt_registry.py` | EU AI Act Art. 12 | Onbeheerste prompt-wijzigingen | BIO 12.1 |
| `human_oversight.py` | EU AI Act Art. 14 | Ontbrekend menselijk toezicht | BIO 10.3 |
| `governance_docs/` | EU AI Act Art. 11, 43 | Ontbrekende conformiteit | — |
| `tests/behavioural/` | EU AI Act Art. 9, 15 | Model drift, bias | BIO 14.2 |

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **algoritmekader** | Regelgevend kader (AI Act risicoklassen, Algoritmeregister, Algoritmekader) |
| **iama-assessment** | Impact Assessment Mensenrechten en Algoritmen (grondrechtentoets) |
| **dpia-assessment** | Data Protection Impact Assessment (AVG-risicobeoordeling) |
| **llm-security** | OWASP LLM Top 10 beveiligingscontrols (prompt injection, DLP, sanitization) |
| **digitale-soevereiniteit** | CLOUD Act, soevereine hosting, BIV-classificatie voor AI-data |
| **avg-privacy** | AVG/GDPR compliance, verwerkingsregister, rechten betrokkenen |
| **logboek-dataverwerkingen** | Logboek Dataverwerkingen API voor AVG-transparantie |

## Meer informatie

- [EU AI Act volledige tekst](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) — officieel
- [Algoritmekader](https://minbzk.github.io/Algoritmekader/) — MinBZK implementatiekader
- [AI-verordening richtsnoeren](https://digital-strategy.ec.europa.eu/nl/policies/regulatory-framework-ai) — EC richtsnoeren
- [NIST AI RMF](https://airc.nist.gov/AI_RMF_Playbook) — complementair risicokader
