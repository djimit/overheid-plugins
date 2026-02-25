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

## EN 301 549 — aanvullende eisen bovenop WCAG

EN 301 549 v3.2.1 is de geharmoniseerde Europese standaard. Naast WCAG 2.1 AA (Clause 9) stelt het aanvullende eisen:

| Clause | Scope | Aanvulling op WCAG |
|--------|-------|-------------------|
| **5** | Generieke eisen | Gesloten functionaliteit, biometrie-alternatieven, behoud toegankelijkheidsinformatie |
| **6** | Tweewegcommunicatie | Real-time tekst (RTT), breedte voor gebarentaalvideo |
| **7** | Video | Ondertiteling: synchronisatie, positionering, aanpasbaarheid |
| **9** | Webcontent | WCAG 2.1 AA volledig opgenomen |
| **10** | Niet-webdocumenten | PDF's, Word, spreadsheets moeten WCAG-equivalent voldoen |
| **11** | Niet-websoftware | Native/mobiele apps voldoen aan WCAG via WCAG2ICT-mapping |
| **11.8** | Authoring tools | Software voor contentcreatie moet toegankelijke output ondersteunen |
| **12** | Documentatie en support | Productdocumentatie zelf ook toegankelijk; helpdesk accommodeert |

## European Accessibility Act (EAA) — tijdlijn

| Datum | Mijlpaal |
|-------|----------|
| Juni 2019 | EAA aangenomen (Richtlijn 2019/882) |
| Juni 2022 | Omzettingsdeadline: nationale wetgeving in alle 27 lidstaten |
| **Juni 2025** | **Handhaving actief** |
| Juni 2030 | Overgangsperiode bestaande dienstcontracten eindigt |

**Scope**: publieke én private sector. E-commerce, bankdiensten, telecom, vervoer, e-books. Micro-ondernemingen (<10 werknemers én <€2M omzet) zijn uitgezonderd voor diensten.

**Boetes Nederland**: tot **€90.000**; toezichthouder kan diensten opschorten.

## Codepatronen voor toegankelijkheid

### Paginastructuur met landmarks

```html
<!DOCTYPE html>
<html lang="nl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Paginatitel - Organisatie | Rijksoverheid</title>
</head>
<body>
  <a href="#main-content" class="skip-link">Ga naar hoofdinhoud</a>

  <header>
    <nav aria-label="Hoofdnavigatie">
      <ul>
        <li><a href="/" aria-current="page">Home</a></li>
        <li><a href="/onderwerpen">Onderwerpen</a></li>
        <li><a href="/contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main id="main-content">
    <h1>Paginatitel</h1>
    <section aria-labelledby="section-heading">
      <h2 id="section-heading">Sectietitel</h2>
      <p>Inhoud...</p>
    </section>
  </main>

  <aside aria-label="Gerelateerde informatie">
    <!-- Aanvullende content -->
  </aside>

  <footer>
    <nav aria-label="Footernavigatie">
      <!-- Footer links -->
    </nav>
  </footer>
</body>
</html>
```

### CSS: skip-link, focus, doelgrootte, sr-only

```css
/* Verborgen voor visueel, zichtbaar voor schermlezers */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

/* Skip-link: zichtbaar bij focus */
.skip-link {
  position: absolute;
  top: -100%;
  left: 0;
  z-index: 1000;
  padding: 0.5rem 1rem;
  background: #000;
  color: #fff;
}
.skip-link:focus { top: 0; }

/* Zichtbare focus-indicator (2.4.7 + 2.4.11) */
:focus-visible {
  outline: 3px solid #000;
  outline-offset: 2px;
}

/* Minimale doelgrootte (2.5.8): 24x24 CSS px */
button, a, input, select, textarea {
  min-height: 24px;
  min-width: 24px;
}

/* Reflow (1.4.10): geen horizontaal scrollen bij 320px */
@media (max-width: 320px) {
  .container { width: 100%; }
}
```

### Toegankelijk formulier met foutafhandeling

```html
<form novalidate>
  <!-- Foutsamenvatting bovenaan (bij meerdere fouten) -->
  <div role="alert" aria-labelledby="error-summary-heading" class="error-summary" hidden>
    <h2 id="error-summary-heading">Er zijn fouten gevonden</h2>
    <ul>
      <li><a href="#postcode">Vul een geldige postcode in</a></li>
    </ul>
  </div>

  <!-- Verplicht veld met hint -->
  <div class="form-group">
    <label for="email">
      E-mailadres <span aria-hidden="true">*</span>
      <span class="sr-only">(verplicht)</span>
    </label>
    <input
      type="email"
      id="email"
      name="email"
      required
      autocomplete="email"
      aria-required="true"
      aria-describedby="email-hint"
    />
    <p id="email-hint" class="hint">Bijvoorbeeld: naam@voorbeeld.nl</p>
  </div>

  <!-- Veld met validatiefout -->
  <div class="form-group form-group--error">
    <label for="postcode">Postcode <span aria-hidden="true">*</span></label>
    <p id="postcode-error" class="error-message" role="alert">
      <span class="sr-only">Fout:</span>
      Vul een geldige postcode in (bijvoorbeeld 1234 AB)
    </p>
    <input
      type="text"
      id="postcode"
      name="postcode"
      required
      autocomplete="postal-code"
      aria-required="true"
      aria-invalid="true"
      aria-describedby="postcode-error"
      pattern="[0-9]{4}\s?[a-zA-Z]{2}"
    />
  </div>

  <button type="submit">Verzenden</button>
</form>
```

### Toegankelijke authenticatie (WCAG 2.2 — 3.3.8)

```html
<!-- Sta plakken toe in wachtwoordvelden -->
<label for="password">Wachtwoord</label>
<input type="password" id="password" name="password" autocomplete="current-password" />
<!-- NOOIT: oncopy="return false" of onpaste="return false" -->
<!-- NOOIT: CSS user-select: none op authenticatievelden -->

<!-- Verificatiecode: sta plakken toe -->
<label for="code">Verificatiecode</label>
<input type="text" id="code" name="code" autocomplete="one-time-code" inputmode="numeric" />
```

### Taalattributen (cruciaal voor overheidswebsites)

```html
<html lang="nl">
<!-- Anderstalige fragmenten -->
<p>Dit formulier is ook beschikbaar in het
  <a href="/en/form" lang="en" hreflang="en">English</a>.
</p>
<!-- Fries -->
<p lang="fy">Wolkom by de provinsje Fryslân.</p>
```

### Live regions voor dynamische content

```html
<!-- Container MOET bestaan in DOM bij pageload (leeg) -->
<!-- Niet-urgent (zoekresultaten, opslaan bevestigd) -->
<div role="status" aria-live="polite" aria-atomic="true"></div>

<!-- Urgent (fouten, sessie-timeout) -->
<div role="alert" aria-live="assertive" aria-atomic="true"></div>
```

Regels: container bestaat bij pageload; `aria-atomic="true"` nodig voor VoiceOver iOS; `role="status"` = polite, `role="alert"` = assertive.

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

### Focus management bij SPA-navigatie

```javascript
function onRouteChange() {
  const main = document.getElementById('main-content');
  main.setAttribute('tabindex', '-1');
  main.focus();
  document.title = `${pageTitle} | MijnOverheid`;
}
```

## Testtools en CI/CD-integratie

| Tool | Type | Sterkte | Integratie |
|------|------|---------|-----------|
| **axe-core** | Engine | Hoogste nauwkeurigheid (~57%), geen false positives | npm, Cypress, Playwright, Jest |
| **axe DevTools** | Browser extensie | 400K+ gebruikers, mobiel testen | Chrome, Firefox, Edge |
| **Pa11y** | CLI | Dual engine (axe + HTML CodeSniffer), CI/CD-vriendelijk | CLI, GitHub Actions, GitLab CI |
| **Lighthouse** | Ingebouwd (Chrome) | Gebruikt axe-core subset | Chrome DevTools, CLI, CI |
| **WAVE** | Browser extensie | Visuele overlay van fouten | Chrome, Firefox |
| **NVDA** | Schermlezer | Gratis, Windows | Handmatig testen |
| **VoiceOver** | Schermlezer | Ingebouwd macOS/iOS | Handmatig testen |

### axe-core in Playwright

```javascript
import { test, expect } from '@playwright/test';
import AxeBuilder from '@axe-core/playwright';

test('pagina voldoet aan WCAG 2.1 AA', async ({ page }) => {
  await page.goto('/');
  const results = await new AxeBuilder({ page })
    .withTags(['wcag2a', 'wcag2aa', 'wcag21a', 'wcag21aa'])
    .analyze();
  expect(results.violations).toEqual([]);
});
```

### Pa11y in GitHub Actions

```yaml
name: Accessibility Tests
on: [push, pull_request]
jobs:
  a11y:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm ci
      - run: npm start &
      - run: npx wait-on http://localhost:3000
      - run: npx pa11y-ci --config .pa11yci.json
```

`.pa11yci.json`:
```json
{
  "defaults": {
    "standard": "WCAG2AA",
    "runners": ["axe", "htmlcs"],
    "timeout": 30000
  },
  "urls": [
    "http://localhost:3000/",
    "http://localhost:3000/formulier"
  ]
}
```

### Handmatige testchecklist (de overige 60-70%)

1. **Toetsenbordnavigatie**: Tab door alle interactieve elementen; controleer focusvolgorde en zichtbaarheid
2. **Schermlezer**: Test met NVDA (Windows, gratis) of VoiceOver (macOS/iOS)
3. **Zoom 200%**: Controleer dat geen content verloren gaat of overlapt
4. **Tekstafstand**: Pas 1.4.12 waarden toe (regelafstand 1.5x, alineaafstand 2x, letterafstand 0.12em, woordafstand 0.16em)
5. **Kleurcontrast**: DevTools of Colour Contrast Analyser voor niet-tekstelementen
6. **Koppenstructuur**: Logische hiërarchie (geen niveaus overslaan)
7. **Formulierfouten**: Dien leeg formulier in; controleer dat fouten worden voorgelezen en focusbaar zijn
8. **Mobiel**: Test op daadwerkelijke apparaten met TalkBack (Android)

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
