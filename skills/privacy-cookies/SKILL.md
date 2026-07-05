---
name: privacy-cookies
version: 1.0.0
description: >
  Privacybeleid en cookie-instellingen voor Nederlandse overheidswebsites.
  AVG-compliant privacybeleid, ePrivacy-conform cookiebeleid.
  Gebruik bij website-ontwikkeling voor de overheid.
triggers:
  keywords: [privacybeleid, cookiebeleid, cookies, toestemming, consent, ePrivacy, AVG website, cookiemelding]
tools: [Read, Glob, Grep, Bash]
---

# Privacy & Cookies

Privacybeleid en cookie-instellingen voor Nederlandse overheidswebsites. Conform AVG/GDPR en ePrivacy-richtlijn.

## Wanneer deze skill gebruiken

- Privacybeleid opstellen voor overheidswebsite
- Cookiebeleid implementeren
- Toestemmingsmechanismen (consent banner)
- DPIA voor cookies en tracking
- Logboek Dataverwerkingen voor cookies

## Privacybeleid Verplichte Elementen (Art. 13-14 AVG)

| Element | Beschrijving |
|---------|-------------|
| Verwerkingsverantwoordelijke | Naam, adres, contact |
| Contactgegevens FGP | Functionaris Gegevensbescherming |
| Doeleinden | Waarvoor gegevens worden verwerkt |
| Rechtmatigheid | Grondslag (artikel 6 AVG) |
| Ontvangers | Wie krijgt toegang |
| Bewaartermijnen | Hoe lang bewaard |
| Rechten | Inzage, correctie, verwijderen |

## Cookie Categorieen

| Categorie | Toestemming | Voorbeelden |
|-----------|-------------|-------------|
| Strikt noodzakelijk | Nee | CSRF, sessie, load balancer |
| Functioneel | Ja | Taalvoorkeur, login-status |
| Analytiek | Ja | Matomo (anoniem) |
| Marketing | Ja | Social media, advertenties |
| Tracking | Ja | Cross-site tracking |

## Consent Banner Vereisten

- Geen pre-checked boxen
- Even makkelijk weigeren als accepteren
- Categorien kunnen worden geselecteerd
- Instellingen altijd terug te vinden
- Geen dark patterns

## DPIA voor Cookies

Verplicht bij: systematische monitoring, bijzondere gegevens, cross-device tracking, profiling.

## Gerelateerde skills

- avg-privacy: AVG compliance
- dpia-assessment: DPIA uitvoeren
- logboek-dataverwerkingen: Logging
- digitoegankelijk: Toegankelijkheid
- veilig-bouwen: Secure development

## Bronnen

- AVG: autoriteitpersoonsgegevens.nl
- ePrivacy: ec.europa.eu
- Cookie-richtlijn: autoriteitpersoonsgegevens.nl/cookies
