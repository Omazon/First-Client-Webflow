# CSS Specificity

Source: https://finsweet.com/client-first/docs/css-specificity

> CSS Specificity determines which CSS property values are most important to
> an element. If an element has two CSS property values, the one with the
> higher specificity wins, and its property value is applied to the element.

This is not specific to Client-First. It is how CSS works.

> The specificity principle most relevant to Client-First:
> **Classes added to the CSS stylesheet latest will "win" when there are
> CSS property value conflicts.**

## Client-First spacing example

### When the spacing system does NOT work

We copy-paste the spacing system from the official starter project into a
new project:

1. Style Guide page → open Navigator.
2. Copy `fs-styleguide_spacing-directions` folder → paste into new project.
3. Copy `fs-styleguide_spacing-sizes` folder → paste into new project.

The classes are pasted in the wrong order. Adding `margin-bottom` and then
`margin-large` to a div applies a large margin to **all sides** instead of
just the bottom.

### Why this does not work

The size classes were added to the project **after** the direction
classes. They are **more specific** to the project's specificity.

Webflow generates styles in the order they were created. CSS specificity
treats a class created later in the stylesheet as more specific.

`margin-large` was created later, so it overwrites `margin-top`. The
`margin-large` has `margin` applied to all sides, which beats the `0rem`
on the other sides of `margin-top`.

We need `margin-top` to overwrite `margin-large` on all sides. To fix this,
**switch the order of creation**: create the size classes first, then the
direction classes.

### When the spacing system works

#### 1. Use the official Client-First starter project

The [official Client-First starter project](https://webflow.com/website/client-first-cloneable)
has the spacing classes in the correct order.

#### 2. Use Finsweet Extension

Finsweet Extension's Client-First tab copies the spacing system in the
correct order: sizes first, then directions.

#### 3. Manual workflow (copy from starter)

1. Style Guide page → Navigator → open `fs-styleguide_classes` →
   `fs-styleguide_spacing-all`.
2. Copy `fs-styleguide_spacing-sizes` folder → paste into new project.
3. Copy `fs-styleguide_spacing-directions` folder → paste into new project.

Sizes first, then directions.

## CSS Specificity `display: none` example

This has nothing to do with Client-First specifically — CSS specificity
issues can occur in any Webflow project.

1. Create `display-none` (sets `display: none`).
2. Create `background-error` (sets `display: block` and red background).
3. Add `display-none` as a combo class to `background-error`.

Expected: hidden. Actual: still visible. Because `background-error` was
created after `display-none`, it has higher specificity and wins.

### Fixing with Finsweet Extension

The **CSS Styles Reorder** candy in Finsweet Extension reorders classes in
the project CSS file:

1. Open Finsweet Extension → Candies → CSS Styles Reorder.
2. Move `background-error` before `display-none`.
3. Save.

`display-none` is now last in the stylesheet and will overwrite any
display property.

## Key takeaways

- Order of creation matters in Webflow.
- Class added later in the stylesheet wins conflicts.
- Client-First spacing requires sizes to be created before directions.
- Finsweet Extension can fix order issues via CSS Styles Reorder.
- Use `!important` strategically (the Global Styles embed already does for
  utility classes) to force the global behavior.

## Further reading

- [W3 Schools CSS Specificity](https://www.w3schools.com/css/css_specificity.asp)
- MDN CSS Specificity docs
