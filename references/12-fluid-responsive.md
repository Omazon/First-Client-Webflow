# Fluid Responsive

Source: https://finsweet.com/client-first/docs/fluid-responsive

## Tools

Two options:

1. The visual CSS snippet configurator on the Finsweet docs page.
2. The same visual configurator in Finsweet Extension.

## What is fluid responsive?

> As the browser viewport changes size, the design scales with it.

### `vw` / `vh` vs Client-First fluid responsive

Using `vw` or `vh` is one way to scale content. Problems:

- Must set `vw`/`vh` on every element we want fluid.
- Elements quickly become too small or too large due to linear scaling.
- Accessibility suffers — browser zoom does not affect `vw`/`vh`.
- Difficult to manage and maintain in Webflow.

### Root-font scaling (Client-First approach)

> Client-First uses **rem** for all sizes. The rem unit is based on the
> **HTML root font size**.

Everything in the project is relative to the HTML font size. By modifying
this size, all rems scale visually.

The fluid responsive generator runs calculations that modify root font size
according to our preferences. The generated CSS makes the project follow
custom size scaling rules.

### Benefits of root-font scaling

- Use Client-First as usual — no workflow change.
- Optional add-on — apply or skip per project.
- Can be added at the end of the project.
- Browser zoom works normally.
- Browser font size preferences are respected.
- Easier to maintain a `rem` project than a fixed `vw`/`vh` project.

## How to use

1. Visually configure the fluid responsive scaling rules.
2. Copy the generated CSS into the Webflow project (Global Styles embed or
   the page `<head>`).
3. The site now scales fluidly in rems.

## When to use fluid responsive

- Marketing sites with smooth, beautiful scaling across screen sizes.
- Brand-driven sites where the design has continuous values rather than
  jump-cut breakpoints.

## When NOT to use fluid responsive

- Sites with very different layouts per breakpoint. Use discrete Webflow
  breakpoints instead.
- Designs that intentionally have jump-cut behavior.

## Best practice

Combine fluid responsive with the core structure. Apply the scaling to root
font size only. All `container-*`, `padding-*`, `margin-*`, etc. already
inherit from the root font size.

The Global Styles embed can host the generated CSS. Add the CSS to the
embed block on every page, or use Site Settings custom code (head) for the
generated code.

## Live stream references

- Learn it Live #5: explanation of the fluid responsive generator.
- Learn it Live #8: implementing the generator on a PS5 website build.

See Finsweet's site for the videos.
