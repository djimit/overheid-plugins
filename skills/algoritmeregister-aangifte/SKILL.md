---
name: algoritmeregister-aangifte
version: 1.0.0
description: >
  Procedure voor het aanmelden van algoritmen bij het Algoritmeregister.
  Wetsgrondslag, aangifte-procedure, vereiste informatie, update-procedure.
  Gebruik bij algoritme-aangifte of Algoritmeregister compliance.
triggers:
  keywords: [algoritmeregister, algoritme aangifte, algoritme registratie, register algoritmen, Wpg, Wet open overheid, algoritme publicatie]
tools: [Read, Glob, Grep, Bash]
---

# Algoritmeregister Aangifte

Procedure voor het aanmelden van algoritmen bij het Algoritmeregister van de Nederlandse overheid.

## Wanneer deze skill gebruiken

- Algoritme aanmelden bij Algoritmeregister
- Bestaande aangifte actualiseren
- Bepalen of algoritme aangifteplichtig is
- Informatie verzamelen voor aangifte

## Wetsgrondslag

- Wet open overheid (Woo): Artikel 2.1 - aangifteplicht algoritmen
- AI Act: Hoog-risico AI-systemen verplicht in EU-databank
- Algoritmekader: Richtlijnen voor verantwoord algoritme-gebruik

## Aangifteplicht

| Criterium | Aangifteplichtig? |
|-----------|------------------|
| Automatische besluitvorming | Ja |
| Ondersteuning met significante impact | Ja |
| Profielering | Ja |
| Risicoprofielering | Ja |
| Algoritme met lage impact | Nee (aanbevolen) |
| Intern zonder externe impact | Nee |

## Aangifte-Procedure

### Stap 1: Inventarisatie
Alle algoritmen in kaart: doel, data, besluitvormingsimpact, profilering.

### Stap 2: Informatie Verzamelen

| Veld | Beschrijving |
|------|-------------|
| Naam | Naam van het algoritme |
| Doel | Waarvoor wordt het gebruikt? |
| Werking | Hoe werkt het? |
| Data | Welke data wordt verwerkt? |
| Impact | Impact op burgers? |
| Toezicht | Menselijk toezeicht? |
| Contact | Contactpersoon |

### Stap 3: Aangifte Indienen
Via register.algoritmes.overheid.nl - Nieuwe aangifte - Vul velden - Documentatie - Dien in.

### Stap 4: Publicatie
Na goedkeuring: openbare beschrijving, doel, impact, contact.

## Update-Procedure

| Trigger | Actie |
|---------|-------|
| Wijziging doel | Update binnen 30 dagen |
| Wijziging data | Update binnen 30 dagen |
| Nieuwe risico's | Direct update |
| Beëindiging | Decommissineren |
| Jaarlijkse review | Periodieke actualisatie |

## Relatie met IAMA en FRIA

| Aspect | Algoritmeregister | IAMA | FRIA |
|--------|-------------------|------|------|
| Doel | Transparantie | Impact-assessment | Grondrechten-impact |
| Verplichting | Woo (NL) | Algoritmekader (NL) | AI Act (EU) |

## Gerelateerde skills

- algoritmekader: Algoritmekader
- iama-assessment: IAMA uitvoeren
- ai-governance: EU AI Act / FRIA
- avg-privacy: AVG compliance
- uitvoeringsorganisaties: UWV, Belasting

## Bronnen

- Algoritmeregister: register.algoritmes.overheid.nl
- Algoritmekader: algoritmekader.overheid.nl
- Wet open overheid: wetten.overheid.nl
