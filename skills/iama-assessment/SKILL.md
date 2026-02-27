---
name: iama-assessment
description: >-
  Helpt bij het uitvoeren van een IAMA (Impact Assessment Mensenrechten en
  Algoritmen) voor overheidsinstellingen die algoritmen of AI-systemen
  inzetten. Begeleidt door alle drie fasen van het assessment met
  alle vragen, beoordelingscriteria en beslisbomen. Gebruik deze skill
  wanneer de gebruiker vraagt over 'IAMA', 'impact assessment mensenrechten',
  'impact assessment algoritmen', 'mensenrechtentoets algoritme',
  'human rights impact assessment', 'IAMA invullen', 'IAMA uitvoeren',
  'IAMA template', 'IAMA fase 1', 'IAMA fase 2', 'IAMA fase 3',
  'grondrechtentoets', 'fundamental rights assessment',
  'discriminatietoets algoritme', 'bias assessment',
  'algoritme impact', 'algorithm impact assessment',
  'proportionaliteitstoets algoritme', 'FRAIA',
  'non-discriminatie algoritme', 'eerlijkheid algoritme',
  'fairness assessment', 'mensenrechten AI', 'human rights AI',
  'artikel 22 AVG toets', 'geautomatiseerde besluitvorming toets',
  'transparantie algoritme beoordeling',
  of wanneer de gebruiker een algoritme of AI-systeem wil toetsen
  op impact op mensenrechten en grondrechten.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# IAMA — Impact Assessment Mensenrechten en Algoritmen

Voer een volledige IAMA uit om de impact van algoritmen en AI-systemen op mensenrechten en grondrechten te beoordelen.

Bron: [IAMA — Universiteit Utrecht](https://www.rijksoverheid.nl/documenten/rapporten/2021/02/25/impact-assessment-mensenrechten-en-algoritmen) | [Algoritmekader](https://minbzk.github.io/Algoritmekader/) | [AI Act](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)

## Wat is het IAMA?

| Aspect | Detail |
|--------|--------|
| **Doel** | Systematisch beoordelen van de impact van algoritmen op mensenrechten en grondrechten |
| **Ontwikkeld door** | Universiteit Utrecht, in opdracht van het Ministerie van BZK |
| **Verplicht** | Aanbevolen voor alle overheidsalgoritmen; verplicht bij hoog-risico (Algoritmekader) |
| **Wanneer** | Vóór inzet van het algoritme; herhalen bij significante wijzigingen |
| **Wie** | Multidisciplinair team: beleid, juridisch, technisch, ethisch, domeinexperts |
| **Relatie AI Act** | IAMA voldoet grotendeels aan conformiteitsbeoordeling AI Act voor hoog-risico |
| **Relatie DPIA** | IAMA vervangt DPIA niet; beide kunnen nodig zijn. IAMA is breder (alle grondrechten) |

## Overzicht drie fasen

```
┌──────────────────────────────────────────────────────────┐
│  FASE 1: VOORBEREIDING                                   │
│  Waarom? Wat? Wie? → Context en doelstelling bepalen     │
├──────────────────────────────────────────────────────────┤
│  FASE 2A: INPUTDATA EN MODELLERING                       │
│  Data, aannames, modellering → Technische analyse        │
├──────────────────────────────────────────────────────────┤
│  FASE 2B: GRONDRECHTENTOETS                              │
│  Per grondrecht toetsen → Juridische analyse             │
├──────────────────────────────────────────────────────────┤
│  FASE 3: IMPLEMENTATIE EN TOEZICHT                       │
│  Waarborgen, transparantie, monitoring → Governance      │
└──────────────────────────────────────────────────────────┘
```

## Fase 1: Voorbereiding

### 1.1 Probleemanalyse

| # | Vraag | Toelichting |
|---|-------|-------------|
| 1.1 | **Welk probleem wordt opgelost?** | Beschrijf het maatschappelijke of bestuurlijke probleem concreet |
| 1.2 | **Wat is het doel van de inzet van het algoritme?** | Specifiek, meetbaar doel formuleren |
| 1.3 | **Welke publieke waarde wordt gediend?** | Bijv. veiligheid, efficiëntie, gelijkheid, rechtmatigheid |
| 1.4 | **Zijn er alternatieven zonder algoritme?** | Menselijke beoordeling, eenvoudiger regels, geen actie |
| 1.5 | **Waarom is een algoritme de beste keuze?** | Onderbouw de noodzaak en meerwaarde t.o.v. alternatieven |

### 1.2 Type algoritme

| # | Vraag | Toelichting |
|---|-------|-------------|
| 1.6 | **Wat voor type algoritme wordt ingezet?** | Regelgebaseerd / machine learning / deep learning / LLM / hybride |
| 1.7 | **Is het een zelflerend systeem?** | Verandert het model na deployment op basis van nieuwe data? |
| 1.8 | **Hoe complex is het model?** | Eenvoudige beslisboom vs. neuraal netwerk — bepaalt uitlegbaarheid |
| 1.9 | **Wat is de rol van het algoritme in het besluitvormingsproces?** | Zie beslismatrix hieronder |

### Beslismatrix: rol van het algoritme

| Rol | Beschrijving | Risico | Art. 22 AVG |
|-----|-------------|--------|-------------|
| **Ondersteunend** | Geeft informatie; mens neemt besluit | Lager | Niet van toepassing |
| **Adviserend** | Doet voorstel; mens kan afwijken | Middel | Mogelijk van toepassing |
| **Semi-autonoom** | Neemt besluit; mens controleert steekproefsgewijs | Hoog | Waarschijnlijk van toepassing |
| **Autonoom** | Neemt besluit zonder menselijke tussenkomst | Zeer hoog | Van toepassing (verbod tenzij uitzondering) |

### 1.3 Betrokkenen en getroffenen

| # | Vraag | Toelichting |
|---|-------|-------------|
| 1.10 | **Wie zijn de directe getroffenen?** | Personen over wie een besluit wordt genomen |
| 1.11 | **Zijn er kwetsbare groepen betrokken?** | Kinderen, ouderen, laaggeletterden, bijstandsgerechtigden, migranten |
| 1.12 | **Hoeveel personen worden geraakt?** | Schaal: individueel, honderden, duizenden, miljoenen |
| 1.13 | **Wat is de ernst van de impact?** | Financieel, vrijheidsbeperkend, discriminerend, stigmatiserend |
| 1.14 | **Welke stakeholders zijn betrokken?** | Beleidsmakers, uitvoerders, toezichthouders, belangenorganisaties |

### 1.4 Wettelijk kader

| # | Vraag | Toelichting |
|---|-------|-------------|
| 1.15 | **Wat is de wettelijke grondslag?** | Welke wet/regeling geeft bevoegdheid tot algoritmisch besluit? |
| 1.16 | **Is er een specifieke wettelijke grondslag voor profilering?** | Art. 22 AVG: verbod op uitsluitend geautomatiseerde besluiten met rechtsgevolg |
| 1.17 | **Is een DPIA vereist?** | Waarschijnlijk ja als persoonsgegevens worden verwerkt |
| 1.18 | **Wat is de AI Act-risicoklasse?** | Verboden / hoog-risico / beperkt risico / minimaal risico |

## Fase 2A: Data en modellering

### 2A.1 Inputdata

| # | Vraag | Toelichting |
|---|-------|-------------|
| 2A.1 | **Welke data wordt gebruikt?** | Alle databronnen, variabelen en kenmerken opsommen |
| 2A.2 | **Bevatten de data persoonsgegevens?** | Directe of indirecte identificatie; bijzondere categorieën? |
| 2A.3 | **Bevatten de data proxyvariabelen voor beschermde kenmerken?** | Postcode → etniciteit, naam → geslacht, etc. |
| 2A.4 | **Wat is de kwaliteit van de data?** | Compleetheid, actualiteit, representativiteit, labeling-kwaliteit |
| 2A.5 | **Zijn er bekende biases in de data?** | Historische bias, selectiebias, meetbias, representatiebias |
| 2A.6 | **Hoe is de data verzameld?** | Bron, methode, toestemming, hergebruik |

### Proxyvariabelen — veelvoorkomende risico's

| Variabele | Kan proxy zijn voor | Risico |
|-----------|-------------------|--------|
| Postcode/wijk | Etniciteit, inkomen | Indirecte discriminatie |
| Naam | Etniciteit, geslacht | Indirecte discriminatie |
| Taal | Nationaliteit, etniciteit | Uitsluiting |
| Leeftijd | Digitale vaardigheid | Leeftijdsdiscriminatie |
| Type uitkering | Sociaaleconomische status | Stigmatisering |
| Schuldenhistorie | Sociaaleconomische status | Uitsluiting kwetsbare groepen |

### 2A.2 Modellering

| # | Vraag | Toelichting |
|---|-------|-------------|
| 2A.7 | **Welke aannames liggen ten grondslag aan het model?** | Expliciteer alle impliciete en expliciete aannames |
| 2A.8 | **Hoe is het model getraind en gevalideerd?** | Train/test split, cross-validatie, onafhankelijke validatieset |
| 2A.9 | **Wat zijn de prestatiemaatstaven?** | Accuracy, precision, recall, F1, AUC-ROC — per subgroep |
| 2A.10 | **Is het model uitlegbaar?** | Kan per individueel geval worden uitgelegd waarom dit resultaat? |
| 2A.11 | **Zijn er fairness-metrics berekend?** | Demographic parity, equalized odds, calibration — per groep |
| 2A.12 | **Hoe gaat het model om met edge cases en outliers?** | Ongebruikelijke situaties, ontbrekende data |

### Fairness-metrics

| Metric | Definitie | Geschikt voor |
|--------|-----------|---------------|
| **Demographic Parity** | Uitkomst onafhankelijk van groep | Gelijke behandeling op uitkomstniveau |
| **Equalized Odds** | Gelijke true positive en false positive rates per groep | Classificatietaken met grondwaarheid |
| **Predictive Parity** | Gelijke precision per groep | Wanneer vertrouwen in uitkomst belangrijk is |
| **Calibration** | Score X% betekent X% kans voor alle groepen | Risicoschattingen |
| **Individual Fairness** | Vergelijkbare personen krijgen vergelijkbare uitkomsten | Wanneer individuele vergelijking mogelijk is |

```python
# Voorbeeld: fairness-metrics berekenen
from sklearn.metrics import confusion_matrix

def calculate_fairness_metrics(y_true, y_pred, group_labels):
    """Bereken fairness-metrics per groep voor IAMA fase 2A."""
    metrics = {}
    groups = set(group_labels)

    for group in groups:
        mask = [g == group for g in group_labels]
        y_true_g = [y for y, m in zip(y_true, mask) if m]
        y_pred_g = [y for y, m in zip(y_pred, mask) if m]

        tn, fp, fn, tp = confusion_matrix(y_true_g, y_pred_g).ravel()
        metrics[group] = {
            "positive_rate": (tp + fp) / len(y_true_g),     # Demographic parity
            "true_positive_rate": tp / (tp + fn) if (tp + fn) > 0 else 0,  # Equalized odds
            "false_positive_rate": fp / (fp + tn) if (fp + tn) > 0 else 0,
            "precision": tp / (tp + fp) if (tp + fp) > 0 else 0,  # Predictive parity
        }

    return metrics
```

## Fase 2B: Grondrechtentoets

Toets het algoritme aan elk relevant grondrecht. Voor elk grondrecht: **is er een inbreuk? Zo ja, is die gerechtvaardigd?**

### Toetsingskader per grondrecht

| # | Grondrecht | Wettelijke basis | Kernvragen |
|---|-----------|-----------------|------------|
| 2B.1 | **Non-discriminatie en gelijkheid** | Art. 1 Gw, Art. 14 EVRM, Art. 21 EU-Handvest | Worden groepen ongelijk behandeld? Is dat objectief gerechtvaardigd? |
| 2B.2 | **Privacy en gegevensbescherming** | Art. 10 Gw, Art. 8 EVRM, Art. 7-8 EU-Handvest, AVG | Worden persoonsgegevens verwerkt? Is er een grondslag? Dataminimalisatie? |
| 2B.3 | **Menselijke waardigheid** | Art. 1 EU-Handvest | Wordt iemand gereduceerd tot een datapunt? Stigmatisering? |
| 2B.4 | **Autonomie en zelfbeschikking** | Art. 10-11 Gw | Wordt de keuzevrijheid beperkt? Kan betrokkene invloed uitoefenen? |
| 2B.5 | **Recht op een eerlijk proces** | Art. 6 EVRM, Art. 47 EU-Handvest | Is er bezwaar/beroep mogelijk? Kan het besluit worden uitgelegd? |
| 2B.6 | **Vrijheid van meningsuiting** | Art. 7 Gw, Art. 10 EVRM | Beperkt het algoritme de uitingsvrijheid? (contentmoderatie, filtering) |
| 2B.7 | **Recht op toegang tot overheidsdiensten** | Art. 41 EU-Handvest, Awb | Worden groepen uitgesloten van dienstverlening? |
| 2B.8 | **Sociale grondrechten** | Art. 19-23 Gw | Impact op recht op huisvesting, onderwijs, gezondheidszorg, bestaanszekerheid? |

### Toetsingsschema per grondrecht

Voor **elk** relevant grondrecht doorloop:

```
1. INBREUK?
   ├── Nee → Geen verdere toetsing nodig
   └── Ja → Ga naar 2

2. WETTELIJKE GRONDSLAG?
   ├── Nee → NIET TOEGESTAAN (stop)
   └── Ja → Ga naar 3

3. LEGITIEM DOEL?
   ├── Nee → NIET GERECHTVAARDIGD (stop)
   └── Ja → Ga naar 4

4. NOODZAKELIJK EN PROPORTIONEEL?
   ├── Nee → NIET PROPORTIONEEL → mitigeren of stoppen
   └── Ja → Ga naar 5

5. MITIGERENDE MAATREGELEN?
   └── Documenteer welke waarborgen zijn ingericht
```

### Non-discriminatie — verdiepende vragen

| # | Vraag |
|---|-------|
| 2B.1a | Maakt het algoritme direct onderscheid op beschermde gronden (geslacht, ras, leeftijd, handicap, religie, seksuele gerichtheid, nationaliteit)? |
| 2B.1b | Maakt het algoritme indirect onderscheid via proxyvariabelen? |
| 2B.1c | Zijn de uitkomsten getoetst op ongelijke impact per groep (disparate impact)? |
| 2B.1d | Is een eventueel onderscheid objectief gerechtvaardigd (legitiem doel, noodzakelijk, proportioneel)? |
| 2B.1e | Is de **80%-regel** (four-fifths rule) toegepast als eerste indicatie van adverse impact? |
| 2B.1f | Zijn intersectionele effecten getoetst (bijv. vrouwen + migratie-achtergrond)? |

### 80%-regel (four-fifths rule)

```python
def four_fifths_rule(positive_rate_group_a: float, positive_rate_group_b: float) -> dict:
    """
    Toets de 80%-regel voor adverse impact (IAMA 2B.1e).
    Als de ratio < 0.8, is er een indicatie van adverse impact.
    """
    if positive_rate_group_a == 0 or positive_rate_group_b == 0:
        return {"ratio": 0.0, "adverse_impact": True, "warning": "Een groep heeft 0% positive rate"}

    ratio = min(positive_rate_group_a, positive_rate_group_b) / max(positive_rate_group_a, positive_rate_group_b)
    return {
        "ratio": round(ratio, 3),
        "adverse_impact": ratio < 0.8,
        "beoordeling": "Mogelijke adverse impact — nadere analyse nodig" if ratio < 0.8 else "Geen indicatie adverse impact"
    }
```

## Fase 3: Implementatie en toezicht

### 3.1 Transparantie

| # | Vraag | Toelichting |
|---|-------|-------------|
| 3.1 | **Is het algoritme opgenomen in het Algoritmeregister?** | Verplicht voor overheidsalgoritmen |
| 3.2 | **Kunnen getroffenen achterhalen dat een algoritme is gebruikt?** | Transparantieplicht (Art. 22 AVG, AI Act) |
| 3.3 | **Kan per individueel geval worden uitgelegd hoe het besluit tot stand kwam?** | Uitlegbaarheid; recht op menselijke beoordeling |
| 3.4 | **Is de broncode openbaar?** | Open source tenzij zwaarwegend belang zich verzet |
| 3.5 | **Is de documentatie begrijpelijk voor niet-experts?** | Publieksvriendelijke uitleg; B1-taalniveau |

### 3.2 Menselijke controle (Human oversight)

| # | Vraag | Toelichting |
|---|-------|-------------|
| 3.6 | **Wie is verantwoordelijk voor het uiteindelijke besluit?** | Ambtelijk verantwoordelijke aanwijzen |
| 3.7 | **Kan een mens het algoritmisch advies overrulen?** | "Human-in-the-loop" of "human-on-the-loop"? |
| 3.8 | **Is automation bias onderkend en gemitigeerd?** | Training, steekproeven, verplichte afwijkingspercentage |
| 3.9 | **Wat gebeurt er bij technische storing?** | Fallback-procedure zonder algoritme |

### 3.3 Bezwaar en beroep

| # | Vraag | Toelichting |
|---|-------|-------------|
| 3.10 | **Kunnen getroffenen bezwaar maken?** | Conform Awb; laagdrempelig, digitaal |
| 3.11 | **Wordt bij bezwaar het algoritmisch besluit inhoudelijk herbeoordeeld door een mens?** | Volledige herbeoordeling, niet alleen herhaling algoritme |
| 3.12 | **Worden bezwaaruitkomsten teruggekoppeld naar modelverbetering?** | Feedbackloop voor modelkwaliteit |

### 3.4 Monitoring en evaluatie

| # | Vraag | Toelichting |
|---|-------|-------------|
| 3.13 | **Hoe vaak wordt het model geëvalueerd?** | Minimaal jaarlijks; frequenter bij zelflerende systemen |
| 3.14 | **Worden fairness-metrics continu gemonitord?** | Drift-detectie op prestatie en eerlijkheid per subgroep |
| 3.15 | **Wat zijn de exit-criteria?** | Wanneer wordt het algoritme stopgezet? Drempelwaarden |
| 3.16 | **Is er een noodstopprocedure?** | Wie kan het algoritme direct uitschakelen? |

### Monitoring implementatie

```python
from dataclasses import dataclass
from datetime import datetime

@dataclass
class IAMAMonitoringConfig:
    """Configuratie voor continue IAMA-monitoring (Fase 3.4)."""
    model_id: str
    evaluatie_frequentie_dagen: int = 90
    fairness_threshold: float = 0.8       # 80%-regel
    performance_threshold: float = 0.7    # Minimum acceptable performance
    drift_threshold: float = 0.05         # Max afwijking t.o.v. baseline
    beschermde_kenmerken: list[str] = None # Groepen om te monitoren

    def __post_init__(self):
        if self.beschermde_kenmerken is None:
            self.beschermde_kenmerken = [
                "geslacht", "leeftijd_groep", "herkomst", "woonregio"
            ]

@dataclass
class IAMAEvaluatieResultaat:
    model_id: str
    datum: datetime
    overall_performance: float
    fairness_per_groep: dict[str, float]
    drift_gedetecteerd: bool
    actie_vereist: bool
    aanbeveling: str

def evalueer_model(config: IAMAMonitoringConfig, y_true, y_pred, groepen) -> IAMAEvaluatieResultaat:
    """Voer periodieke IAMA-evaluatie uit."""
    from sklearn.metrics import accuracy_score

    overall = accuracy_score(y_true, y_pred)
    fairness = {}
    actie = False

    for kenmerk in config.beschermde_kenmerken:
        if kenmerk in groepen:
            for groep_waarde in set(groepen[kenmerk]):
                mask = [g == groep_waarde for g in groepen[kenmerk]]
                groep_perf = accuracy_score(
                    [y for y, m in zip(y_true, mask) if m],
                    [y for y, m in zip(y_pred, mask) if m]
                )
                fairness[f"{kenmerk}:{groep_waarde}"] = groep_perf
                if groep_perf / overall < config.fairness_threshold:
                    actie = True

    return IAMAEvaluatieResultaat(
        model_id=config.model_id,
        datum=datetime.utcnow(),
        overall_performance=overall,
        fairness_per_groep=fairness,
        drift_gedetecteerd=False,  # Vergelijk met baseline
        actie_vereist=actie,
        aanbeveling="Herziening model vereist: fairness-threshold overschreden" if actie else "Geen actie vereist"
    )
```

## IAMA-rapport template

```markdown
# IAMA-rapport: [Naam algoritme]

**Versie**: [versienummer]
**Datum**: [datum]
**Verantwoordelijke**: [naam + functie]
**Status**: [concept / definitief / herzien]

## Samenvatting
[Beknopte beschrijving: wat doet het algoritme, voor wie, wat is de impact]

## Fase 1: Voorbereiding
### Probleem en doel
[Beantwoord vragen 1.1 t/m 1.5]
### Type algoritme
[Beantwoord vragen 1.6 t/m 1.9]
### Betrokkenen
[Beantwoord vragen 1.10 t/m 1.14]
### Wettelijk kader
[Beantwoord vragen 1.15 t/m 1.18]

## Fase 2A: Data en modellering
### Data
[Beantwoord vragen 2A.1 t/m 2A.6]
### Model
[Beantwoord vragen 2A.7 t/m 2A.12]
### Fairness-metrics
[Resultaten per groep]

## Fase 2B: Grondrechtentoets
### Per grondrecht
[Voor elk relevant grondrecht het toetsingsschema doorlopen]

## Fase 3: Implementatie
### Transparantie
[Beantwoord vragen 3.1 t/m 3.5]
### Menselijke controle
[Beantwoord vragen 3.6 t/m 3.9]
### Bezwaar en beroep
[Beantwoord vragen 3.10 t/m 3.12]
### Monitoring
[Beantwoord vragen 3.13 t/m 3.16]

## Conclusie en maatregelen
[Samenvatting risico's en genomen maatregelen]

## Bijlagen
- Fairness-metrics rapport
- Algoritmeregister-publicatie
- DPIA (indien uitgevoerd)
```

## Relatie met andere assessments

| Assessment | Scope | Wanneer naast IAMA? |
|-----------|-------|---------------------|
| **DPIA** | Privacy en gegevensbescherming | Altijd als persoonsgegevens worden verwerkt |
| **AI Act conformiteitsbeoordeling** | Hoog-risico AI-systemen | Bij AI Act hoog-risico classificatie |
| **Algoritmeregister** | Transparantie | Altijd (publicatieplicht) |
| **BIA** (Business Impact Assessment) | Bedrijfscontinuiteit | Bij kritische processen |

## Implementatie-checklist

- [ ] **Multidisciplinair team**: beleid, juridisch, technisch, ethisch en domeinexperts betrokken
- [ ] **Fase 1 compleet**: probleemanalyse, type algoritme, betrokkenen, wettelijk kader beoordeeld
- [ ] **Fase 2A compleet**: data geanalyseerd op bias; model gevalideerd; fairness-metrics berekend per subgroep
- [ ] **Fase 2B compleet**: alle relevante grondrechten getoetst via het toetsingsschema
- [ ] **Non-discriminatie**: 80%-regel getoetst; proxyvariabelen geidentificeerd; intersectionele effecten getoetst
- [ ] **Fase 3 compleet**: transparantie, menselijke controle, bezwaar/beroep, monitoring ingericht
- [ ] **Algoritmeregister**: algoritme gepubliceerd in het Algoritmeregister
- [ ] **DPIA**: apart uitgevoerd indien persoonsgegevens worden verwerkt
- [ ] **Monitoring**: continue fairness-monitoring ingericht met duidelijke drempelwaarden en exit-criteria
- [ ] **Rapport**: IAMA-rapport opgesteld, goedgekeurd en gepubliceerd
- [ ] **Herhalingsschema**: datum voor volgende IAMA-evaluatie vastgesteld

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **dpia-assessment** | DPIA uitvoeren naast IAMA wanneer persoonsgegevens worden verwerkt |
| **algoritmekader** | AI Act risicoklassen, Algoritmeregister-publicatie, generatieve AI-richtlijnen |
| **avg-privacy** | AVG-grondslagen, Privacy by Design, verwerkingsregister voor het algoritme |
| **nora-architectuur** | BIO-beveiligingseisen voor de technische implementatie |

## Meer informatie

- [IAMA rapport (Rijksoverheid)](https://www.rijksoverheid.nl/documenten/rapporten/2021/02/25/impact-assessment-mensenrechten-en-algoritmen)
- [Algoritmekader](https://minbzk.github.io/Algoritmekader/) — verantwoord algoritmegebruik overheid
- [Algoritmeregister](https://algoritmes.overheid.nl/) — publicatieplicht algoritmen
- [AI-verordening](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) — EU AI Act
- [College voor de Rechten van de Mens](https://www.mensenrechten.nl/) — discriminatietoetsing
- [Toetsingskader algoritmen Algemene Rekenkamer](https://www.rekenkamer.nl/publicaties/rapporten/2021/01/26/aandacht-voor-algoritmes)
