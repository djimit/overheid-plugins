---
name: dpia-assessment
description: >-
  Helpt bij het uitvoeren van een DPIA (Data Protection Impact Assessment /
  Gegevensbeschermingseffectbeoordeling) conform de AVG en het model van de
  Rijksoverheid. Begeleidt door alle stappen van het assessment met
  vragen, risicobeoordeling, maatregelen en AP-criteria. Gebruik deze skill
  wanneer de gebruiker vraagt over 'DPIA', 'data protection impact assessment',
  'gegevensbeschermingseffectbeoordeling', 'GEB', 'PIA',
  'privacy impact assessment', 'DPIA uitvoeren', 'DPIA invullen',
  'DPIA template', 'DPIA model', 'DPIA Rijksoverheid',
  'DPIA verplicht', 'DPIA criteria', 'AP DPIA-lijst',
  'risicobeoordeling privacy', 'privacy risk assessment',
  'voorafgaande raadpleging AP', 'prior consultation',
  'hoog risico verwerking', 'high risk processing',
  'DPIA artikel 35', 'DPIA algoritme', 'DPIA AI',
  'DPIA app', 'DPIA systeem', 'DPIA software',
  'privacy risico', 'privacy risk', 'restrisico',
  of wanneer de gebruiker een gegevensbeschermingseffectbeoordeling
  wil uitvoeren voor een systeem, applicatie of gegevensverwerking.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# DPIA — Gegevensbeschermingseffectbeoordeling

Voer een volledige DPIA uit conform Art. 35 AVG en het model van de Rijksoverheid om privacyrisico's te identificeren en te mitigeren.

Bron: [AP — DPIA](https://www.autoriteitpersoonsgegevens.nl/themas/basis-avg/praktisch-avg/data-protection-impact-assessment-dpia) | [DPIA-model Rijksoverheid](https://www.rijksoverheid.nl/documenten/rapporten/2017/09/29/model-gegevensbeschermingseffectbeoordeling-rijksdienst) | [AVG Art. 35](https://eur-lex.europa.eu/eli/reg/2016/679/oj)

## Wanneer is een DPIA verplicht?

Een DPIA is verplicht wanneer een verwerking **waarschijnlijk een hoog risico** inhoudt voor de rechten en vrijheden van betrokkenen (Art. 35 lid 1 AVG).

### Verplicht bij (Art. 35 lid 3)

| Situatie | Voorbeeld |
|----------|-----------|
| **Systematische en uitgebreide beoordeling** van persoonlijke aspecten (profilering) | Credit scoring, fraudedetectie, risicoprofilering |
| **Grootschalige verwerking** van bijzondere persoonsgegevens (Art. 9) of strafrechtelijke gegevens (Art. 10) | Medische dossiers, justitiële gegevens |
| **Stelselmatige en grootschalige monitoring** van openbaar toegankelijke ruimten | Cameratoezicht, wifi-tracking |

### AP-criteria (2 of meer = DPIA verplicht)

De Autoriteit Persoonsgegevens hanteert 9 criteria. Bij **2 of meer** is een DPIA verplicht:

| # | Criterium | Voorbeeld |
|---|----------|-----------|
| 1 | **Beoordelen of profileren** | Gedragsanalyse, risico-inschatting, scoring |
| 2 | **Geautomatiseerde besluitvorming met rechtsgevolgen** | Automatische afwijzing aanvraag, boete-oplegging |
| 3 | **Stelselmatige monitoring** | Cameratoezicht, locatietracking, netwerk-monitoring |
| 4 | **Gevoelige of bijzondere gegevens** | Gezondheid, etniciteit, politieke voorkeur, BSN, biometrie |
| 5 | **Grootschalige gegevensverwerking** | >5.000 betrokkenen of langdurig/permanent |
| 6 | **Gekoppelde databases** | Combineren van datasets uit verschillende bronnen |
| 7 | **Kwetsbare personen** | Kinderen, werknemers, patiënten, bijstandsgerechtigden, ouderen |
| 8 | **Nieuwe technologieën** | AI/ML, biometrische herkenning, IoT, blockchain |
| 9 | **Blokkering van recht, dienst of contract** | Toegangsweigering, uitkeringstop, contractbeëindiging |

### Beslisboom: is een DPIA nodig?

```
Start: Verwerkt het systeem persoonsgegevens?
├── Nee → Geen DPIA nodig
└── Ja → Tel AP-criteria
    ├── 0-1 criteria → DPIA aanbevolen maar niet verplicht
    ├── 2+ criteria → DPIA VERPLICHT
    └── Art. 35 lid 3 situatie → DPIA VERPLICHT

Uitzonderingen (Art. 35 lid 5):
- Verwerking staat op de AP-lijst van NIET-verplichtte DPIA's
- Verwerking is al beoordeeld in het kader van de wet zelf
```

## DPIA-stappenplan (7 stappen)

### Stap 1: Beschrijving van de verwerking

| Vraag | Toelichting |
|-------|-------------|
| **Wat is het doel?** | Concrete, specifieke doelomschrijving |
| **Welke gegevens worden verwerkt?** | Alle categorieën persoonsgegevens opsommen |
| **Van wie?** | Categorieën betrokkenen (burgers, medewerkers, etc.) |
| **Hoeveel betrokkenen?** | Schaal: exact of schatting |
| **Hoe lang bewaard?** | Bewaartermijnen per gegevenstype |
| **Wie heeft toegang?** | Interne medewerkers, externe verwerkers, derden |
| **Welke systemen?** | Software, databases, cloudproviders |
| **Welke gegevensstromen?** | Dataflow: van verzameling tot verwijdering |

### Dataflow-diagram template

```
┌──────────┐    ┌──────────────┐    ┌──────────────┐
│  Burger  │───→│  Webformulier │───→│  Applicatie  │
│ (betrok- │    │  (verzameling)│    │  (verwerking)│
│  kene)   │    └──────────────┘    └──────┬───────┘
└──────────┘                               │
                                    ┌──────▼───────┐
                                    │   Database   │
                                    │  (opslag)    │
                                    └──────┬───────┘
                                           │
              ┌────────────────────────────┤
              │                            │
       ┌──────▼───────┐           ┌────────▼──────┐
       │  Medewerker  │           │  Verwerker    │
       │  (inzage)    │           │  (hosting)    │
       └──────────────┘           └───────────────┘
```

### Stap 2: Noodzaak en proportionaliteit

| Vraag | Toetscriterium |
|-------|---------------|
| **Grondslag** | Welke AVG-grondslag (Art. 6)? Bij overheid: (c) wettelijke verplichting of (e) publieke taak |
| **Doelbinding** | Worden gegevens alleen voor het beschreven doel gebruikt? |
| **Dataminimalisatie** | Wordt elk gegeven daadwerkelijk gebruikt? Kan met minder? |
| **Juistheid** | Hoe wordt gewaarborgd dat gegevens correct en actueel zijn? |
| **Opslagbeperking** | Zijn bewaartermijnen gedefinieerd en geautomatiseerd? |
| **Subsidiariteit** | Kan het doel met minder ingrijpende middelen worden bereikt? |
| **Proportionaliteit** | Staat de inbreuk op privacy in verhouding tot het doel? |

### Stap 3: Risico-inventarisatie

Identificeer risico's voor de rechten en vrijheden van betrokkenen:

| Risicocategorie | Voorbeeldrisico's |
|----------------|-------------------|
| **Onrechtmatige verwerking** | Verwerking zonder grondslag, doelafwijking, te veel gegevens |
| **Ongeautoriseerde toegang** | Datalek, hacking, onbevoegde medewerker |
| **Ongewenste openbaarmaking** | Lekken van gevoelige gegevens, verkeerd geadresseerd |
| **Verlies of vernietiging** | Ransomware, hardwarefalen, menselijke fout |
| **Onrechtmatige besluitvorming** | Onjuist profiel, discriminatie, kafkaësk effect |
| **Beperking rechten betrokkenen** | Inzageverzoek niet gehonoreerd, geen correctiemogelijkheid |
| **Function creep** | Gegevens worden later voor ander doel gebruikt |
| **Chilling effect** | Mensen passen gedrag aan omdat ze weten dat ze gemonitord worden |

### Stap 4: Risicobeoordeling

Beoordeel elk risico op **kans** en **impact**:

| | **Impact: Laag** | **Impact: Midden** | **Impact: Hoog** | **Impact: Zeer hoog** |
|---|---|---|---|---|
| **Kans: Zeer hoog** | Midden | Hoog | Zeer hoog | Zeer hoog |
| **Kans: Hoog** | Midden | Hoog | Hoog | Zeer hoog |
| **Kans: Midden** | Laag | Midden | Hoog | Hoog |
| **Kans: Laag** | Laag | Laag | Midden | Hoog |

**Impact-schaal:**

| Niveau | Beschrijving | Voorbeeld |
|--------|-------------|-----------|
| **Laag** | Beperkt ongemak | Onterecht nieuwsbrief ontvangen |
| **Midden** | Significante hinder | Onjuiste creditcheck, vertraagde dienstverlening |
| **Hoog** | Ernstige schade | Financieel verlies, discriminatie, reputatieschade |
| **Zeer hoog** | Onomkeerbare schade | Fysiek gevaar, verlies vrijheid, existentiële bedreiging |

```python
from dataclasses import dataclass
from enum import IntEnum

class Kans(IntEnum):
    LAAG = 1
    MIDDEN = 2
    HOOG = 3
    ZEER_HOOG = 4

class Impact(IntEnum):
    LAAG = 1
    MIDDEN = 2
    HOOG = 3
    ZEER_HOOG = 4

class Risiconiveau(IntEnum):
    LAAG = 1       # Acceptabel
    MIDDEN = 2     # Mitigeren aanbevolen
    HOOG = 3       # Mitigeren verplicht
    ZEER_HOOG = 4  # Voorafgaande raadpleging AP of stoppen

@dataclass
class PrivacyRisico:
    beschrijving: str
    categorie: str
    kans: Kans
    impact: Impact
    maatregelen: list[str]
    restrisico_kans: Kans | None = None
    restrisico_impact: Impact | None = None

    @property
    def risiconiveau(self) -> Risiconiveau:
        score = self.kans * self.impact
        if score <= 2: return Risiconiveau.LAAG
        if score <= 6: return Risiconiveau.MIDDEN
        if score <= 9: return Risiconiveau.HOOG
        return Risiconiveau.ZEER_HOOG

    @property
    def restrisico(self) -> Risiconiveau | None:
        if self.restrisico_kans and self.restrisico_impact:
            score = self.restrisico_kans * self.restrisico_impact
            if score <= 2: return Risiconiveau.LAAG
            if score <= 6: return Risiconiveau.MIDDEN
            if score <= 9: return Risiconiveau.HOOG
            return Risiconiveau.ZEER_HOOG
        return None
```

### Stap 5: Maatregelen

Per geïdentificeerd risico maatregelen bepalen:

| Risicotype | Technische maatregelen | Organisatorische maatregelen |
|-----------|----------------------|----------------------------|
| **Ongeautoriseerde toegang** | Encryptie, MFA, RBAC, netwerksegmentatie | Autorisatiebeleid, functiescheiding |
| **Datalek** | WAF, IDS/IPS, DLP, logging | Incidentresponsplan, datalekprocedure |
| **Te veel gegevens** | Dataminimalisatie in queries, field-level security | Periodieke review noodzaak gegevens |
| **Te lang bewaard** | Automatische verwijdering, retention policies | Bewaartermijnenregister |
| **Onrechtmatig besluit** | Uitlegbare algoritmen, audit-logging | Menselijke controle, bezwaarprocedure |
| **Geen inzage mogelijk** | Self-service portaal, export API | Procedure inzageverzoeken |
| **Function creep** | Purpose binding in autorisaties | Verwerkingsregister, DPIA bij nieuw doel |

### Stap 6: Restrisicobeoordeling

Na maatregelen opnieuw beoordelen:

```
Oorspronkelijk risico → Maatregelen → Restrisico
     Hoog (3x3=9)   → Encryptie,   → Midden (2x2=4)  ✓ Acceptabel
                       MFA, logging

Als restrisico HOOG of ZEER HOOG:
├── Aanvullende maatregelen treffen
├── Risico expliciet accepteren (door bevoegd gezag)
└── Of: voorafgaande raadpleging AP (Art. 36 AVG)
```

### Stap 7: Documentatie en goedkeuring

| Onderdeel | Verplicht |
|-----------|-----------|
| **DPIA-rapport** | Ja — bewaar als verantwoordingsdocument |
| **Advies FG** | Ja — functionaris gegevensbescherming moet adviseren (Art. 35 lid 2) |
| **Goedkeuring** | Ja — door verwerkingsverantwoordelijke |
| **Verwerkingsregister** | Update verwerkingsregister met DPIA-bevindingen |
| **Herziening** | Bij significante wijzigingen; minimaal elke 3 jaar |

## Voorafgaande raadpleging AP (Art. 36)

Verplicht wanneer na de DPIA het **restrisico hoog blijft** ondanks maatregelen:

| Stap | Detail |
|------|--------|
| **Wanneer** | Restrisico is hoog en kan niet verder worden gemitigeerd |
| **Wat indienen** | DPIA-rapport, verwerkingsbeschrijving, maatregelen, FG-advies |
| **Termijn** | AP reageert binnen 8 weken (verlengbaar met 6 weken) |
| **Uitkomst** | AP kan aanvullende maatregelen eisen of verwerking verbieden |

## DPIA voor specifieke scenario's

### DPIA bij algoritme/AI

Aanvullende vragen naast standaard DPIA:

| Vraag | Toelichting |
|-------|-------------|
| Wat voor type algoritme? | Regelgebaseerd / ML / deep learning / LLM |
| Worden besluiten automatisch genomen? | Art. 22 AVG: recht op menselijke tussenkomst |
| Zijn er proxyvariabelen? | Postcode, naam als proxy voor beschermde kenmerken |
| Is bias getoetst? | Fairness-metrics per subgroep |
| Is het model uitlegbaar? | Per individueel geval uitleggen |
| **IAMA ook nodig?** | Ja — IAMA naast DPIA uitvoeren |

### DPIA bij cloudmigratie

| Vraag | Toelichting |
|-------|-------------|
| Waar staan de servers? | EU/EER of derde land? |
| Welke doorgifte-waarborgen? | SCC's, adequaatheidsbesluit, BCR |
| Heeft cloudprovider toegang? | Subverwerker; verwerkersovereenkomst vereist |
| Hoe worden data verwijderd? | Cryptographic erasure, fysieke vernietiging |
| Wat bij faillissement provider? | Exit-strategie, data-extractie |

### DPIA bij app/portaal voor burgers

| Vraag | Toelichting |
|-------|-------------|
| Welke authenticatie? | DigiD (betrouwbaarheidsniveau) |
| Welke gegevens worden getoond? | BSN, inkomen, gezondheid — maskeren! |
| Logging van burgeracties? | Alleen noodzakelijk; niet tot profiel herleidbaar |
| Analytics? | Geen tracking-cookies zonder toestemming |
| Toegankelijkheid? | WCAG 2.1 AA (geen privacy via uitsluiting) |

## DPIA-rapport template

```markdown
# DPIA: [Naam systeem/verwerking]

**Versie**: [versienummer]
**Datum**: [datum]
**Verwerkingsverantwoordelijke**: [organisatie]
**FG**: [naam + contactgegevens]
**Status**: [concept / FG-advies gevraagd / goedgekeurd]

## 1. Beschrijving verwerking
- Doel: [...]
- Categorieën persoonsgegevens: [...]
- Categorieën betrokkenen: [...]
- Aantal betrokkenen: [...]
- Bewaartermijnen: [...]
- Ontvangers: [...]
- Systemen en verwerkers: [...]
- Dataflow-diagram: [...]

## 2. AP-criteria toets
| Criterium | Van toepassing? | Toelichting |
|-----------|----------------|-------------|
| Beoordelen/profileren | Ja/Nee | [...] |
| Geautomatiseerde besluitvorming | Ja/Nee | [...] |
| [etc. voor alle 9 criteria] | | |
**Conclusie**: [x] criteria van toepassing → DPIA [verplicht/niet verplicht]

## 3. Noodzaak en proportionaliteit
- Grondslag: [...]
- Doelbinding: [...]
- Dataminimalisatie: [...]
- Subsidiariteit: [...]

## 4. Risico-inventarisatie en beoordeling
| Risico | Kans | Impact | Niveau | Maatregelen | Restkans | Restimpact | Restniveau |
|--------|------|--------|--------|-------------|----------|------------|------------|
| [...] | [...] | [...] | [...] | [...] | [...] | [...] | [...] |

## 5. Restrisicobeoordeling
[Beoordeling of restrisico's acceptabel zijn]

## 6. Advies FG
[Advies van de functionaris gegevensbescherming]

## 7. Besluit
[Goedkeuring door verwerkingsverantwoordelijke]
[Eventueel: voorafgaande raadpleging AP nodig?]

## Bijlagen
- Verwerkingsregister-entry
- Verwerkersovereenkomsten
- Technische beveiligingsmaatregelen
```

## Implementatie-checklist

- [ ] **AP-criteria getoetst**: alle 9 criteria beoordeeld; conclusie DPIA verplicht/niet verplicht
- [ ] **Beschrijving compleet**: doel, gegevens, betrokkenen, bewaartermijnen, systemen, dataflow
- [ ] **Noodzaak en proportionaliteit**: grondslag, doelbinding, dataminimalisatie, subsidiariteit beoordeeld
- [ ] **Risico-inventarisatie**: alle relevante risico's geidentificeerd per categorie
- [ ] **Risicobeoordeling**: kans x impact matrix ingevuld voor elk risico
- [ ] **Maatregelen**: technische en organisatorische maatregelen per risico bepaald
- [ ] **Restrisico**: restrisico beoordeeld na maatregelen
- [ ] **FG-advies**: functionaris gegevensbescherming heeft geadviseerd (Art. 35 lid 2)
- [ ] **Goedkeuring**: verwerkingsverantwoordelijke heeft DPIA goedgekeurd
- [ ] **Voorafgaande raadpleging**: bij hoog restrisico: AP geraadpleegd (Art. 36)
- [ ] **Verwerkingsregister**: bijgewerkt met DPIA-bevindingen
- [ ] **Herziening gepland**: datum voor herziening vastgesteld (bij wijzigingen of max 3 jaar)
- [ ] **IAMA**: apart IAMA uitgevoerd indien algoritme/AI betrokken is

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **avg-privacy** | AVG-grondslagen, Privacy by Design patronen, verwerkingsregister, rechten betrokkenen |
| **iama-assessment** | IAMA uitvoeren naast DPIA wanneer algoritmen of AI-systemen betrokken zijn |
| **algoritmekader** | AI Act risicoklassen en conformiteitsbeoordeling bij algoritmische verwerking |
| **overheid-authenticatie** | DigiD/eHerkenning beveiligingseisen bij authenticatie in de verwerking |
| **genai-governance** | EU AI Act governance (conformiteitsbeoordeling, audit trail) |
| **sociaal-domein** | DPIA-specifics voor sociaal domein (bijzondere persoonsgegevens, Suwinet) |

## Meer informatie

- [AP — DPIA](https://www.autoriteitpersoonsgegevens.nl/themas/basis-avg/praktisch-avg/data-protection-impact-assessment-dpia)
- [DPIA-model Rijksoverheid](https://www.rijksoverheid.nl/documenten/rapporten/2017/09/29/model-gegevensbeschermingseffectbeoordeling-rijksdienst)
- [AP — Lijst verplichte DPIA's](https://www.autoriteitpersoonsgegevens.nl/nl/zelf-doen/data-protection-impact-assessment-dpia#702)
- [AVG Art. 35-36](https://eur-lex.europa.eu/eli/reg/2016/679/oj) — DPIA en voorafgaande raadpleging
- [EDPB Guidelines DPIA](https://edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-data-protection-impact-assessment-and-determining_en)
- [CNIL PIA tool](https://www.cnil.fr/en/privacy-impact-assessment-pia) — open-source DPIA-tool (referentie)
