---
name: algoritmekader
description: >-
  Helpt bij het verantwoord ontwikkelen en inzetten van algoritmen en AI-systemen
  conform het Nederlandse Algoritmekader, de AI-verordening (AI Act), het IAMA
  (Impact Assessment Mensenrechten en Algoritmen) en het Algoritmeregister.
  Biedt richtlijnen voor risicoklassificatie, transparantie, non-discriminatie,
  menselijke controle en verantwoording. Gebruik deze skill wanneer de gebruiker
  vraagt over 'algoritmekader', 'algoritme overheid', 'AI overheid',
  'AI Act overheid', 'AI-verordening', 'IAMA', 'impact assessment algoritmen',
  'impact assessment mensenrechten', 'algoritmeregister', 'algorithm register',
  'algorithm framework', 'responsible AI', 'verantwoord algoritmegebruik',
  'transparantie algoritmen', 'bias algoritmen', 'discriminatie algoritmen',
  'non-discriminatie AI', 'eerlijke algoritmen', 'fair algorithms',
  'hoog-risico AI', 'high-risk AI', 'AI-risicoklasse', 'AI risk classification',
  'conformiteitsbeoordeling AI', 'AI conformity assessment',
  'menselijke controle AI', 'human oversight AI', 'uitlegbaarheid AI',
  'explainability AI', 'AI-transparantie', 'AI governance overheid',
  'algoritme-audit', 'algorithm audit', 'AI-toezicht', 'AI supervision',
  'foundation model', 'generatieve AI overheid', 'generative AI government',
  'verboden AI-praktijken', 'prohibited AI practices',
  of wanneer de gebruiker een algoritme of AI-systeem wil laten voldoen
  aan het Algoritmekader, de AI Act of andere Nederlandse vereisten voor
  verantwoord algoritmegebruik.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# Algoritmekader & AI-verordening

Toets algoritmen en AI-systemen aan het Nederlandse Algoritmekader en de EU AI-verordening. Het Algoritmekader is het centrale kader van de Nederlandse overheid voor verantwoord gebruik van algoritmen en AI-systemen.

Bron: [Algoritmekader](https://minbzk.github.io/Algoritmekader/) | [GitHub — MinBZK/Algoritmekader](https://github.com/MinBZK/Algoritmekader) | [Algoritmeregister](https://algoritmes.overheid.nl)

## AI-verordening (AI Act) — risicoklassificatie

De EU AI-verordening (2024/1689) is sinds augustus 2024 van kracht en wordt gefaseerd van toepassing.

### Risiconiveaus

| Niveau | Beschrijving | Voorbeeld | Vereisten |
|--------|-------------|-----------|-----------|
| **Onaanvaardbaar risico** | Verboden AI-praktijken | Social scoring, realtime biometrie in openbare ruimte (uitzonderingen), manipulatie van kwetsbare groepen | **Verboden** sinds februari 2025 |
| **Hoog risico** | AI in kritieke sectoren (Bijlage III) | Biometrie, onderwijs, werkgelegenheid, essentiële diensten, rechtshandhaving, migratie, rechtspraak | Conformiteitsbeoordeling, risicobeheer, datakwaliteit, transparantie, menselijk toezicht, nauwkeurigheid, robuustheid, cybersecurity |
| **Beperkt risico** | Transparantieverplichtingen | Chatbots, deepfakes, emotieherkenning | Informatieplicht: gebruiker moet weten dat ze met AI interacteren |
| **Minimaal risico** | Geen aanvullende eisen | Spamfilters, AI in games | Vrijwillige gedragscodes |

### Tijdlijn AI Act

| Datum | Verplichting |
|-------|-------------|
| Februari 2025 | Verboden AI-praktijken van toepassing |
| Augustus 2025 | Regels voor AI-modellen voor algemene doeleinden (GPAI/foundation models) |
| Augustus 2026 | Alle verplichtingen voor hoog-risico AI-systemen |

### Hoog-risico AI bij de overheid

Veel overheidstoepassingen vallen in de categorie **hoog risico** (Bijlage III):

- Toegang tot essentiële publieke diensten en uitkeringen
- Beoordeling van aanvragen (vergunningen, subsidies, toeslagen)
- Rechtshandhaving en migratiebeslissingen
- Onderwijs (toelating, beoordeling)
- Werkgelegenheid (werving, evaluatie)

**Verplichtingen voor hoog-risico AI-systemen:**

1. Risicobeheersysteem gedurende gehele levenscyclus
2. Data governance: training-, validatie- en testdata van hoge kwaliteit
3. Technische documentatie en logregistratie
4. Transparantie en informatie aan gebruikers
5. Menselijk toezicht (human-in-the-loop of human-on-the-loop)
6. Nauwkeurigheid, robuustheid en cybersecurity
7. Conformiteitsbeoordeling vóór ingebruikname

## Algoritmekader — kernvereisten

Het Algoritmekader vertaalt wet- en regelgeving naar praktische richtlijnen voor overheidsorganisaties. Het kader is georganiseerd rond zes thema's:

### 1. Governance

| Vereiste | Toelichting |
|----------|-------------|
| Eindverantwoordelijkheid | Bestuur is verantwoordelijk voor inzet van algoritmen |
| Beleidskader | Organisatiebeleid voor algoritmegebruik vaststellen |
| Rollen en verantwoordelijkheden | Duidelijke rolverdeling (opdrachtgever, ontwikkelaar, beheerder, toezichthouder) |
| Risicoanalyse | Classificeer algoritmen op risico voorafgaand aan ontwikkeling |

### 2. Transparantie

| Vereiste | Toelichting |
|----------|-------------|
| Algoritmeregister | Alle impactvolle algoritmen publiceren in het Algoritmeregister |
| Uitlegbaarheid | Besluiten die met algoritmen zijn genomen moeten uitlegbaar zijn voor betrokkenen |
| Broncode | Broncode van algoritmen waar mogelijk als open source publiceren |
| Communicatie | Actief communiceren over gebruik van algoritmen |

### 3. Non-discriminatie en eerlijkheid

| Vereiste | Toelichting |
|----------|-------------|
| Bias-detectie | Test op directe en indirecte discriminatie op beschermde kenmerken |
| Representatieve data | Trainingsdata moet representatief zijn voor de doelpopulatie |
| Fairness-metriek | Kies en documenteer passende fairness-maatstaven |
| Periodieke monitoring | Blijvend monitoren op bias in productie |

### 4. Menselijke controle

| Vereiste | Toelichting |
|----------|-------------|
| Human-in-the-loop | Bij hoog-risico besluiten: mens neemt het besluit, algoritme adviseert |
| Human-on-the-loop | Bij lager risico: mens kan ingrijpen en corrigeren |
| Bezwaar en beroep | Betrokkenen moeten een algoritmisch besluit kunnen aanvechten bij een mens |
| Stopknop | Mogelijkheid om algoritme direct te stoppen bij ongewenste effecten |

### 5. Technische robuustheid en veiligheid

| Vereiste | Toelichting |
|----------|-------------|
| Validatie en testen | Uitgebreide test- en validatieprocedures vóór ingebruikname |
| Monitoring | Continue monitoring op prestatie, drift en onverwacht gedrag |
| Cybersecurity | Algoritmen beveiligen tegen adversarial attacks en data poisoning |
| Reproduceerbaarheid | Resultaten moeten reproduceerbaar zijn |

### 6. Privacy en gegevensbescherming

| Vereiste | Toelichting |
|----------|-------------|
| DPIA | Gegevensbeschermingseffectbeoordeling uitvoeren bij verwerking persoonsgegevens |
| Dataminimalisatie | Alleen strikt noodzakelijke gegevens gebruiken |
| Doelbinding | Data alleen gebruiken voor het doel waarvoor het is verzameld |
| Bewaartermijnen | Trainings- en inputdata verwijderen na afloop bewaartermijn |

## IAMA — Impact Assessment Mensenrechten en Algoritmen

Het IAMA is een verplicht instrument voor overheidsorganisaties om de impact van algoritmische systemen op mensenrechten en publieke waarden te beoordelen.

Bron: [IAMA handleiding (PDF)](https://www.rijksoverheid.nl/documenten/rapporten/2021/02/25/impact-assessment-mensenrechten-en-algoritmen) | [Utrecht University](https://www.uu.nl/organisatie/alumnirelaties/impact-assessment-mensenrechten-en-algoritmen-iama)

### Fasen van het IAMA

| Fase | Naam | Kernactiviteiten |
|------|------|-------------------|
| **1** | Voorbereiding | Projectbeschrijving, stakeholderidentificatie, samenstelling beoordelingsteam (multidisciplinair) |
| **1A** | Waarom | Doel en noodzaak van het algoritme; proportionaliteitstoets |
| **1B** | Wat | Type algoritme (regelgebaseerd, machine learning, deep learning), databronnen, verwachte output |
| **1C** | Hoe | Technische implementatie, integratie in besluitvormingsproces |
| **2** | Beoordeling fundamentele rechten | Toets aan EVRM/Grondwet: privacy, gelijkheid, non-discriminatie, effectief rechtsmiddel |
| **2A** | Recht op privacy | Noodzaak en proportionaliteit gegevensverwerking |
| **2B** | Non-discriminatie | Risico op (indirecte) discriminatie op beschermde gronden |
| **2C** | Autonomie | Impact op individuele keuzevrijheid |
| **3** | Beoordeling publieke waarden | Transparantie, uitlegbaarheid, verantwoording, menselijke controle |
| **3A** | Transparantie en uitlegbaarheid | Hoe wordt het algoritme uitgelegd aan betrokkenen? |
| **3B** | Verantwoording | Wie is verantwoordelijk voor besluiten? |

### Wanneer is een IAMA verplicht?

- Bij de **ontwikkeling** van nieuwe algoritmen of AI-systemen
- Bij **significante wijzigingen** aan bestaande systemen
- Bij **hergebruik** van algoritmen in een andere context
- Aanbevolen: periodieke **herijking** van bestaande IAMA's

## Algoritmeregister

Het Algoritmeregister is het publieke register waarin overheidsorganisaties hun algoritmen publiceren.

Bron: [algoritmes.overheid.nl](https://algoritmes.overheid.nl) | [API-documentatie](https://algoritmes.overheid.nl/api/docs)

### Verplichte registratievelden

| Veld | Beschrijving |
|------|-------------|
| `name` | Naam van het algoritme |
| `organization` | Verantwoordelijke organisatie |
| `department` | Verantwoordelijke afdeling |
| `description_short` | Korte beschrijving (max 150 tekens) |
| `type` | Type: regelgebaseerd, machine learning, of deep learning |
| `category` | Beleidsterrein (bijv. werk, zorg, veiligheid) |
| `status` | In ontwikkeling, in gebruik, buiten gebruik |
| `goal` | Doel en beoogd effect |
| `impact` | Impact op burgers en samenleving |
| `proportionality` | Motivering noodzaak en proportionaliteit |
| `legal_base` | Wettelijke grondslag |
| `human_intervention` | Beschrijving menselijke controle |

### Optionele registratievelden

| Veld | Beschrijving |
|------|-------------|
| `source_data` | Gebruikte databronnen |
| `methods_and_models` | Gebruikte methoden en modellen |
| `monitoring` | Monitoring- en evaluatieprocedures |
| `risks` | Geïdentificeerde risico's en mitigatie |
| `performance_standard` | Prestatienormen en -metrieken |
| `competent_authority` | Toezichthoudende autoriteit |
| `url` | Link naar meer informatie |
| `contact_email` | Contactgegevens |
| `publication_date` | Publicatiedatum |
| `revision_date` | Laatste revisiedatum |

### API-gebruik

```bash
# Alle algoritmen ophalen
GET https://algoritmes.overheid.nl/api/v1/algorithms

# Zoeken op organisatie
GET https://algoritmes.overheid.nl/api/v1/algorithms?organisation=gemeente-amsterdam

# Specifiek algoritme ophalen
GET https://algoritmes.overheid.nl/api/v1/algorithms/{id}
```

## Implementatie-checklist voor ontwikkelaars

Bij het bouwen van algoritmen of AI-systemen voor de overheid, controleer minimaal:

- [ ] **Risicoklasse bepaald**: is dit een hoog-risico AI-systeem onder de AI Act? (Bijlage III)
- [ ] **IAMA uitgevoerd**: multidisciplinair, met aandacht voor mensenrechten en publieke waarden
- [ ] **DPIA uitgevoerd**: als persoonsgegevens worden verwerkt (AVG art. 35)
- [ ] **Bias getest**: op directe en indirecte discriminatie op beschermde kenmerken
- [ ] **Uitlegbaarheid geborgd**: besluiten zijn uitlegbaar voor betrokkenen
- [ ] **Menselijke controle**: human-in-the-loop bij hoog-risico besluiten
- [ ] **Bezwaarmogelijkheid**: betrokkenen kunnen bij een mens in bezwaar
- [ ] **Monitoring ingericht**: continue monitoring op prestatie, bias-drift en ongewenste effecten
- [ ] **Algoritmeregister**: publicatie in algoritmes.overheid.nl
- [ ] **Broncode open**: code gepubliceerd als open source (tenzij zwaarwegende redenen)
- [ ] **Technische documentatie**: systeembeschrijving, databronnen, modelkeuzes, testresultaten
- [ ] **Validatie**: uitgebreide test- en validatieresultaten gedocumenteerd
- [ ] **Cybersecurity**: bescherming tegen adversarial attacks en data poisoning
- [ ] **Data governance**: kwaliteit, representativiteit en herkomst van trainingsdata geborgd
- [ ] **Bewaartermijnen**: trainingsdata en logdata conform AVG-bewaartermijnen

## Generatieve AI bij de overheid

Het Algoritmekader bevat specifieke richtlijnen voor generatieve AI (foundation models, LLM's):

| Aspect | Richtlijn |
|--------|-----------|
| **Transparantie** | Vermeld altijd dat output door AI is gegenereerd |
| **Factualiteit** | Controleer AI-output op feitelijke juistheid (hallucinaties) |
| **Persoonsgegevens** | Geen persoonsgegevens in prompts zonder DPIA en grondslag |
| **Vertrouwelijkheid** | Geen vertrouwelijke informatie in externe AI-diensten |
| **Publieke waarden** | Generatieve AI niet inzetten voor geautomatiseerde besluiten |
| **Inkoop** | Generatieve AI-diensten beoordelen op privacy, security en vendor lock-in |

## Beslisboom: welke vereisten gelden?

```
Is het een algoritme dat invloed heeft op burgers of processen?
├── Nee → Geen aanvullende vereisten (maar documenteer wel)
└── Ja → Registreer in Algoritmeregister
    ├── Worden persoonsgegevens verwerkt?
    │   └── Ja → Voer DPIA uit (AVG art. 35)
    ├── Voer IAMA uit
    └── Is het een AI-systeem onder de AI Act?
        ├── Nee (regelgebaseerd) → Volg Algoritmekader-richtlijnen
        └── Ja → Bepaal risicoklasse
            ├── Onaanvaardbaar → VERBODEN
            ├── Hoog risico (Bijlage III) → Conformiteitsbeoordeling + alle verplichtingen
            ├── Beperkt risico → Transparantieverplichtingen
            └── Minimaal risico → Vrijwillige gedragscodes
```

## Meer informatie

- [Algoritmekader](https://minbzk.github.io/Algoritmekader/) | [GitHub](https://github.com/MinBZK/Algoritmekader)
- [Algoritmeregister](https://algoritmes.overheid.nl) | [API-docs](https://algoritmes.overheid.nl/api/docs)
- [IAMA handleiding](https://www.rijksoverheid.nl/documenten/rapporten/2021/02/25/impact-assessment-mensenrechten-en-algoritmen)
- [AI-verordening (EU 2024/1689)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
- [Toetsingskader algoritmes Algemene Rekenkamer](https://www.rekenkamer.nl/onderwerpen/algoritmes)
