---
name: omazon-webflow-first-client
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
  version: "1.2.0"
  source: https://finsweet.com/client-first/docs
  repo: https://github.com/Omazon/First-Client-Webflow
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

## Deep dive references (GitHub)

For detailed explanations, examples, and edge cases beyond what is inlined in
this file, the agent fetches reference documents from the GitHub repository.
**The agent must be able to fetch raw URLs from GitHub** to use these deep
dive references.

**Raw URL pattern:**

```
https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/<file>.md
```

The full routing table with each file's URL is at the end of this document
under "Deep dive references (GitHub)".

If the agent cannot fetch URLs, this skill still works for ~90% of cases —
naming, core structure, core rules, and the most-used utility classes are all
inlined below. Only the detailed guides for each topic require the fetch.

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
| `button` | Base button (use with `is-` variants) | `button`, `button is-secondary`, `button is-text` |
| `background-color-` | Background color utility | `background-color-primary` |
| `icon-` | Icon sizing | `icon-1x1-medium`, `icon-height-small` |
| `hide-` | Responsive hide | `hide-tablet`, `hide-mobile-portrait` |
| `display-` | Display helpers | `display-inlineflex` |
| `is-` | Combo class prefix (variant) | `is-brand`, `is-home`, `is-mobile-small` |
| `section_` | Custom section wrapper | `section_home`, `section_pricing` |
| `nav_` | Custom nav folder | `nav_component`, `nav_link` |
| `form_` | Custom form folder | `form_input`, `form_label` |
| `page-wrapper` | Core structure outermost | (single instance per page) |
| `main-wrapper` | Core structure main | (single instance per page) |
| `padding-global` | Site-wide horizontal padding | (single instance per project) |
| `inherit-color` | Override color → inherit parent | (single utility) |

## Core structure (use on every page)

```
page-wrapper (outermost, no class on <body>)
└── main-wrapper        (HTML tag: <main>)
    └── section_home    (HTML tag: <section>)
        └── padding-global
            └── padding-section-large
                └── container-large
                    └── (content)
```

| Class | Purpose | HTML tag | CSS key properties |
| --- | --- | --- | --- |
| `page-wrapper` | Outermost parent of all page content | div | Optional. Limit body styles to typography and `background-color` only. |
| `main-wrapper` | Main content of the page. Nav and footer outside. | **`<main>`** | Optional. Accessibility. |
| `section_[id]` | One section per logical content block. All sections live in the `section_` folder. | **`<section>`** | Avoid styling. For dark/light variant use `is-style-dark` combo. |
| `padding-global` | Site-wide left/right padding | div | Only `padding-left` and `padding-right`. |
| `padding-section-[size]` | Top/bottom padding for sections. Apply to the same div as `padding-global`. | div | Only `padding-top` and `padding-bottom`. |
| `container-[size]` | Centered, max-width wrapper. `margin: 0 auto`, `width: 100%`, `max-width`. | div | `small` ≈ 48rem, `medium` ≈ 64rem, `large` ≈ 80rem (editable). |

### Section naming examples

```
section_home
section_about
section_how-it-works
section_testimonials
section_pricing
section_cta
section_faq
```

### Container sizes

```
container-small
container-medium
container-large
```

### Section padding sizes

```
padding-section-small
padding-section-medium
padding-section-large
```

### Core structure flexibility

`padding-global` is decoupled from `container-*` so they can be used
independently. Place `padding-global` as a parent, a child, or together with
the container.

## Most-used utility classes (catalog)

### Margin direction

```
margin-top
margin-bottom
margin-left
margin-right
margin-horizontal
margin-vertical
```

### Margin size

| Class | Value |
| --- | ---: |
| `margin-0` | 0rem |
| `margin-tiny` | 0.125rem |
| `margin-xxsmall` | 0.25rem |
| `margin-xsmall` | 0.5rem |
| `margin-small` | 1rem |
| `margin-medium` | 2rem |
| `margin-large` | 3rem |
| `margin-xlarge` | 4rem |
| `margin-xxlarge` | 5rem |
| `margin-huge` | 6rem |
| `margin-xhuge` | 8rem |
| `margin-xxhuge` | 12rem |
| `margin-custom1` | 1.5rem |
| `margin-custom2` | 2.5rem |
| `margin-custom3` | 3.5rem |

### Padding direction

```
padding-top
padding-bottom
padding-left
padding-right
padding-horizontal
padding-vertical
```

### Padding size

| Class | Value |
| --- | ---: |
| `padding-0` | 0rem |
| `padding-tiny` | 0.125rem |
| `padding-xxsmall` | 0.25rem |
| `padding-xsmall` | 0.5rem |
| `padding-small` | 1rem |
| `padding-medium` | 2rem |
| `padding-large` | 3rem |
| `padding-xlarge` | 4rem |
| `padding-xxlarge` | 5rem |
| `padding-huge` | 6rem |
| `padding-xhuge` | 8rem |
| `padding-xxhuge` | 12rem |
| `padding-custom1` | 1.5rem |
| `padding-custom2` | 2.5rem |
| `padding-custom3` | 3.5rem |

### Spacer system (one-class spacing block)

Empty Div Block that creates space between sibling elements. Supports `is-`
responsive combo classes.

```
spacer-tiny       (0.125rem)
spacer-xxsmall    (0.25rem)
spacer-xsmall     (0.5rem)
spacer-small      (1rem)
spacer-medium     (2rem)
spacer-large      (3rem)
spacer-xlarge     (4rem)
spacer-xxlarge    (5rem)
spacer-huge       (6rem)
spacer-xhuge      (8rem)
spacer-xxhuge     (12rem)
spacer-custom1    (1.5rem)
spacer-custom2    (2.5rem)
spacer-custom3    (3.5rem)
```

Responsive combo: `spacer-large is-mobile-small`.

### Heading style switch

Change a Heading's style without changing its tag. Use when the SEO tag and
the visual style don't match.

```
heading-style-h1
heading-style-h2
heading-style-h3
heading-style-h4
heading-style-h5
heading-style-h6
```

Example: `H1 + heading-style-h2` — visually H2, semantically H1 for SEO.

### Text size

```
text-size-tiny
text-size-small
text-size-regular
text-size-medium
text-size-large
```

### Text style

```
text-style-allcaps
text-style-italic
text-style-link
text-style-muted
text-style-nowrap
text-style-quote
text-style-strikethrough
text-style-2lines
text-style-3lines
```

### Text weight

```
text-weight-xbold
text-weight-bold
text-weight-semibold
text-weight-normal
text-weight-light
```

### Text alignment

```
text-align-left
text-align-center
text-align-right
```

### Text color

```
text-color-primary
text-color-secondary
text-color-alternate
```

### Buttons

```
button
button is-secondary
button is-text
```

### Max width (nested)

Use `container-*` for the primary outer max-width. Use `max-width-*` for
nested cases.

```
max-width-xxlarge   (80rem)
max-width-xlarge    (64rem)
max-width-large     (48rem)
max-width-medium    (32rem)
max-width-small     (20rem)
max-width-xsmall    (16rem)
max-width-xxsmall   (12rem)
```

`max-width-full` (and `-tablet`, `-mobile-landscape`, `-mobile-portrait`)
sets `max-width: none` at the corresponding breakpoint.

### Hide

```
hide
hide-tablet
hide-mobile-landscape
hide-mobile-portrait
```

### Icon sizes

```
icon-height-small
icon-height-medium
icon-height-large
icon-1x1-small
icon-1x1-medium
icon-1x1-large
```

### Background colors

```
background-color-primary
background-color-secondary
background-color-tertiary
background-color-alternate
```

### Other useful utilities

```
display-inlineflex
z-index-1
z-index-2
align-center
layer
pointer-events-none
pointer-events-auto
overflow-hidden
overflow-scroll
overflow-auto
aspect-ratio-square
aspect-ratio-portrait
aspect-ratio-landscape
aspect-ratio-widescreen
inherit-color
spacing-clean   # sets all margin and padding to 0
```

## Rem conversions (cheat sheet)

| px | rem |
| ---: | ---: |
| 1 | 1px (borders only) |
| 2 | 0.125 |
| 4 | 0.25 |
| 8 | 0.5 |
| 12 | 0.75 |
| 14 | 0.875 (typography) |
| 16 | 1 |
| 24 | 1.5 |
| 32 | 2 |
| 40 | 2.5 |
| 48 | 3 |
| 64 | 4 |
| 80 | 5 |
| 96 | 6 |
| 128 | 8 |
| 192 | 12 |

**Rule:** every rem conversion is a multiple of 16. Convert px to rem by
dividing by 16.

**Exceptions:** 14px = 0.875rem (typography), 2px = 0.125rem (tiny
spacing), 1px = 1px (borders, retina).

**Accessibility:** rem respects browser font size and browser zoom. `px` and
`vw`/`vh` do not.

## Class name patterns

### General-to-specific naming

Within a class name, keywords go from general to specific.

```
text-size-large              # text (general) → size (CSS prop) → large (value)
team-list_headshot-wrapper   # team-list (folder) → headshot (element) → wrapper (role)
```

This powers intelligent search in the Styles panel and clean Folders.

### Custom class (uses underscore)

```
team-list_headshot-wrapper
home-hero_title
nav_component
form_input
section_home
clients-slider_arrow
```

### Utility class (dashes only, no underscore)

```
text-size-large
margin-bottom
padding-global
container-large
button is-secondary
heading-style-h2
```

### Combo class (uses `is-` prefix)

The base class is first. The `is-` variant only works on top of the base.

```
button is-brand
button is-secondary
button is-text
section_home is-dark
section_header is-home
text-size-large is-mobile-small
spacer-large is-home-tabs
```

### Form pattern

```
form_component
form_wrapper
form_block
form_label
form_input
form_submit
```

## Decision flowcharts

### Class type decision

```
Is this CSS property used in many places globally?
├── YES → Utility class (margin-large, text-size-large)
└── NO
    ├── Is it a reusable component? → Custom class (nav_component, clients-slider_component)
    └── Is it one instance only? → Custom class (about-hero_title, footer_copyright-text)
```

### Spacing decision

```
Need equal spacing across a list of siblings?
├── YES → CSS Grid on the parent wrapper
└── NO
    ├── Standard spacing between two elements?
    │   ├── Need responsive overrides → spacer-[size] (one-class block, supports is-)
    │   └── No responsive needs → padding-[direction] padding-[size] (two-class block)
    ├── Spacing for a recurring element (form_input, footer_link) → custom class with margin/padding
    └── One-off unique spacing → custom class with specific margin/padding
```

### Typography decision

```
Does the text match the default H1-H6 / body style?
├── YES → No class. Let the default tag style apply.
└── NO
    ├── Is it a common variation used in many places? → utility class
    │   Examples: text-size-large + text-color-primary + text-weight-semibold
    ├── Is it a "mismatch" between SEO tag and visual size? → heading-style-h#
    │   Example: H1 element + heading-style-h2
    └── Is it specific to one element or a group? → custom class
        Examples: footer_copyright-text, footer_link, faq-template_heading-text
```

### Spacing on a text element

```
DON'T do: H3 + margin-bottom (deep stacks with typography)
DO: H3 alone, then a sibling spacing block (spacer-small) for the gap
```

Spacing classes should not stack directly on a Heading or Paragraph.

## Deep stacking limits

| Classes on an element | Verdict |
| ---: | --- |
| 1 or 2 | Great. Common. |
| 3 | OK, but question whether 3 are needed. |
| 4 | Absolute maximum. Are all 4 really needed? |
| 5+ | Too much. Create a custom class. |

## Output style for the agent

- When suggesting class names, **use the exact CF conventions** (underscore
  for custom, dash-only for utility, `is-` for combo, general-to-specific).
- When generating Webflow project structures, **always include the core
  structure** (`page-wrapper` > `main-wrapper` > `section_[id]` > `padding-global` > `container-[size]`).
- When proposing a spacing solution, **prefer utility spacing first**
  (blocks / wrappers / `spacer-*`) and only fall back to a custom class
  with margin/padding when there is a clear use case.
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

## Deep dive references (GitHub)

For detailed explanations, examples, use cases, and edge cases, fetch the
corresponding reference from GitHub. The agent must support raw URL fetch.

**Base URL:** `https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/`

| Topic | File | Full URL |
| --- | --- | --- |
| Intro, goals, naming mindset | `00-overview.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/00-overview.md |
| Custom / utility / global / combo types, no deep stacking | `01-classes-strategy-1.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/01-classes-strategy-1.md |
| `page-wrapper` / `main-wrapper` / `section_` / `padding-global` / `container-*` / `padding-section-*` | `02-core-structure.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/02-core-structure.md |
| rem math, browser font size, px to rem conversions | `03-sizes-and-rem.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/03-sizes-and-rem.md |
| `heading-style-h#`, `text-size-*`, default HTML tag styles | `04-typography-strategy.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/04-typography-strategy.md |
| Spacing blocks, wrappers, custom class spacing, CSS Grid, `spacer-*` responsive combos | `05-spacing-strategy.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/05-spacing-strategy.md |
| Full catalog of CF utility classes with examples | `06-utility-class-systems.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/06-utility-class-systems.md |
| Custom class creation, deep stacking limits, combo class strategy, no layout system | `07-classes-strategy-2.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/07-classes-strategy-2.md |
| Folders feature (Finsweet Extension), underscore folder system, utility folder system | `08-folders.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/08-folders.md |
| Folder strategies (one vs nested, page-name, reusable, components) | `09-folders-strategy.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/09-folders-strategy.md |
| Color Variables (primitive + semantic tokens), naming, grouping | `10-variables.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/10-variables.md |
| Interaction naming convention `Element [Action State]` | `11-interactions-naming.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/11-interactions-naming.md |
| Fluid Responsive (root-font scaling) | `12-fluid-responsive.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/12-fluid-responsive.md |
| Semantic HTML tags (`<header>`, `<main>`, `<section>`, etc.) | `13-semantic-html.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/13-semantic-html.md |
| Accessibility (keyboard nav, ARIA, focus, alt text) | `14-accessibility.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/14-accessibility.md |
| Global Styles embed snippets | `15-global-styles-embed.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/15-global-styles-embed.md |
| CSS Specificity (why margin classes overwrite, order of creation) | `16-css-specificity.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/16-css-specificity.md |
| Client-First v1 to v2 migration changes | `17-v1-to-v2.md` | https://raw.githubusercontent.com/Omazon/First-Client-Webflow/main/references/17-v1-to-v2.md |

## Source

- All content adapted from Finsweet Client-First documentation:
  https://finsweet.com/client-first/docs
- Original system and concepts by Finsweet. This skill is unofficial.
- Open the [official Cloneable](https://finsweet.info/client-first-cloneable)
  and the [official site](https://finsweet.com/client-first/) for the full
  experience.
- This skill repository: https://github.com/Omazon/First-Client-Webflow
