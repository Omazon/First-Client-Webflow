---
name: client-first
description: >-
  Use when building, reviewing, auditing, or refactoring Webflow projects that follow
  the Finsweet Client-First style system. Triggers on any mention of Client-First,
  Client-first, Finsweet naming conventions, custom vs utility classes, underscore
  class naming, is- combo classes, page-wrapper / main-wrapper / section_ core
  structure, padding-global / padding-section-*, container-* / max-width-*,
  rem sizing, heading-style-h# / text- utility classes, padding-* / margin- /
  spacer-* utility spacing, Finsweet Folders, Custom class folders, Utility class
  folders, Client-First Variables (primitive / semantic tokens), Client-First
  Interactions naming (Element [Action State]), Fluid Responsive root-font scaling,
  Global Styles embed snippets, Client-First v1 to v2 migration, or any question
  about how to apply Client-First in Webflow Designer. Do not use for arbitrary
  Webflow or CSS questions unrelated to the Client-First system.
license: MIT
metadata:
  author: Omazon
  version: "1.0.0"
  source: https://finsweet.com/client-first/docs
  upstream: Finsweet Client-First (unofficial skill)
  date: June 2026
---

# Client-First for Webflow

Unofficial AI-agent skill that encodes the Finsweet Client-First style system
as procedural guidance. Built from Finsweet's public documentation. All credit
for the underlying system goes to Finsweet.

Client-First = "We put our clients' interests first in the Webflow build
process." It is a collection of principles, class naming conventions, and a
core structure for building scalable Webflow projects in Designer.

## When to use this skill

Activate this skill when the user:

- Asks how to name a class, build a section, or structure a page in a Client-First project.
- Mentions `padding-global`, `container-large`, `section_home`, `is-brand`, `text-size-medium`, `margin-large`, `heading-style-h2`, `spacer-large`, `page-wrapper`, `main-wrapper`, `nav_component`, `team-list_headshot-wrapper`, etc.
- Asks why a margin/padding class is overwriting another (CSS Specificity in Client-First).
- Wants to add an Interaction and asks how to name it the Client-First way.
- Is migrating a Webflow project from Client-First v1 to v2.
- Is converting a non-Client-First Webflow project to Client-First.
- Mentions "Folders" by Finsweet Extension in a Webflow context.
- Asks about Fluid Responsive scaling in a Client-First project.
- Wants to set up color Variables (primitive / semantic tokens) the Client-First way.
- Asks to refactor messy class names into Client-First conventions.

Do not use this skill for general Webflow or CSS questions that are not
related to the Client-First system.

## Core rules (non-negotiable)

1. **Custom classes use `_` in the class name.** Utility classes do not.
   `team-list_headshot-wrapper` is a custom class. `text-color-primary` is a
   utility class. Never mix the convention.
2. **One underscore equals one folder** in the Folders view. Two underscores
   equal two nested folders. Underscore is for organization, not decoration.
3. **Combo classes use the `is-` prefix.** `button is-brand`, `section_header
   is-home`, `spacer-large is-mobile-small`. The `is-` variant only works on
   top of the base class.
4. **Use rem for all sizes**, not px. 1rem = 16px at default browser font size.
   Use easily readable rem values (0.25, 0.5, 1, 1.5, 2, 2.5, 3, 4, 5...).
   Exceptions: 14px = 0.875rem (typography), 2px = 0.125rem (tiny spacing),
   1px = 1px (borders, retina).
5. **Don't deep stack classes.** 1-2 classes: great. 3: question it. 4:
   absolute max. 5+: create a custom class. Stacked classes cannot be reordered
   in the Webflow Styles panel and are painful to edit on mobile breakpoints.
6. **Stack similar classes** on the same element (margin with margin, padding
   with padding, typography with typography). Never add new styles to a stack
   of global utility classes — that creates a combo class.
7. **Use the core structure on every page:** `page-wrapper` > `main-wrapper` >
   `section_[identifier]` > `padding-global` > `container-[size]`. Use the
   `<main>` HTML tag on `main-wrapper` and `<section>` on each section.
8. **Prefer utility classes for global, recurring CSS properties** (margin,
   padding, color, typography, max-width, display). Prefer custom classes for
   anything instance-specific, component-level, or that needs unique
   responsive behavior.
9. **Most Headings and Paragraphs should have no class.** Style the default
   HTML tags globally. Add a class only when there is a variation.
10. **Style goes from general to specific** within a class name:
    `text-size-large`, `team-list_headshot-wrapper`, not `large-size-text`.

## Quick reference: utility class prefixes

| Prefix | Purpose | Example |
| --- | --- | --- |
| `text-` | Typography utility (size, color, weight, style, align) | `text-size-large`, `text-color-primary` |
| `heading-` | Heading style overrides | `heading-style-h2` |
| `padding-` | Padding direction + size (utility) | `padding-global`, `padding-large`, `padding-section-medium` |
| `margin-` | Margin direction + size (utility) | `margin-bottom`, `margin-large` |
| `container-` | Max-width container | `container-large`, `container-medium`, `container-small` |
| `max-width-` | Nested max-width | `max-width-small`, `max-width-full` |
| `spacer-` | One-class empty spacing block | `spacer-large` |
| `button` | Base button | `button`, `button is-secondary`, `button is-text` |
| `background-color-` | Background color utility | `background-color-primary` |
| `icon-` | Icon sizing | `icon-1x1-medium`, `icon-height-small` |
| `hide-` | Responsive hide | `hide-tablet`, `hide-mobile-portrait` |
| `display-` | Display helpers | `display-inlineflex` |
| `is-` | Combo class prefix (variant) | `is-brand`, `is-home`, `is-mobile-small` |
| `section_` | Custom section wrapper | `section_home`, `section_pricing` |
| `nav_` | Custom nav folder | `nav_component`, `nav_link` |
| `form_` | Custom form folder | `form_input`, `form_label` |
| `page-wrapper` | Core structure outermost | (single instance) |
| `main-wrapper` | Core structure main | (single instance) |
| `padding-global` | Site-wide horizontal padding | (single instance) |
| `inherit-color` | Override color → inherit parent | (single utility) |

## Reference routing

Load the reference file that matches the user's question. Do not load all
references — pick the smallest set that answers the question.

| Topic | Reference file | When to load |
| --- | --- | --- |
| Intro, goals, naming convention mindset | `references/00-overview.md` | First time user asks "what is Client-First" or wants the philosophy |
| Custom / utility / global / combo class types, no deep stacking | `references/01-classes-strategy-1.md` | User asks about class types or naming |
| `page-wrapper` / `main-wrapper` / `section_` / `padding-global` / `container-*` / `padding-section-*` | `references/02-core-structure.md` | User asks about page structure, padding, containers, sections |
| rem math, browser font size, px to rem conversions | `references/03-sizes-and-rem.md` | User asks about units, rem, px, accessibility scaling |
| `heading-style-h#`, `text-size-*`, `text-color-*`, default HTML tag styles | `references/04-typography-strategy.md` | User asks about text, headings, typography |
| Spacing blocks, spacing wrappers, custom class spacing, CSS Grid spacing, `spacer-*` responsive combos | `references/05-spacing-strategy.md` | User asks about margin, padding, spacing, gaps |
| Full catalog of CF utility classes (sizes, structure, display, hide, etc.) | `references/06-utility-class-systems.md` | User asks "what utility classes are available" or needs exact class names |
| Custom class creation, when to use them, deep stacking limits, combo class strategy, no layout system | `references/07-classes-strategy-2.md` | User asks when to create a custom class, combo class decisions, or layout |
| Folders feature (Finsweet Extension), underscore folder system, utility folder system | `references/08-folders.md` | User asks about Folders, organizing classes, underscore conventions |
| Folder strategies (one vs nested, page-name, reusable, components) | `references/09-folders-strategy.md` | User asks how to structure folders for a project type |
| Color Variables (primitive + semantic tokens), naming, grouping | `references/10-variables.md` | User asks about color tokens, variables, theming |
| Interaction naming convention `Element [Action State]` | `references/11-interactions-naming.md` | User asks how to name Webflow Interactions / animations |
| Fluid Responsive (root-font scaling) | `references/12-fluid-responsive.md` | User asks about fluid responsive, scaling, vw vs rem |
| Semantic HTML tags (`<header>`, `<main>`, `<section>`, `<article>`, etc.) | `references/13-semantic-html.md` | User asks about HTML semantics, tag choice, SEO structure |
| Accessibility (keyboard nav, ARIA, focus, alt text) | `references/14-accessibility.md` | User asks about a11y, screen readers, keyboard navigation |
| Global Styles embed snippets (text clarity, focus state, container centerizer, etc.) | `references/15-global-styles-embed.md` | User asks about the global CSS embed block, custom CSS overrides |
| CSS Specificity (why margin classes overwrite, order of creation, !important) | `references/16-css-specificity.md` | User asks why a utility class is not working or being overridden |
| Client-First v1 to v2 migration changes | `references/17-v1-to-v2.md` | User has a v1 project, asks about renaming, `page-padding` → `padding-global`, etc. |

## Output style for the agent

- When suggesting class names, **use the exact CF conventions** (underscore
  for custom, dash-only for utility, `is-` for combo, general-to-specific).
- When generating Webflow project structures, **always include the core
  structure** (`page-wrapper` > `main-wrapper` > `section_[id]` > `padding-global` > `container-[size]`).
- When proposing a spacing solution, **prefer utility spacing first**
  (blocks / wrappers / `spacer-*`) and only fall back to a custom class
  with margin/padding when there is a clear use case (per `references/05`).
- When proposing a typography solution, **prefer no class on text by
  default** — only add `text-*` or `heading-style-h#` when there is a
  variation.
- When auditing an existing project, **call out**: missing core structure,
  deep-stacked elements (≥4 classes), utility classes used where a custom
  class would be cleaner, px used instead of rem, classes that break the
  custom/utility naming convention.
- Never invent class names that are not in the CF system. If a need is not
  covered, propose a new utility or custom class following the conventions
  and explain the rationale.

## Source

- All content adapted from Finsweet Client-First documentation:
  https://finsweet.com/client-first/docs
- Original system and concepts by Finsweet. This skill is unofficial.
- Open the [official Cloneable](https://finsweet.info/client-first-cloneable)
  and the [official site](https://finsweet.com/client-first/) for the full
  experience.
