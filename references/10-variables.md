# Variables (Colors)

Source: https://finsweet.com/client-first/docs/variables

> ⚠️ Size variables are not released because there is no breakpoint feature
> on the Webflow variables panel. When Webflow releases breakpoints, Finsweet
> will revisit. For now, this page is about **color variables** only.

## Benefits of color variables

### Consistency

Defining a color once and using it in many places maintains a consistent
look and feel — crucial for brand identity and UX. Variables give us a
curated list of available options to choose from.

### Ease of maintenance

If a color needs to change, update it once in the Variables panel. Every
usage updates automatically. Reduces errors.

### Theming (future)

Variables simplify theming, including dark/light modes, when Webflow
releases modes. Switch a set of color variables to change the theme.

### Improved readability

`var(--primary-color)` is much more readable than `#FF5733`.

### Context for usage

Semantic tokens describe how the color is used. If we need a text color for
a heading, we find the "Text Color" variables section.

## Primitive tokens

> Primitive tokens, represented by base colors, are the foundational
> building blocks of a design system's color palette.

Identified by the prefix **- Base Color:**

### How to use primitives

In practice, primitives feed semantic variables. Avoid linking primitive
colors directly to classes unless there is a strong reason.

### How to group primitives

Client-First starts with three groups:

- Brand colors
- Neutral colors
- System colors

Every project is different. Rename and regroup as needed.

### How to name primitives

Client-First starts with color names plus a small number of shades:

```
-base-color-brand-red
-base-color-brand-blue
-base-color-neutral-100
-base-color-neutral-200
-base-color-neutral-900
-base-color-system-error
-base-color-system-success
```

If this doesn't fit, alternatives include numeric scales
(`-base-color-red-100` through `-base-color-red-900`) or functional names.

## Semantic tokens

> Semantic tokens are variables where the name describes the purpose or
> meaning of the color within the design rather than the color itself.

All variables that do not contain the prefix **- Base Color** are semantic
tokens.

### How to use semantic tokens

Use semantic tokens to style elements per their purpose:

- **Background color** → use the Background Color semantic tokens.
- **Text color** → use the Text Color semantic tokens.
- **Border color** → use the Border Color semantic tokens.

#### Use semantic tokens as utility classes

Every semantic token can be used as a utility class. Client-First starts
with these utility classes linked to semantic tokens:

```
background-color-primary        -> var(--background-color--background-primary)
background-color-secondary      -> var(--background-color--background-secondary)
background-color-tertiary       -> var(--background-color--background-tertiary)
background-color-alternate      -> var(--background-color--background-alternate)
text-color-primary              -> var(--text-color--text-primary)
text-color-secondary            -> var(--text-color--text-secondary)
text-color-alternate            -> var(--text--text-alternate)
```

#### Avoid linking a text element base tag directly to a semantic variable

Linking a color directly to a text element loses the ability to inherit the
color from the parent. To override and inherit, use the
`inherit-color` utility class:

```
inherit-color * {
  color: inherit;
}
```

### How to name semantic tokens

Use the convention:

```
[element] - [style] - [identifier]
```

Examples:

```
background - color - dark
text       - color - primary
border     - color - brand
```

Questions to ask:

- **Element:** What is it being added to? (background, text, border)
- **Style:** What value is changing? (color, opacity)
- **Identifier:** What identifier describes this variable? (primary,
  secondary, brand, dark, light)

### Don't name a semantic variable by its color

If we name a variable by its color, any theme change requires renaming the
token. Semantic names abstract the design from specific color values.

### Naming for future theming

Names must be generic enough to accommodate light/dark mode. Avoid
including the color in the name.

### Primary and alternate concept

Set the default theme as a reference point.

- If `background-color--background-primary` is black, then
  `background-color--background-alternate` is the inverse (white).
- If `text-color--text-primary` is white, then `text-color--text-alternate`
  is black — for use on white backgrounds.

## FAQ

### Follow the client's color system?

Yes. If the client has an established style guide, follow it. Consistency
and brand alignment matter.

### What if the design file is a mess?

Happens often. Organize the colors using the primitive/semantic token
convention.

### Can I name a semantic variable by color?

No. Use names that describe the role, not the color value.

### How do I know which variables are primitives?

Primitive tokens are identified by the prefix **- Base Color.**

### How do I link variables with utility classes?

Create utility classes that reference color variables. Always use semantic
tokens. Use clear, descriptive naming.

## Suggested full naming pattern

Primitives (raw colors):

```
-base-color-brand-red
-base-color-brand-blue
-base-color-brand-green
-base-color-neutral-white
-base-color-neutral-black
-base-color-neutral-100
-base-color-neutral-900
-base-color-system-error
-base-color-system-success
-base-color-system-focus-state
```

Semantic (purpose-driven):

```
--background-color--background-primary
--background-color--background-secondary
--background-color--background-tertiary
--background-color--background-alternate
--text-color--text-primary
--text-color--text-secondary
--text-color--text-alternate
--border-color--border-primary
--border-color--border-secondary
--border-color--border-brand
```
