# Utility class systems

Source: https://finsweet.com/client-first/docs/utility-class-systems

The utility classes included with the official Client-First cloneable. They
are not specific to any website, design, or style. They manage important
CSS properties used throughout pages, sections, or elements.

**All included utility styles are optional.** Adapt to the project. Most
projects work very well with the included classes.

## Most important utility systems

Three primary global systems come with Client-First:

1. **Core structure** — see `references/02-core-structure.md`.
2. **Typography** — see `references/04-typography-strategy.md`.
3. **Spacing** — see `references/05-spacing-strategy.md`.

## Structure

### Global horizontal padding

- `padding-global`

### Container size

- `container-large`
- `container-medium`
- `container-small`

### Section padding

- `padding-section-small`
- `padding-section-medium`
- `padding-section-large`

Apply to the same div as `padding-global` to reduce nesting.

## Typography

### HTML tag default styles

Style globally: `body`, `h1`-`h6`. No class needed for default text.

### Heading style switch

- `heading-style-h1`
- `heading-style-h2`
- `heading-style-h3`
- `heading-style-h4`
- `heading-style-h5`
- `heading-style-h6`

### Text size

- `text-size-large`
- `text-size-medium`
- `text-size-regular`
- `text-size-small`
- `text-size-tiny`

### Text style

- `text-style-allcaps`
- `text-style-italic`
- `text-style-link`
- `text-style-muted`
- `text-style-nowrap`
- `text-style-quote`
- `text-style-strikethrough`
- `text-style-2lines`
- `text-style-3lines`

### Text weight

- `text-weight-xbold`
- `text-weight-bold`
- `text-weight-semibold`
- `text-weight-normal`
- `text-weight-light`

### Text alignment

- `text-align-left`
- `text-align-center`
- `text-align-right`

### Text color

- `text-color-primary`
- `text-color-secondary`
- `text-color-alternate`

### Buttons

- `button`
- `button is-secondary`
- `button is-text`

## Spacing

### Margin direction

- `margin-top`
- `margin-bottom`
- `margin-left`
- `margin-right`
- `margin-horizontal`
- `margin-vertical`

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

- `padding-top`
- `padding-bottom`
- `padding-left`
- `padding-right`
- `padding-horizontal`
- `padding-vertical`

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

### Remove all spacing

- `spacing-clean` — sets all margin and padding to 0. Useful for removing
  native Webflow component spacing.

## Useful utility systems

### Responsive hide

- `hide` — hide on all devices.
- `hide-tablet` — hide from tablet resolution.
- `hide-mobile-landscape` — hide from mobile landscape.
- `hide-mobile-portrait` — hide from mobile portrait.

### Display inline flex

- `display-inlineflex` — sets `display: inline-flex`. Useful for buttons
  with `display: flex` that would otherwise take 100% of the space.

### Max width

Use `container-*` for primary outer max-widths. Use `max-width-*` for
nested max-widths.

- `max-width-xxlarge` — 80rem
- `max-width-xlarge` — 64rem
- `max-width-large` — 48rem
- `max-width-medium` — 32rem
- `max-width-small` — 20rem
- `max-width-xsmall` — 16rem
- `max-width-xxsmall` — 12rem

#### Max width full

- `max-width-full` — sets `max-width: none`.
- `max-width-full-tablet` — sets `max-width: none` on tablet.
- `max-width-full-mobile-landscape` — sets `max-width: none` on landscape.
- `max-width-full-mobile-portrait` — sets `max-width: none` on portrait.

### Icon sizes

- `icon-height-small`
- `icon-height-medium`
- `icon-height-large`
- `icon-1x1-small` — both width and height
- `icon-1x1-medium`
- `icon-1x1-large`

### Background colors

- `background-color-primary`
- `background-color-secondary`
- `background-color-tertiary`
- `background-color-alternate`

### Other useful utilities

- `z-index-1` — sets `z-index: 1`.
- `z-index-2` — sets `z-index: 2`.
- `align-center` — sets `margin-left` and `margin-right` to `auto`.
- `layer` — sets `position: absolute` with 0% on all sides. Expands to the
  full size of the (positioned) parent.
- `pointer-events-none` — disables click/hover.
- `pointer-events-auto` — re-enables click/hover.
- `overflow-hidden` — sets `overflow: hidden`.
- `overflow-scroll` — sets `overflow: scroll`.
- `overflow-auto` — sets `overflow: auto`.
- `aspect-ratio-square` — `aspect-ratio: 1 / 1`.
- `aspect-ratio-portrait` — `aspect-ratio: 2 / 3`.
- `aspect-ratio-landscape` — `aspect-ratio: 3 / 2`.
- `aspect-ratio-widescreen` — `aspect-ratio: 16 / 9`.
- `inherit-color` — sets `color: inherit` on all children. Use when a child
  has been linked to a semantic color and we want to inherit from the
  parent.

## Spacer system (new in V2)

Empty Div Block that creates space between sibling elements.

- `spacer-tiny` — 0.125rem
- `spacer-xxsmall` — 0.25rem
- `spacer-xsmall` — 0.5rem
- `spacer-small` — 1rem
- `spacer-medium` — 2rem
- `spacer-large` — 3rem
- `spacer-xlarge` — 4rem
- `spacer-xxlarge` — 5rem
- `spacer-huge` — 6rem
- `spacer-xhuge` — 8rem
- `spacer-xxhuge` — 12rem
- `spacer-custom1` — 1.5rem
- `spacer-custom2` — 2.5rem
- `spacer-custom3` — 3.5rem

Add an `is-` combo class for responsive variants:
`spacer-large is-mobile-small`.

## Global embed

Client-First comes with a symbol embed block holding global site-wide
custom CSS. The embed block goes on every page.

Place the CSS in a Designer embed (not Page Settings or Site Settings) so
the styles are visible in the Designer canvas.

The Global Styles embed includes snippets for text clarity, focus state,
Rich Text margin cleanup, container centering, and `!important` declarations
for the utility spacing system. See `references/15-global-styles-embed.md`
for the full list.
