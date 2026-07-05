# Skill Quality Gates

Documentatie over de kwaliteitseisen voor skills in de overheid-plugins marketplace.

## Overzicht

Elke skill in deze repository moet voldoen aan de quality gates hieronder.
Deze gates zorgen voor consistentie, vindbaarheid en bruikbaarheid van alle skills.

## Gate 1: Frontmatter Validatie

Elke `SKILL.md` moet geldig YAML frontmatter bevatten:

```yaml
---
name: skill-naam
version: semver
description: >
  Beschrijving van wat de skill doet en wanneer te gebruiken.
triggers:
  keywords:
    - keyword-1
    - keyword-2
tools:
  - Read
  - Glob
  - Grep
---
```

 Vereisten:
- `name`: lowercase, kebab-case
- `version`: semantic versioning (x.y.z)
- `description`: minimaal 20 tekens, bevat zowel WHAT als WHEN
- `keywords`: minimaal 5 trigger-keywords
- `tools`: lijst van benodigde tools

## Gate 2: Cross-References

Elke skill moet een "Gerelateerde skills" sectie bevatten met minimaal 2
cross-references naar andere skills in de repository.

## Gate 3: NORA Mapping

Elke skill moet duidelijk maken welke NORA principes het implementeert of ondersteunt.

## Gate 4: Bronverwijzingen

Elke skill moet wettelijke bronverwijzingen bevatten:
- `wetten.overheid.nl` voor Nederlandse wetgeving
- `eur-lex.europa.eu` voor EU-verordeningen
- Bij voorkeur met artikel-nummer en versie-datum

## Gate 5: Test Scenarios

Elke skill moet minimaal bevatten:
- Happy path scenario (succesvol gebruik)
- Edge case scenario (grensgeval)
- Error scenario (foutafhandeling)

## Gate 6: Jurist-Acceptatie (juridische skills)

Skills die juridische content bevatten moeten een acceptatie-sectie hebben:
- Naam van de jurist
- Datum van acceptatie
- Geldigheidsperiode
- Versie van de skill

## Gate 7: Trigger Coverage

Elke skill moet minimaal 5 trigger-keywords hebben die relevant zijn
voor zoekopdrachten in de Claude Code interface.

## Gate 8: Tool Minimality

Skills moeten alleen tools vermelden die daadwerkelijk nodig zijn.
Geen onnodige tools (principle of least privilege).

## Automatische Validatie

De CI workflow (`validate.yml`) controleert:
- Frontmatter syntax
- Verplichte velden
- Cross-references
- Trigger coverage
- Bestandsstructuur

## Handmatige Review

Naast automatische gates:
- Peer review door minimaal 1 andere developer
- Jurist review bij juridische content
- Architect review bij architectuur-wijzigingen
