# Classes strategy 1

Source: https://finsweet.com/client-first/docs/classes-strategy-1

## Types of classes

### Utility class

> A class created with a specific combination of CSS properties that can be
> applied to elements globally across the project.

All utility classes are global classes. A utility helps apply global CSS
properties inside the project.

Examples: `background-color-primary`, `font-size-large`, `text-color-secondary`.

**Utility classes do not use an underscore in the class name.**

### Custom class

> A custom class created for a specific component, page, grouping of
> elements, or single element.

Custom because it is custom outside of the project's utility classes. Created
when utility classes can not or should not be used on an element. The class
is custom to that element.

Examples: `about-team_component`, `footer_column`, `clients-slider_arrow`,
`nav_link`, `home-header_texture`, `header_background-layer`,
`testimonial-slider_headshot`.

**Custom classes use an underscore in the class name.**

#### Form example

```
form_component
form_wrapper
form_block
form_label
form_input
form_submit
```

### Global class

> A classification of a class. A global class is intended for use across the
> entire project. Both utility and custom classes can be global classes.

A global class applies styles that will remain unified across the project.

- All utility classes are global. `margin-large` is a global controller:
  change its value and every instance updates.
- A custom class can also be global. `faq_item`, `header_content`,
  `clients-slider_arrow` — used in many places, managed globally.

If we intend to use the class throughout the website, it is considered
global.

### Combo class

> A combo class is a variant to a base class. A combo class inherits styles
> from the base class and adds more styles on top of it.

The "base class" is the first class in the stacked combo class. The added
class is the variant. The variant uses the `is-` prefix.

The stacked combo class will only work when combined with the base class. It
does not work alone.

```
button              # base
button is-brand     # combo: button base + is-brand variant
section_header      # base
section_header is-home
```

Combo classes can be created from custom or utility base classes.

## Don't deep stack

> **Deep stack** — many classes 'stacked' on top of an element.
> **Deep stacking** — the action of stacking many classes on top of an
> element.

Client-First does not recommend deep stacking in Webflow.

### Reasons to not deep stack

#### 1. Inability to reorder styles in the Designer styles panel

Classes cannot be reordered or freely managed in Webflow. To change an
earlier class in the list, you have to remove all classes after it.

This problem becomes extreme on lower breakpoint levels.

#### 2. Slower workflow

Many steps for small changes. Constant practice makes build and maintenance
time longer.

#### 3. Increased learning curve

Deeper requirement for understanding what the classes do and how to manage
them.

#### 4. Writing CSS in Webflow is fast

CSS can be written visually in the Webflow Styles panel. Take advantage of
it; don't fight it with class stacking.

#### 5. CSS size savings are not significant

Saving a few KB on the CSS file is not worth the workflow cost.

## Use custom classes

Custom classes are a powerful and recommended method inside Client-First.

Use them to:

1. Make easy edits to specific elements.
2. Avoid using utility classes **everywhere** in the project.
3. Avoid deep stacking.

### Background texture example

Don't stack `background-absolute` + `fit-size` + `opacity-low` for a
texture. Create a custom class:

```
services-item_background-texture
```

Now edits are quick and a custom class is ready to accept unique styling.

## Naming convention

Create clear and specific names. A Webflow developer, client, or anyone
should understand what a class is doing based on a class name alone.

### Meaningful names and keywords

A strong keyword gives us context. Each class name should serve a
meaningful purpose.

### General to specific within a class name

| Wrong | Right | Why |
| --- | --- | --- |
| `large-size-text` | `text-size-large` | Enables Folders, intelligent search |
| `wrapper-headshot-team-list` | `team-list_headshot-wrapper` | Folder organization |

### Sample class family

```
team-list_headshot-wrapper
team-list_headshot-image
team-list_headshot-texture-layer
team-list_headshot-background
```

General (`team-list`) → specific (`headshot`) → specific (`wrapper` /
`image` / `texture-layer` / `background`).
