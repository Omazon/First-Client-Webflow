# Spacing strategy

Source: https://finsweet.com/client-first/docs/spacing-strategy

Spacing strategy has two parts: **utility classes** and **custom classes**.
Each has strategies within it.

## Part 1: Utility classes

### Spacing block strategy (Option 1)

> A "spacing block" is an empty Div Block that creates space between two
> sibling elements.

```
# Empty Div Block
spacer-large
```

Add content elements as siblings of the spacing block. The block creates
space (padding) between elements.

### Spacing block strategy (Option 2)

```
# Empty Div Block
padding-bottom
padding-medium
```

Apply the direction class + size class.

#### Option 1 vs 2?

- `spacer-*` uses one class.
- `padding-[direction]` + `padding-[size]` uses two classes.

The decision is up to the developer. One benefit of `spacer-*` is the option
to add responsive variants (see `Responsive spacing` below).

### Spacing wrapper strategy

> A "spacing wrapper" is a Div Block that wraps a child element and creates
> space between a sibling element.

```
# Div Block with content inside
margin-bottom
margin-medium
```

or

```
padding-top
padding-large
```

Nest the content element inside the spacing wrapper. The wrapper creates
space between itself and a sibling.

## Use cases for utility spacing

### 1. Default global spacing values

- **Consistency.** Unified spacing across sections and pages.
- **Automatic breakpoint updates.** Blocks and wrappers auto-apply unified
  spacing on tablet and mobile.
- **Global site-wide updates.** Change one utility class, update everywhere.

### 2. Workflow and scalability benefits

- Reduces custom classes for margin/padding.
- Avoids deep stacking.
- Faster workflow when used correctly.

#### It's not required to use utility spacing everywhere.

Apply margin/padding directly to custom classes when it makes more sense.
Use cases below.

### 3. Spacing typography and buttons

For an H3 + Paragraph + Button layout, use spacing blocks or wrappers to
create space between each text element. Avoid stacking spacing classes on
the text element itself.

### 4. Spacing for reused symbols and components

Apply spacing outside the symbol with blocks/wrappers so different
instances can have different spacing. No combo class, no new custom class.

## Spacing block use cases

### 1. Create space between two elements

Fast to implement, fewer nested levels, more visible in Navigator.

### 2. See children in Navigator

Spacing blocks create a clear view in Navigator. Wrappers can hide
elements inside nested folders. Blocks show elements more visibly.

### 3. Unique spacing for top and bottom of sections

When a section's top and bottom padding should be different, while keeping
the global utility system: use one size on top, another on bottom.

## Spacing wrapper use cases

### 1. Use with CSS Grid spacing strategy

When CSS Grid creates equal space between children, use a wrapper to create
unique spacing for one element in the list. Example: a list of items with
1rem between each child — except the last item, which gets a different
margin-top.

## Are empty divs bad for the website?

No. As long as the empty divs don't have any content or accessibility
attributes (like `aria-label`), screen readers will omit them. Search
engines will not be confused. The "Excessive DOM size" alert is more likely
caused by animations, Lottie files, or embeds than by Client-First spacing.

## Part 2: Custom classes

### Custom class on element strategy

Apply margin and padding values directly to the custom class.

```
faq_title {
  margin-bottom: 0.75rem;
}
```

Most flexible. Total control of a specific element across all breakpoints.
Overuse creates too many custom classes for spacing.

### CSS Grid strategy

Apply CSS Grid to a parent wrapper to create space for the children inside.

```
.benefits_list {
  display: grid;
  grid-row-gap: 1rem;
}
```

Instead of applying many blocks, wrappers, or custom classes on elements in
a list, use CSS Grid to manage all children with one controller — the parent
wrapper.

#### Use case: list items

Equal space between sibling elements. One adjustment to the parent class
adjusts all children.

#### Use case: content card

Apply CSS Grid to a content card to space icon, title, paragraph inside it.
Adjust the CSS Grid row values and all cards update together.

If a card has a CTA with a different spacing, use a spacing wrapper to add
the unique spacing inside the grid.

## Custom class on element — use cases

### 1. Globally manage the spacing of a specific element

When an element recurs many times in the project, use a custom class.

Ask:

- How many instances of this element exist in the project?
- How do we want to manage each instance?

If many instances, use a custom class. Example: `form_input` with
`margin-bottom: 1rem`. Change one class, every form input updates.

### 2. Unique tablet and mobile spacing sizes

When an element needs unique spacing on tablet, mobile, or both, apply
spacing directly to the custom class. Utility spacing unifies across
breakpoints; custom spacing is for variation.

### 3. Unique one-off spacing

When the spacing doesn't fit any utility class, create a one-off custom
class. Example: `about_testimonial-title` with `margin-bottom: 2.25rem`.

Use sparingly. One-off custom classes reduce the global unity of the
project.

## CSS Grid spacing — use cases

### 1. Spacing children in a list

Equal space between siblings. One controller (the parent wrapper) manages
all.

```
# Footer links
.footer_links-column {
  display: grid;
  grid-row-gap: 1rem;
}
```

## Responsive spacing

The `spacer-*` class system uses only one class, so it accepts an `is-`
combo class for responsive variants.

```
spacer-large is-mobile-small    # desktop: large space, mobile: small space
spacer-large is-home-tabs       # specific element
```

Two-class strategies (margin + size) already use two classes. Adding a
third starts to deep-stack. Responsive variants on two-class strategies are
discouraged.

## Spacing tips

### `padding-section-[size]`

`padding-section-[size]` manages top and bottom padding for sections
globally. Apply to the same div as `padding-global` to reduce nesting.

```
section_home
+ padding-global
+ padding-section-medium
```

A `section-` folder is added to the `padding-` utility class folder:
`padding-section-small`, `padding-section-medium`, `padding-section-large`.

For unique section padding:

- **Recommended:** use spacing blocks on top and bottom of the section.
- Or apply the unique padding to `section_[identifier]`.

### Optional margin on Heading tags

Add a `margin-bottom` to Heading tags to unify spacing above and below
across the project. Example: every H2 has `margin-bottom: 2rem`.

Skip this if the design has many Heading variations. Forcing a uniform
margin will create overrides and more work.

### Flex or grid for buttons and button rows

- **Button with icon:** apply flex or grid to the button to space the text
  and the icon inside.
- **Button row:** apply flex or grid to the parent wrapper to space
  buttons horizontally.

Don't apply `margin-right` to the `button` class itself. It limits where the
button can be used. Spacing blocks are bad for mobile button rows. Use
flex/grid on the parent.

### Avoid utility padding to create size for inner elements

Don't use utility padding classes to create padding around item content.
This encourages deep stacking and mobile conflicts. Instead, apply inner
padding to the custom class.

### Create a custom class folder of spacers

Use `spacer_` (with underscore) as a custom folder for managing all custom
unique spacings across the project.

```
spacer_header
spacer_sticky-nav
spacer_title-primary
spacer_title-subtitle
spacer_footer
spacer_home-faq
```

## Decision flowchart

1. **Need equal, repeated space across a list or section?**
   → CSS Grid on the parent.
2. **Need standard spacing between two elements (responsive-friendly)?**
   → `spacer-[size]` empty div.
3. **Need standard spacing between two elements (no responsive need)?**
   → `padding-[direction] padding-[size]` empty div.
4. **Need spacing around a specific element (one-off, mobile variation)?**
   → Margin/padding on the custom class.
5. **Need global spacing for a recurring element (form input, button row)?**
   → Margin/padding on the custom class with underscore folder.
