# Externe Repo Consolidatie

Documentatie over externe Djimit repos met skills en de consolidatie-strategie.

## Overzicht Externe Repos

| Repo | Skills | Status | Actie |
|------|--------|--------|-------|
| djimit/ai-governance | ai-governance | Geconsolideerd | Skill toegevoegd aan overheid-plugins |
| djimit/common-ground | common-ground | Geconsolideerd | Skill toegevoegd aan overheid-plugins |
| djimit/nis2-compliance | nis2-compliance | Geconsolideerd | Skill toegevoegd aan overheid-plugins |
| djimit/bio-security-baseline | bio-security-baseline | Geconsolideerd | Marketplace plugin |
| djimit/juraregel | juraregel-integratie | Geconsolideerd | Skill toegevoegd aan overheid-plugins |
| djimit/sovereign-ai-in-a-box | - | Referentie | BIO2-compliant on-prem AI |
| djimit/djimitflo | - | Runtime | Agent orchestration platform |

## Consolidatie-Strategie

### Principe: overheid-plugins als centrale catalogus

Alle skills voor de Nederlandse overheid worden geconsolideerd in
`djimit/overheid-plugins`. Externe repos worden:

1. **Gearchiveerd** als de skill volledig is gemigreerd
2. **Gerefereerd** als marketplace plugin als de repo autonoom blijft
3. **Gedocumenteerd** in deze consolidatie-documentatie

### Migratiepad

1. Skill inhoud wordt gekopieerd naar `overheid-plugins/skills/<naam>/`
2. Cross-references worden bijgewerkt
3. CI/CD validatie wordt uitgevoerd
4. Externe repo wordt gearchiveerd of gerefereerd in marketplace.json

### Uitzonderingen

Sommige repos blijven autonoom vanwege hun runtime-natuur:

- **djimit/juraregel** — Heeft eigen Rule API runtime, SDK, dashboard
- **djimit/djimitflo** — Is een orchestration platform, geen skill-catalogus
- **djimit/sovereign-ai-in-a-box** — Is een deployment tool, geen skill

Deze repos worden gerefereerd als marketplace plugins of in de
cross-reference matrix.

## Gerelateerde skills

- [cross-reference-matrix](../skills/cross-reference-matrix/SKILL.md) — Volledige matrix
- [agentic-governance](../skills/agentic-governance/SKILL.md) — Agent orchestratie
