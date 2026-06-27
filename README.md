# Client-First Skill for AI Agents

An unofficial skill that encodes the [Finsweet Client-First](https://finsweet.com/client-first/docs)
Webflow style system as procedural guidance for AI coding agents.

All credit for the underlying system, the class naming conventions, the
core structure, and the design system documentation goes to Finsweet.
This skill is a derivative work, built from Finsweet's public
documentation.

## Install

```bash
npx skills add Omazon/First-Client-Webflow
```

## What this skill covers

Client-First is a Webflow style system focused on:

- **Scalability** — a project that grows cleanly.
- **Speed** — fast to build and fast to maintain.
- **Client hand-off** — class names a non-developer can read and understand.
- **Standardization** — a core structure shared across all pages.

The skill encodes:

- **Naming convention** — custom classes use `_`, utility classes don't.
  Combo variants use `is-`. Names go general → specific.
- **Class types** — custom, utility, global, combo.
- **Core structure** — `page-wrapper` → `main-wrapper` → `section_[id]` →
  `padding-global` → `container-[size]`.
- **Sizes and rem** — use rem, not px. 1rem = 16px.
- **Typography strategy** — default HTML tags first, utility classes for
  variations.
- **Spacing strategy** — utility blocks, utility wrappers, custom
  class on element, CSS Grid on parent.
- **Utility class systems** — the full catalog of CF utility classes
  (`text-*`, `heading-*`, `padding-*`, `margin-*`, `container-*`,
  `max-width-*`, `spacer-*`, `button`, etc.).
- **Classes strategy 2** — when to create a custom class, no deep
  stacking, the `is-` combo system, no global layout system.
- **Folders** — Finsweet Extension's virtual folder organization.
- **Folders strategy** — one folder vs nested, page-name strategy,
  component libraries.
- **Variables** — color variables with primitive + semantic token
  architecture.
- **Interactions naming** — `Element [Action State]` convention.
- **Fluid responsive** — root-font scaling instead of `vw`/`vh`.
- **Semantic HTML tags** — proper HTML semantics in Webflow.
- **Accessibility** — keyboard nav, ARIA, focus, hide patterns.
- **Global Styles embed** — every snippet in the cloneable's global
  embed block.
- **CSS specificity** — why margin/padding classes break after
  copy-paste, and how to fix.
- **V1 → V2 migration** — every rename and addition.

## Source

- Finsweet Client-First docs: https://finsweet.com/client-first/docs
- Finsweet: https://finsweet.com
- Original cloneable: https://finsweet.info/client-first-cloneable

## Repository structure

```
client-first/
├── SKILL.md                          # Root entry point — loaded first
├── README.md                         # This file
├── LICENSE                           # MIT
├── CHANGELOG.md                      # Version history
├── .gitignore
└── references/
    ├── 00-overview.md                # Intro, goals, naming mindset
    ├── 01-classes-strategy-1.md      # Custom / utility / global / combo
    ├── 02-core-structure.md          # page-wrapper, main-wrapper, section_, padding, container
    ├── 03-sizes-and-rem.md           # rem math, accessibility scaling
    ├── 04-typography-strategy.md     # HTML tags + utility classes
    ├── 05-spacing-strategy.md        # Block / wrapper / custom / grid
    ├── 06-utility-class-systems.md   # Full utility class catalog
    ├── 07-classes-strategy-2.md      # Custom class creation, combo strategy, no deep stacking
    ├── 08-folders.md                 # Folders feature (Finsweet Extension)
    ├── 09-folders-strategy.md        # One vs nested folders, page-name, components
    ├── 10-variables.md               # Color variables (primitive / semantic)
    ├── 11-interactions-naming.md     # Element [Action State] convention
    ├── 12-fluid-responsive.md        # Root-font scaling
    ├── 13-semantic-html.md           # header, main, section, article, etc.
    ├── 14-accessibility.md           # Keyboard nav, ARIA, focus, hide
    ├── 15-global-styles-embed.md     # CSS snippets in the global embed
    ├── 16-css-specificity.md         # Order of creation, why classes overwrite
    └── 17-v1-to-v2.md                # Migration from Client-first v1
```

## License

MIT — see [LICENSE](./LICENSE).

## Credits

- **System, design, and content:** Finsweet (https://finsweet.com).
- **Skill packaging:** Omazon (this repository).
