# Global Styles embed

Source: https://finsweet.com/client-first/docs/global-styles-embed

The Global Styles embed is a symbol embed block that holds global
site-wide custom CSS. It is included with the Client-First cloneable and
should be placed on every page.

> Place CSS in a Designer embed, not Page Settings or Site Settings. The
> embed lets us see the CSS inside the Designer canvas, not just on the
> published site.

Below are the snippets from the embed, what they do, and when to use them.

## Text clarity

Makes text look crisper and more legible in all browsers.

```html
<style>
  body {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-smoothing: antialiased;
    text-rendering: optimizeLegibility;
  }
</style>
```

## Focus state for keyboard navigation

Unified "selected effect" for all focusable elements. Targets elements with
`tabindex` and the file input.

```html
<style>
  *[tabindex]:focus-visible,
  input[type="file"]:focus-visible {
    outline: 0.125rem solid var(--base-color-system--focus-state);
    outline-offset: 0.125rem;
  }
</style>
```

The outline color comes from the `--base-color-system--focus-state`
primitive token. Override per element with the Webflow "Focused (keyboard)"
state.

## Rich Text top margin removal

Removes the top margin from the first element in any Rich Text.

```html
<style>
  .w-richtext > :not(div):first-child,
  .w-richtext > div:first-child > :first-child {
    margin-top: 0 !important;
  }
</style>
```

For example, an H2 inside a Rich Text might have `margin-top: 4rem`. The
snippet removes the margin only for the first element so there is no
unwanted space at the top of the Rich Text block.

## Rich Text bottom margin removal

Removes the bottom margin from the last element in any Rich Text.

```html
<style>
  .w-richtext > :last-child,
  .w-richtext ol li:last-child,
  .w-richtext ul li:last-child {
    margin-bottom: 0;
  }
</style>
```

For example, Paragraph might have `margin-bottom: 0.5rem`. The snippet
removes the margin for the last element so there is no extra space at the
bottom of the Rich Text block.

## Container centerizer

Forces horizontal centering of all container sizes, protecting against
accidental margin changes.

```html
<style>
  .container-medium,
  .container-small,
  .container-large {
    margin-right: auto !important;
    margin-left: auto !important;
  }
</style>
```

## Inherit color from parent element

Override a linked text color and inherit from the parent.

```html
<style>
  .inherit-color * {
    color: inherit;
  }
</style>
```

Apply `inherit-color` to an element whose children have a linked semantic
color but should inherit the parent color.

## !important declarations for utility classes

Prevents CSS specificity issues for display, padding, and margin utility
classes. Forces them to maintain global style controls.

```html
<style>
  .hide { display: none !important; }
  .margin-0 { margin: 0rem !important; }
  .padding-0 { padding: 0rem !important; }
  .margin-top { margin-right: 0rem !important; margin-bottom: 0rem !important; margin-left: 0rem !important; }
  .padding-top { padding-right: 0rem !important; padding-bottom: 0rem !important; padding-left: 0rem !important; }
  /* ... and the rest of margin/padding directions ... */

  /* Responsive hide with !important */
  @media screen and (max-width: 991px) {
    .hide, .hide-tablet { display: none !important; }
  }
  @media screen and (max-width: 767px) {
    .hide, .hide-tablet, .hide-mobile-landscape { display: none !important; }
  }
  @media screen and (max-width: 479px) {
    .hide, .hide-tablet, .hide-mobile-landscape, .hide-mobile { display: none !important; }
  }
</style>
```

Full snippet in the cloneable. The `!important` ensures utility classes
behave as true globals.

## Inherited styles for Webflow elements (advanced, off by default)

```html
<style>
  .hide { display: none !important; }
  @media screen and (max-width: 991px) {
    .hide, .hide-tablet { display: none !important; }
  }
  @media screen and (max-width: 767px) {
    .hide-mobile-landscape { display: none !important; }
  }
  @media screen and (max-width: 479px) {
    .hide-mobile { display: none !important; }
  }
  .margin-0 { margin: 0rem !important; }
  /* ... full direction set ... */
</style>
```

This snippet makes styling for some Webflow elements easier. Instead of
manually overriding hardcoded styles, we can inherit from the parent. For
example, Webflow form inputs are hardcoded to 14px — this snippet removes
the hardcode so they inherit the body font-size.

**Disabled by default.** Why? It can cause unexpected behavior. For
example, "All links" no longer responds to global color updates because the
hardcoded values are replaced with inherit.

## Custom CSS additions

Use the Global Styles embed for custom CSS that:

- Needs to be visible inside the Designer canvas.
- Is shared across the project.
- Should not be a one-off in Page Settings.

For page-specific CSS, use Page Settings custom code. For the entire site,
use Site Settings custom code (head).
