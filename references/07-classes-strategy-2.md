# Classes strategy 2

Source: https://finsweet.com/client-first/docs/classes-strategy-2

## Custom class creation

Most of a Client-First project will be custom classes. The Styles panel is
Webflow's biggest win — create new classes and apply styles visually, very
quickly.

### Benefits of custom classes

#### 1. Fast creation

In Webflow, we can create classes visually. Don't try to write CSS by hand
when Designer lets us apply it in seconds.

#### 2. Easier and safer to edit

Customizing an instance-specific custom class is fast and safe. Editing a
global utility class affects the whole project.

#### 3. Tablet and mobile responsive updates

Custom classes give free control across breakpoints. With utility classes,
responsive updates need additional utility variants.

#### 4. Working with clients

Client requests are often "random" and don't fit defaults. Custom class use
lets us implement those requests quickly and safely.

## Using global classes

A global class should be simple, powerful, and meaningful.

### Benefits of global classes

1. **Manage styles globally.** A change to `container-large` updates every
   instance.
2. **Faster build time and client convenience.** Utilities like
   `hide-tablet` let us selectively show/hide elements without new classes.

### When to use a global class

Ask:

- Does this style benefit from being managed globally?
- Does it lead to faster build time, efficient recurring styles, or client
  convenience?

If neither, it's not a beneficial global class.

#### Position absolute example

`position-absolute` is not a good global class. Position absolute usually
needs additional properties. There is no meaningful global update to make.

#### Dark section example

`section-dark` IS a good global class. Apply `color: white` and
`background-color: black`. Change `background-color: #000000` to
`#111111` once, and all dark sections update.

## Stacked global classes

> Stacked global classes can help us apply multiple global styles to a
> single element.

### Stack similar classes

Stack margin with margin, padding with padding, typography with typography.
Mixing categories leads to deep stacking.

Examples:

- `margin-top` + `margin-large` — good (margin + margin).
- `text-size-large` + `text-color-neutral` — good (typography + typography).
- `margin-top` + `margin-large` + `max-width-small` — bad (mix of
  categories, hard to swap `margin-large` for a different size without
  removing `max-width-small` first).

### Don't add new styles to stacked global classes

Adding new styles to a stack creates a combo class on top of global
utilities. This defeats the global nature of the utility class.

#### Solutions

1. **Start with a custom class from the beginning.** Build
   `home-header_text` with all the styles baked in. Lose the global link.
2. **Add a combo class for the instance.** Build `text-size-large
   text-color-neutral is-home-header`. The `is-home-header` combo holds
   instance-specific styles. `text-size-large` and `text-color-neutral`
   remain global.

## Combo classes

### What is a combo class?

> A combo class is a variant to a base class. A combo class inherits styles
> from the base class and adds more styles on top of it.

The key difference from a stacked utility: a combo class creates a NEW class
in the CSS file. Stacked global classes do not.

### `is-` prefix

Use `is-` to mark a combo class. Anyone reading the class list knows that
class is meant to be combined.

### Inheriting styles from the base class

> A combo class must have a clear benefit for inheriting styles from the
> base class.

If there's no clear benefit, a single custom class is better.

#### Button example

```
button                       # base — padding, font-size
button is-primary            # variant — primary colors
button is-alternative        # variant — alternative colors
button is-inactive           # variant — disabled state
button is-dark               # variant — dark mode
```

All variants inherit padding and font-size from `button`. Change the base
once, all variants update.

### Combo classes with purpose

#### Unneeded combo class — Container

Tempting to do `container is-large` / `is-medium` / `is-small`. But:

- `margin: 0 auto` and `width: 100%` are properties we never want to change
  on the base class. So there's no benefit to inheriting them.
- The only variable is `max-width`.

Better: create single classes `container-small`, `container-medium`,
`container-large`. Easier to scan in the Navigator.

#### Typography example — inheriting desktop, customizing for mobile

On desktop and tablet, the element follows `text-size-large`. On mobile, it
needs a unique size.

**Option 1 — Custom class from the start:**

```
home-header_text-subtitle {
  font-size: 1.5rem;
  /* ... all the styles ... */
}
```

Loses the global `text-size-large` link.

**Option 2 — Combo class on top of utility:**

```
text-size-large
text-color-neutral
is-home-header   /* holds the mobile override */
```

`text-size-large` and `text-color-neutral` remain global.
`is-home-header` adds the instance-specific mobile styles.

### Use this strategy with other utility classes

```
icon-medium is-footer
button-primary is-nav
heading-medium is-mobile-effect
```

Only create a combo from a global utility when there's a clear purpose.

Don't deep stack! The `is-` combo strategy becomes less effective when there
are many stacked global classes:

```
# Too deep
text-size-large
text-color-primary
text-style-underline
is-testimonials-title
```

## Don't deep stack

### Reasons to not deep stack

1. **Workflow problems in Webflow Styles panel.** Cannot reorder stacked
   classes. Cannot edit early classes on mobile breakpoints without
   removing later classes.
2. **Many steps for small changes.** Deleting a list of classes to edit a
   single early class is time-consuming.
3. **Increased learning curve.** A new developer must understand every
   class in the stack.
4. **Writing CSS in Webflow is fast.** Don't optimize for fewer classes
   when the Styles panel makes custom classes fast.
5. **Tiny CSS savings.** A few KB on the CSS file is not worth the
   workflow cost.

### Deep stack limits

| Classes | Verdict |
| --- | --- |
| 1 or 2 | Great. Common. |
| 3 | OK, but question whether 3 are needed. |
| 4 | Absolute max. Are all 4 really needed? |
| 5+ | Too much. Create a custom class. |

### Strategies to avoid deep stacking

1. **Use one single custom class.** Style the element with one class, no
   stacking.
2. **Nest another Div Block.** Each layer manages a different style. The
   core structure uses this approach (padding separated from max-width
   separated from layout).
3. **Create a combo class.** Group several stacked styles into a single
   `is-` combo.

## No layout system

Client-First does not include flex, grid, column, or layout utility classes.

### Why not?

- Fully global flex/grid utility systems create long stacked lists and
  limit responsive flexibility.
- The same approach as utility spacing would require a massive library of
  classes for every layout option at every breakpoint.
- Clear class names like `flex-a-l-j-c` are unreadable.
- Even `col-2-d col-5-t col-12m` is opaque to anyone who doesn't know the
  system.

### When layout utility classes work

- Use them when truly global. Default 2-column layout → `grid_col-2`.
  Default 3-column layout → `grid_col-3`.
- Use combo classes for instance-specific overrides:
  `grid_col-2 is-specific-instance`.

### Default recommendation

Build layouts with custom classes. Custom classes for layouts let us:

- Build page structures quickly.
- Make future edits quickly.
- Make all responsive customizations.
- Prevent accidental site-wide layout breaking.
- Hand off the project with a minimal learning curve.
