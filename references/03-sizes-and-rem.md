# Sizes and rem

Source: https://finsweet.com/client-first/docs/sizes-and-rem

Webflow defaults to `px`. Client-First uses `rem`. Select `rem` in the unit
dropdown of any Designer input.

## What is rem?

**rem** stands for "root em".

- Rem is a relative unit based on the `<html>` element's `font-size`.
- The root element is `html`.
- Most sizes applied in Client-First are in rem.

## The math

Browsers default to `16px` for the `html` font-size. **`1rem = 16px`** at
default browser settings.

Every rem conversion is a multiple of 16.

| px | rem |
| ---: | ---: |
| 2 | 0.125 |
| 4 | 0.25 |
| 8 | 0.5 |
| 12 | 0.75 |
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

To convert: divide px by 16. To go the other way: multiply rem by 16.

### Calculation in Webflow Designer

Inside most unit inputs, type the math directly: e.g. `100/16rem` in a width
input to get the rem value calculated.

## Recommended px-to-rem values

Client-First approved values are a recommendation, not a strict requirement.
Prefer easily readable rem values: `0.25`, `0.5`, `1`, `1.5`, `2`, `2.5`, `3`,
`4`, `5`. Avoid long, hard-to-remember values like `8.4375rem`.

### Three exceptions

1. **Typography:** 14px = 0.875rem. 12px is often too small for typography.
2. **2px spacing:** 2px = 0.125rem. Use for tiny spacing.
3. **1px is 1px:** for borders, use `1px`, not rem. Retina devices have
   different scaling rules; using `1px` produces a 1px line on any device.

## Accessibility benefits

### Browser font size

Browsers let users change the default font size. Client-First's rem system
adapts to that. With `px` or `vw`, we ignore the user's preferences.

### Browser zoom

Rem respects browser zoom. Layout and content zoom with the user. With
`vw`/`vh`, browser zoom does not work because they depend on viewport size
only.

## Migrating a px project to rem

The Finsweet Extension's **PX to REM Migrator** (under the Client-First tab)
converts every value in a project from px to its computed rem value.

## Conversions cheat sheet

```
1px  = 1px       (borders only — keep as px)
2px  = 0.125rem  (tiny spacing)
4px  = 0.25rem
8px  = 0.5rem
12px = 0.75rem
14px = 0.875rem  (typography exception)
16px = 1rem
24px = 1.5rem
32px = 2rem
40px = 2.5rem
48px = 3rem
64px = 4rem
80px = 5rem
96px = 6rem
128px = 8rem
192px = 12rem
```
