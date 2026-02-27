---
name: nl-design-system
description: >-
  Helpt bij het bouwen van overheidswebsites en -applicaties met het
  NL Design System, inclusief design tokens, community componenten,
  Storybook en Rijkshuisstijl. Biedt richtlijnen voor het implementeren
  van herbruikbare, toegankelijke UI-componenten. Gebruik deze skill
  wanneer de gebruiker vraagt over 'NL Design System', 'NLDS',
  'design tokens overheid', 'design token', 'Rijkshuisstijl',
  'Rijksoverheid huisstijl', 'government design system',
  'community componenten', 'community components',
  'Storybook overheid', 'overheid componenten', 'government components',
  'Utrecht design system', 'Den Haag design system',
  'Amsterdam design system', 'gemeente design system',
  'overheid button', 'overheid formulier', 'overheid component',
  'overheid thema', 'overheid theme', 'CSS custom properties overheid',
  'Web Component overheid', 'React component overheid',
  'Angular component overheid', 'Vue component overheid',
  'Figma overheid', 'accessible component', 'toegankelijk component',
  of wanneer de gebruiker een website of applicatie wil bouwen
  met herbruikbare overheidscomponenten en design tokens.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(npm *)
  - Bash(npx *)
  - Bash(gh api *)
  - Bash(gh search *)
---

# NL Design System — Herbruikbare Overheidscomponenten

Bouw consistente, toegankelijke overheidswebsites met NL Design System community componenten en design tokens.

Bron: [NL Design System](https://nldesignsystem.nl/) | [GitHub](https://github.com/nl-design-system) | [Storybook](https://nl-design-system.github.io/themes/)

## Wat is NL Design System?

| Aspect | Detail |
|--------|--------|
| **Doel** | Eén componentenbibliotheek voor alle Nederlandse overheidswebsites |
| **Aanpak** | Community-driven; organisaties bouwen samen, delen via design tokens |
| **Kernprincipe** | Elke organisatie gebruikt dezelfde componenten met eigen thema via design tokens |
| **Technologie** | Framework-agnostisch: Web Components, React, Angular, Vue |
| **Toegankelijkheid** | WCAG 2.1 AA ingebouwd in elk component |
| **Governance** | Kernteam bij ICTU; community uit gemeenten, Rijksoverheid, uitvoeringsorganisaties |

### Architectuur

```
┌──────────────────────────────────────────────────────────────┐
│  THEMA (design tokens)                                       │
│  Gemeente Amsterdam / Rijksoverheid / Gemeente Utrecht / ... │
├──────────────────────────────────────────────────────────────┤
│  COMPONENTEN (community components)                          │
│  Button, TextInput, Alert, Heading, Table, Pagination, ...   │
├──────────────────────────────────────────────────────────────┤
│  FRAMEWORK IMPLEMENTATIE                                     │
│  Web Components │ React │ Angular │ Vue │ HTML/CSS           │
└──────────────────────────────────────────────────────────────┘
```

## Design tokens

Design tokens zijn de kern van NL Design System. Ze definiëren kleuren, typografie, spacing en andere visuele eigenschappen als CSS Custom Properties.

### Token-architectuur (3 lagen)

| Laag | Prefix | Voorbeeld | Beschrijving |
|------|--------|-----------|-------------|
| **Brand** | `--{org}-` | `--rijksoverheid-color-blue-500` | Organisatie-specifieke waarden |
| **Common** | `--nl-` | `--nl-color-action-default` | Gedeelde semantische tokens |
| **Component** | `--nl-{component}-` | `--nl-button-background-color` | Component-specifieke tokens |

### Design tokens implementeren

```css
/* 1. Brand tokens (organisatie-specifiek) */
:root {
  /* Rijksoverheid thema */
  --rijksoverheid-color-hemelblauw: #007bc7;
  --rijksoverheid-color-donkerblauw: #01689b;
  --rijksoverheid-color-groen: #39870c;
  --rijksoverheid-color-wit: #ffffff;
  --rijksoverheid-color-zwart: #000000;

  --rijksoverheid-font-family: "RijksoverheidSansWebText", Arial, sans-serif;
  --rijksoverheid-font-size-base: 1rem;
  --rijksoverheid-line-height-base: 1.5;

  --rijksoverheid-space-block-sm: 0.5rem;
  --rijksoverheid-space-block-md: 1rem;
  --rijksoverheid-space-block-lg: 2rem;
}

/* 2. Semantische tokens (mapping brand → common) */
:root {
  --nl-color-action-default: var(--rijksoverheid-color-hemelblauw);
  --nl-color-action-hover: var(--rijksoverheid-color-donkerblauw);
  --nl-color-action-active: var(--rijksoverheid-color-donkerblauw);
  --nl-color-success: var(--rijksoverheid-color-groen);

  --nl-font-family-body: var(--rijksoverheid-font-family);
  --nl-font-size-body: var(--rijksoverheid-font-size-base);
  --nl-line-height-body: var(--rijksoverheid-line-height-base);
}

/* 3. Component tokens */
:root {
  --nl-button-background-color: var(--nl-color-action-default);
  --nl-button-color: var(--rijksoverheid-color-wit);
  --nl-button-font-family: var(--nl-font-family-body);
  --nl-button-font-weight: 700;
  --nl-button-padding-block: var(--rijksoverheid-space-block-sm);
  --nl-button-padding-inline: var(--rijksoverheid-space-block-md);
  --nl-button-border-radius: 0;
}
```

### JSON design tokens (Design Tokens Community Group)

```json
{
  "rijksoverheid": {
    "color": {
      "hemelblauw": { "$value": "#007bc7", "$type": "color" },
      "donkerblauw": { "$value": "#01689b", "$type": "color" },
      "groen": { "$value": "#39870c", "$type": "color" }
    },
    "font": {
      "family": {
        "body": { "$value": "'RijksoverheidSansWebText', Arial, sans-serif", "$type": "fontFamily" }
      },
      "size": {
        "base": { "$value": "1rem", "$type": "dimension" }
      }
    },
    "space": {
      "sm": { "$value": "0.5rem", "$type": "dimension" },
      "md": { "$value": "1rem", "$type": "dimension" },
      "lg": { "$value": "2rem", "$type": "dimension" }
    }
  }
}
```

## Community componenten

### Beschikbare componenten (selectie)

| Component | Status | WCAG | Beschrijving |
|-----------|--------|------|-------------|
| **Button** | Community | AA | Primair, secundair, destructief |
| **Link** | Community | AA | Inline link, standalone link |
| **Heading** | Community | AA | h1-h6 met semantische tokens |
| **Paragraph** | Community | AA | Tekst met regelafstand |
| **TextInput** | Community | AA | Invoerveld met label en foutmelding |
| **Textarea** | Community | AA | Meerdere regels invoer |
| **Select** | Community | AA | Dropdownselectie |
| **Checkbox** | Community | AA | Enkele of groep checkboxes |
| **RadioButton** | Community | AA | Radiobutton-groep |
| **FormField** | Community | AA | Wrapper: label + input + hint + error |
| **Alert** | Community | AA | Informatie, waarschuwing, fout, succes |
| **Table** | Community | AA | Datatabel met sortering |
| **Pagination** | Community | AA | Pagina-navigatie |
| **Breadcrumb** | Community | AA | Kruimelpad-navigatie |
| **Accordion** | Community | AA | Uitklapbare secties |
| **Badge** | Community | AA | Statuslabel |
| **Skiplink** | Community | AA | "Ga naar hoofdinhoud" |

### Component gebruiken — HTML/CSS

```html
<!-- NL Design System class-name conventie: BEM -->

<!-- Button -->
<button class="nl-button nl-button--primary" type="button">
  Verzenden
</button>

<button class="nl-button nl-button--secondary" type="button">
  Annuleren
</button>

<!-- Alert -->
<div class="nl-alert nl-alert--warning" role="alert">
  <div class="nl-alert__icon" aria-hidden="true">⚠</div>
  <div class="nl-alert__content">
    <p class="nl-alert__message">Let op: de bewaartermijn is bijna verlopen.</p>
  </div>
</div>

<!-- Form Field -->
<div class="nl-form-field">
  <label class="nl-form-field__label" for="naam">
    Naam
    <span class="nl-form-field__label--required" aria-hidden="true">*</span>
  </label>
  <p class="nl-form-field__description" id="naam-hint">
    Uw volledige naam zoals op uw identiteitsbewijs.
  </p>
  <input
    class="nl-text-input"
    id="naam"
    name="naam"
    type="text"
    required
    aria-required="true"
    aria-describedby="naam-hint"
    autocomplete="name"
  />
</div>

<!-- Form Field met fout -->
<div class="nl-form-field nl-form-field--invalid">
  <label class="nl-form-field__label" for="email">E-mailadres</label>
  <p class="nl-form-field__error" id="email-error" role="alert">
    Vul een geldig e-mailadres in.
  </p>
  <input
    class="nl-text-input nl-text-input--invalid"
    id="email"
    type="email"
    aria-invalid="true"
    aria-describedby="email-error"
    autocomplete="email"
  />
</div>
```

### Component gebruiken — React

```bash
npm install @nl-design-system-community/button-react
npm install @nl-design-system-community/textinput-react
```

```tsx
import { Button } from '@nl-design-system-community/button-react';
import { FormField, TextInput } from '@nl-design-system-community/textinput-react';

function AanvraagFormulier() {
  return (
    <form noValidate>
      <FormField
        label="Naam"
        description="Uw volledige naam zoals op uw identiteitsbewijs."
        required
      >
        <TextInput
          name="naam"
          autoComplete="name"
          required
        />
      </FormField>

      <Button type="submit" appearance="primary">
        Aanvraag indienen
      </Button>
    </form>
  );
}
```

### Component gebruiken — Web Component

```html
<!-- Web Components werken in elk framework -->
<script type="module" src="@nl-design-system-community/button-web-component"></script>

<nl-button appearance="primary">
  Verzenden
</nl-button>
```

## Thema's van organisaties

| Organisatie | Thema-package | Kenmerken |
|-------------|--------------|-----------|
| **Rijksoverheid** | `@nl-design-system/rijksoverheid-theme` | Hemelblauw (#007bc7), RijksoverheidSans |
| **Gemeente Utrecht** | `@utrecht/design-tokens` | Complete implementatie; meest volwassen |
| **Gemeente Den Haag** | `@gemeente-denhaag/design-tokens` | Uitgebreide componentenset |
| **Gemeente Amsterdam** | `@amsterdam/design-system-tokens` | Inclusief kaart- en datacomponenten |
| **Logius** | `@logius/design-tokens` | DigiD, MijnOverheid |

### Eigen thema maken

```bash
# Start met het NL Design System template
npx @nl-design-system/create-theme mijn-gemeente

# Structuur:
# mijn-gemeente/
#   ├── src/
#   │   ├── brand.tokens.json      # Brand tokens
#   │   ├── common.tokens.json     # Semantische mapping
#   │   └── component.tokens.json  # Component-specifiek
#   ├── dist/
#   │   └── theme.css              # Gegenereerde CSS
#   └── package.json
```

## Storybook

NL Design System gebruikt Storybook als centrale documentatie en demo-omgeving.

```bash
# Storybook opzetten met NL Design System
npx storybook@latest init
npm install @nl-design-system/storybook-theme
```

```javascript
// .storybook/preview.js
import '@mijn-gemeente/design-tokens/dist/theme.css';

export const parameters = {
  a11y: {
    config: {
      rules: [
        { id: 'color-contrast', enabled: true },
        { id: 'label', enabled: true },
      ],
    },
  },
};
```

## Rijkshuisstijl — kernwaarden

| Aspect | Specificatie |
|--------|-------------|
| **Primaire kleur** | Hemelblauw #007bc7 |
| **Secundaire kleur** | Donkerblauw #01689b |
| **Succeskleur** | Groen #39870c |
| **Foutkleur** | Rood #d52b1e |
| **Lettertype** | RijksoverheidSansWebText (koppen), RijksoverheidSerifWebText (body) |
| **Beeldmerk** | Rijksoverheid lint met rijkswapen |
| **Contrasteis** | Minimaal 4.5:1 tekst; 3:1 grote tekst/UI (WCAG AA) |

## Implementatie-checklist

- [ ] **Design tokens**: thema gedefinieerd met CSS Custom Properties op 3 lagen
- [ ] **Community componenten**: componenten geinstalleerd uit NL Design System community
- [ ] **BEM-naamgeving**: CSS classes conform nl-{component}--{modifier} conventie
- [ ] **Toegankelijkheid**: alle componenten getest op WCAG 2.1 AA
- [ ] **Storybook**: componenten gedocumenteerd in Storybook met a11y-addon
- [ ] **Responsief**: componenten werken op 320px (reflow) en 200% zoom
- [ ] **Dark mode**: design tokens ondersteunen prefers-color-scheme (optioneel)
- [ ] **Formulieren**: alle invoervelden met label, hint, foutmelding; aria-attributen correct
- [ ] **Focus**: zichtbare focus-indicator op alle interactieve elementen
- [ ] **Typografie**: lettertype geladen; fallback fonts gedefinieerd
- [ ] **Iconen**: SVG-iconen met aria-hidden="true" (decoratief) of role="img" + aria-label (informatief)
- [ ] **Framework-agnostisch**: componenten bruikbaar in React, Angular, Vue of vanilla HTML

## Gerelateerde skills

| Skill | Wanneer te gebruiken |
|-------|---------------------|
| **digitoegankelijk** | WCAG 2.1/2.2 eisen, EN 301 549, testtools voor toegankelijkheid |
| **gemma-common-ground** | GEMMA architectuur en Open Formulieren voor gemeentelijke apps |
| **nora-architectuur** | Verplichte open standaarden en architectuurprincipes |

## Meer informatie

- [NL Design System](https://nldesignsystem.nl/) | [GitHub](https://github.com/nl-design-system)
- [Storybook — alle thema's](https://nl-design-system.github.io/themes/)
- [Gemeente Utrecht componenten](https://nl-design-system.github.io/utrecht/) — meest volwassen implementatie
- [Rijkshuisstijl](https://www.rijkshuisstijl.nl/) — visuele identiteit Rijksoverheid
- [Design Tokens Community Group](https://design-tokens.github.io/community-group/format/) — W3C standaard
- [Figma — NL Design System](https://www.figma.com/@nldesignsystem) — design assets
