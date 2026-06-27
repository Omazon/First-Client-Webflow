# Changelog

All notable changes to this skill will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-06-27

### Added

- Initial release of the unofficial Client-First skill for AI agents.
- Root `SKILL.md` with rich frontmatter description, core rules, quick
  reference table of utility class prefixes, and a routing table to the
  `references/` files.
- 18 reference files covering the full Client-First v2 documentation:
  - `00-overview.md` — Intro, goals, naming mindset.
  - `01-classes-strategy-1.md` — Class types and no deep stacking.
  - `02-core-structure.md` — page-wrapper, main-wrapper, section_,
    padding-global, container-*, padding-section-*.
  - `03-sizes-and-rem.md` — rem math and px-to-rem conversions.
  - `04-typography-strategy.md` — Default HTML tags + utility classes.
  - `05-spacing-strategy.md` — Spacing block, wrapper, custom,
    CSS Grid strategies.
  - `06-utility-class-systems.md` — Full catalog of CF utility classes.
  - `07-classes-strategy-2.md` — Custom class creation, combo strategy,
    no deep stacking, no global layout system.
  - `08-folders.md` — Folders feature, underscore and utility folder
    conventions.
  - `09-folders-strategy.md` — One vs nested folders, page-name
    strategy, component libraries.
  - `10-variables.md` — Color variables with primitive and semantic
    token architecture.
  - `11-interactions-naming.md` — `Element [Action State]` convention.
  - `12-fluid-responsive.md` — Root-font scaling.
  - `13-semantic-html.md` — Proper HTML semantics in Webflow.
  - `14-accessibility.md` — Keyboard navigation, ARIA, focus, hide
    patterns.
  - `15-global-styles-embed.md` — Every CSS snippet in the global
    embed block.
  - `16-css-specificity.md` — Why margin/padding classes break after
    copy-paste.
  - `17-v1-to-v2.md` — Migration guide.
- `README.md` with install instructions and repository structure.
- `LICENSE` (MIT) with credit to Finsweet for the underlying system.

### Source

- All content adapted from Finsweet's public Client-First documentation
  at https://finsweet.com/client-first/docs.
- Skill packaging: Omazon.
- The Client-First system and all original documentation content is the
  intellectual property of Finsweet.
