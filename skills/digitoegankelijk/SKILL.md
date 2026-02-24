---
name: digitoegankelijk
description: >-
  Helpt bij het bouwen van digitaal toegankelijke websites, applicaties en
  documenten conform WCAG 2.1/2.2, EN 301 549, het Besluit digitale
  toegankelijkheid overheid en de European Accessibility Act (EAA).
  Biedt richtlijnen, codevoorbeelden en testprocedures voor toegankelijk
  ontwerpen en ontwikkelen. Gebruik deze skill wanneer de gebruiker vraagt
  over 'WCAG', 'toegankelijkheid', 'accessibility', 'a11y',
  'digitoegankelijk', 'digitale toegankelijkheid', 'digital accessibility',
  'EN 301 549', 'European Accessibility Act', 'EAA',
  'Besluit digitale toegankelijkheid', 'toegankelijkheidsverklaring',
  'accessibility statement', 'screenreader', 'schermlezer',
  'ARIA', 'WAI-ARIA', 'alt-tekst', 'alt text', 'toetsenbordtoegankelijkheid',
  'keyboard accessibility', 'kleurcontrast', 'color contrast',
  'focus indicator', 'skip link', 'semantic HTML', 'semantische HTML',
  'toegankelijke formulieren', 'accessible forms', 'WCAG 2.1', 'WCAG 2.2',
  'WCAG A', 'WCAG AA', 'WCAG AAA', 'accessibility audit',
  'toegankelijkheidsaudit', 'toegankelijkheidstoets',
  'BITV', 'Section 508', 'inclusief ontwerp', 'inclusive design',
  'universeel ontwerp', 'universal design', 'cognitieve toegankelijkheid',
  of wanneer de gebruiker een website, app of document toegankelijk wil
  maken conform de Nederlandse en Europese vereisten.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(npm *)
  - Bash(npx *)
---

# DigiToegankelijk — WCAG 2.1/2.2 & EN 301 549

Bouw digitaal toegankelijke overheidswebsites en -applicaties conform wettelijke vereisten. Digitale toegankelijkheid is **wettelijk verplicht** voor alle Nederlandse overheidsorganisaties.

Bron: [DigiToegankelijk.nl](https://www.digitoegankelijk.nl/) | [WCAG 2.1 (W3C)](https://www.w3.org/TR/WCAG21/) | [WCAG 2.2 (W3C)](https://www.w3.org/TR/WCAG22/) | [EN 301 549](https://www.etsi.org/deliver/etsi_en/301500_301599/301549/03.02.01_60/en_301549v030201p.pdf)

## Wettelijk kader

| Aspect | Detail |
|--------|--------|
| **Wet** | Besluit digitale toegankelijkheid overheid (onder Wet digitale overheid) |
| **Standaard** | EN 301 549 v3.2.1 (bevat WCAG 2.1 level AA als kern) |
| **Scope** | Websites, mobiele apps, intranets, extranets, SaaS-applicaties van overheidsorganisaties |
| **WCAG 2.2** | Nog **niet** wettelijk verplicht; wel aanbevolen voor nieuwe projecten |
| **EAA** | European Accessibility Act: sinds 28 juni 2025 ook private e-commerce en diensten |
| **Beheerder** | Logius; beleid door Ministerie van BZK |

### Complianceniveaus

| Status | Betekenis | Wettelijk compliant? |
|--------|-----------|---------------------|
| **A** | Alle 50 succescriteria voldaan + verklaring gepubliceerd | Ja |
| **B** | Gedeeltelijke compliance + verklaring met verbeterplan | Ja |
| **C** | Verklaring gepubliceerd + audit gepland binnen 6 maanden | Ja |
| **Geen** | Geen verklaring of geen compliance-inspanning | **Nee** |

### Verplichtingen

- **Toegankelijkheidsverklaring** publiceren (jaarlijks bijwerken)
- **Audit** elke 36 maanden door een onafhankelijke partij
- **Feedbackmechanisme** voor gebruikers om toegankelijkheidsproblemen te melden
- **Disproportionele last** mag alleen als uitzondering met onderbouwing

## WCAG 2.1 — succescriteria (Level A en AA)

### Principe 1: Waarneembaar (Perceivable)

| Criterium | Niveau | Vereiste |
|-----------|--------|----------|
| **1.1.1** Niet-tekstuele content | A | Alle afbeeldingen, iconen, grafieken hebben een tekstalternatief |
| **1.2.1** Alleen audio/video | A | Transcriptie voor audio; audiobeschrijving of transcriptie voor video |
| **1.2.2** Ondertiteling (vooraf opgenomen) | A | Ondertiteling bij alle vooraf opgenomen video met geluid |
| **1.2.3** Audiobeschrijving (vooraf opgenomen) | A | Audiobeschrijving of volledige transcriptie bij video |
| **1.2.4** Ondertiteling (live) | AA | Live ondertiteling bij live audiovisuele content |
| **1.2.5** Audiobeschrijving (vooraf opgenomen) | AA | Audiobeschrijving bij alle vooraf opgenomen video |
| **1.3.1** Info en relaties | A | Structuur en relaties zijn programmatisch bepaalbaar (koppen, lijsten, tabellen, formulierlabels) |
| **1.3.2** Betekenisvolle volgorde | A | Leervolgorde van content is programmatisch bepaalbaar |
| **1.3.3** Zintuiglijke kenmerken | A | Instructies niet alleen op kleur, vorm, grootte of locatie |
| **1.3.4** Oriëntatie | AA | Content niet beperkt tot één schermoriëntatie |
| **1.3.5** Identificeer invoerdoel | AA | Formuliervelden met autocomplete-attributen waar van toepassing |
| **1.4.1** Gebruik van kleur | A | Kleur niet als enige manier om informatie over te brengen |
| **1.4.2** Geluidsbediening | A | Mechanisme om geluid dat automatisch afspeelt te pauzeren/stoppen |
| **1.4.3** Contrast (minimum) | AA | Tekst: minimaal **4.5:1** contrastverhouding; grote tekst: **3:1** |
| **1.4.4** Herschalen tekst | AA | Tekst schaalbaar tot 200% zonder verlies van functionaliteit |
| **1.4.5** Afbeeldingen van tekst | AA | Gebruik echte tekst, geen afbeeldingen van tekst |
| **1.4.10** Reflow | AA | Content bruikbaar bij 320px breed (geen horizontaal scrollen) |
| **1.4.11** Contrast niet-tekstueel | AA | UI-componenten en grafische elementen: minimaal **3:1** contrast |
| **1.4.12** Tekstafstand | AA | Content bruikbaar bij aangepaste regelafstand, woordafstand, letterafstand |
| **1.4.13** Content bij hover/focus | AA | Extra content bij hover/focus: sluiten, hoveren, persistent |

### Principe 2: Bedienbaar (Operable)

| Criterium | Niveau | Vereiste |
|-----------|--------|----------|
| **2.1.1** Toetsenbord | A | Alle functionaliteit bedienbaar met toetsenbord |
| **2.1.2** Geen toetsenbordval | A | Focus kan altijd wegbewegen van een component |
| **2.1.4** Tekensneltoetsen | A | Enkeltekensneltoetsen uitschakelbaar of aanpasbaar |
| **2.2.1** Timing aanpasbaar | A | Tijdslimieten uitschakelbaar, aanpasbaar of verlengbaar |
| **2.2.2** Pauzeren, stoppen, verbergen | A | Bewegende/knipperende content pauzeerbaar |
| **2.3.1** Drie flitsen of onder drempel | A | Geen content die meer dan 3x per seconde flitst |
| **2.4.1** Blokken omzeilen | A | Skip-links of navigatiemechanisme om herhalende blokken over te slaan |
| **2.4.2** Paginatitel | A | Pagina's hebben beschrijvende titels |
| **2.4.3** Focusvolgorde | A | Logische focusvolgorde bij toetsenbordnavigatie |
| **2.4.4** Linkdoel (in context) | A | Doel van elke link is duidelijk uit de linktekst of context |
| **2.4.5** Meerdere manieren | AA | Meerdere manieren om pagina's te bereiken (menu, zoeken, sitemap) |
| **2.4.6** Koppen en labels | AA | Koppen en labels beschrijven het onderwerp of doel |
| **2.4.7** Focus zichtbaar | AA | Toetsenbordfocus is visueel zichtbaar |

### Principe 3: Begrijpelijk (Understandable)

| Criterium | Niveau | Vereiste |
|-----------|--------|----------|
| **3.1.1** Taal van de pagina | A | `lang`-attribuut op `<html>` element |
| **3.1.2** Taal van onderdelen | AA | `lang`-attribuut bij content in een andere taal |
| **3.2.1** Bij focus | A | Geen onverwachte contextverandering bij focus |
| **3.2.2** Bij invoer | A | Geen onverwachte contextverandering bij invoer |
| **3.2.3** Consistente navigatie | AA | Navigatie is consistent op alle pagina's |
| **3.2.4** Consistente identificatie | AA | Componenten met dezelfde functie zijn consistent benoemd |
| **3.3.1** Foutidentificatie | A | Fouten worden duidelijk beschreven in tekst |
| **3.3.2** Labels of instructies | A | Formuliervelden hebben labels of instructies |
| **3.3.3** Foutsuggestie | AA | Suggesties voor foutcorrectie waar mogelijk |
| **3.3.4** Foutpreventie (juridisch, financieel) | AA | Reversibel, controleerbaar of bevestigbaar bij juridische/financiële transacties |

### Principe 4: Robuust (Robust)

| Criterium | Niveau | Vereiste |
|-----------|--------|----------|
| **4.1.2** Naam, rol, waarde | A | Alle UI-componenten hebben programmatisch bepaalbare naam, rol en waarde |
| **4.1.3** Statusberichten | AA | Statusberichten zijn programmatisch bepaalbaar zonder focus te verplaatsen |

## WCAG 2.2 — nieuwe succescriteria (aanbevolen)

| Criterium | Niveau | Vereiste |
|-----------|--------|----------|
| **2.4.11** Focus niet verborgen | AA | Gefocust element is niet volledig verborgen |
| **2.4.12** Focus niet bedekt | AAA | Gefocust element is niet gedeeltelijk bedekt |
| **2.4.13** Focusweergave | AAA | Focus-indicator voldoet aan minimumgrootte en contrast |
| **2.5.7** Sleepbewegingen | AA | Drag-and-drop ook bedienbaar met klik |
| **2.5.8** Doelgrootte (minimum) | AA | Klikbare elementen minimaal 24x24 CSS pixels |
| **3.2.6** Consistente hulp | A | Hulpfuncties staan op consistente locatie |
| **3.3.7** Overbodige invoer | A | Eerder ingevoerde informatie niet opnieuw vragen |
| **3.3.8** Toegankelijke authenticatie | AA | Geen cognitieve functietest vereist voor inloggen |

## Codepatronen voor toegankelijkheid

### Skip-link

```html
<body>
  <a href="#main-content" class="skip-link">Ga naar hoofdinhoud</a>
  <header><!-- navigatie --></header>
  <main id="main-content" tabindex="-1">
    <!-- hoofdinhoud -->
  </main>
</body>

<style>
.skip-link {
  position: absolute;
  top: -40px;
  left: 0;
  padding: 8px;
  background: #000;
  color: #fff;
  z-index: 100;
}
.skip-link:focus {
  top: 0;
}
</style>
```

### Toegankelijk formulier

```html
<form novalidate>
  <div class="form-group">
    <label for="email">E-mailadres <span aria-hidden="true">*</span></label>
    <input
      type="email"
      id="email"
      name="email"
      required
      autocomplete="email"
      aria-required="true"
      aria-describedby="email-help email-error"
    />
    <p id="email-help" class="hint">Bijv. naam@voorbeeld.nl</p>
    <p id="email-error" class="error" role="alert" hidden>
      Vul een geldig e-mailadres in
    </p>
  </div>
  <button type="submit">Verzenden</button>
</form>
```

### Toegankelijke tabel

```html
<table>
  <caption>Openingstijden gemeentehuis</caption>
  <thead>
    <tr>
      <th scope="col">Dag</th>
      <th scope="col">Openingstijd</th>
      <th scope="col">Sluitingstijd</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Maandag</th>
      <td>09:00</td>
      <td>17:00</td>
    </tr>
  </tbody>
</table>
```

### Statusbericht (WCAG 4.1.3)

```html
<!-- Gebruik role="status" voor niet-urgente meldingen -->
<div role="status" aria-live="polite">
  3 zoekresultaten gevonden
</div>

<!-- Gebruik role="alert" voor urgente foutmeldingen -->
<div role="alert" aria-live="assertive">
  Er is een fout opgetreden bij het opslaan
</div>
```

### Focus management bij SPA-navigatie

```javascript
// Na routewijziging in SPA: verplaats focus naar hoofdinhoud
function onRouteChange() {
  const main = document.getElementById('main-content');
  main.setAttribute('tabindex', '-1');
  main.focus();
  document.title = `${pageTitle} | MijnOverheid`;
}
```

## Testtools

| Tool | Type | Beschrijving |
|------|------|-------------|
| **axe-core** | Geautomatiseerd | Open-source accessibility engine; integreert in CI/CD |
| **Lighthouse** | Geautomatiseerd | Chrome DevTools accessibility audit |
| **WAVE** | Geautomatiseerd | Web accessibility evaluation tool (browser extensie) |
| **Pa11y** | Geautomatiseerd | CLI-tool voor CI/CD-integratie |
| **NVDA** | Schermlezer | Gratis schermlezer voor Windows |
| **VoiceOver** | Schermlezer | Ingebouwd in macOS/iOS |
| **TalkBack** | Schermlezer | Ingebouwd in Android |
| **Colour Contrast Analyser** | Handmatig | Contrastverhouding meten |

### Geautomatiseerd testen in CI/CD

```bash
# axe-core via CLI
npx @axe-core/cli https://mijn-website.nl

# Pa11y
npx pa11y https://mijn-website.nl --standard WCAG2AA

# Lighthouse CI
npx lhci autorun --collect.url=https://mijn-website.nl
```

## Implementatie-checklist

- [ ] **HTML-structuur**: semantische elementen (`header`, `nav`, `main`, `footer`, `section`, `article`)
- [ ] **Koppen**: correcte hiërarchie (h1 → h2 → h3), geen niveaus overslaan
- [ ] **Afbeeldingen**: alt-tekst voor informatieve afbeeldingen; `alt=""` voor decoratieve
- [ ] **Formulieren**: labels gekoppeld aan invoervelden; foutmeldingen duidelijk en beschrijvend
- [ ] **Toetsenbord**: alle interactieve elementen bereikbaar en bedienbaar met toetsenbord
- [ ] **Focus**: zichtbare focus-indicator; logische focusvolgorde
- [ ] **Contrast**: tekst ≥4.5:1; grote tekst ≥3:1; UI-componenten ≥3:1
- [ ] **Taal**: `lang="nl"` op `<html>`; `lang`-attribuut bij anderstalige content
- [ ] **Skip-link**: "Ga naar hoofdinhoud" link als eerste focusbaar element
- [ ] **Responsive**: content bruikbaar bij 320px breed (reflow) en 200% zoom
- [ ] **Statusberichten**: `role="status"` of `role="alert"` voor dynamische berichten
- [ ] **Toegankelijkheidsverklaring**: gepubliceerd en jaarlijks bijgewerkt
- [ ] **Geautomatiseerde tests**: axe-core of Pa11y in CI/CD-pipeline

## Meer informatie

- [DigiToegankelijk.nl](https://www.digitoegankelijk.nl/) | [Wat is verplicht?](https://www.digitoegankelijk.nl/wetgeving/wat-is-verplicht)
- [WCAG 2.1 (W3C)](https://www.w3.org/TR/WCAG21/) | [WCAG 2.2 (W3C)](https://www.w3.org/TR/WCAG22/)
- [EN 301 549 v3.2.1](https://www.etsi.org/deliver/etsi_en/301500_301599/301549/03.02.01_60/en_301549v030201p.pdf)
- [NL Design System](https://nldesignsystem.nl/) — herbruikbare, toegankelijke componenten
- [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/)
