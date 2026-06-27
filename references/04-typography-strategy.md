# Typography strategy

Source: https://finsweet.com/client-first/docs/typography-strategy

## HTML tags are default

Typography should be the simplest and most organized utility system. HTML
typography tags are the default typography values.

Style these HTML tags globally:

- `body`
- `h1`, `h2`, `h3`, `h4`, `h5`, `h6`

In a perfect world, no class is needed on a Heading or Text Element. Class
only when there is a variation from the default.

## Utility classes to customize the default

Client-First comes with a global utility class system for typography. Use
`text-` and `heading-` as prefixes.

### Benefits of the system

1. **Global management.** Change one value, update site-wide typography.
2. **Prevents duplicate classes.** Reuse styles via utility classes instead
   of creating many custom classes for the same color/size.
3. **Workflow speed.** Search the Styles panel by prefix (`text-` or
   `heading-`) to find classes fast.

## When to customize the default

### 1. Variation in style

Most common reason. Apply one or more utility classes to the text element.

```
H3 element
+ text-color-primary
+ text-weight-semibold
```

### 2. SEO tag vs design tag mismatch

When the SEO tag and the visual style don't match, use `heading-style-h#` to
change the style without changing the tag.

```
H1 (for SEO) + heading-style-h2  # visually an H2, semantically an H1
```

`heading-style-h#` does NOT change the HTML tag. It only changes the CSS.

`heading-style-h#` should be used sparingly. Most Headings should have no
class.

### 3. Avoid using a Heading tag for non-Headings

Don't force a Heading tag on something that isn't a Heading. Use a Text
Element + a custom class instead, e.g. for "Featured price: $99".

## Customizing the typography system

The Client-First starter is a starting point, not a final system. Update
the styles per project, and consider adding new utility classes for new CSS
properties (e.g. `text-opacity-low`, `text-opacity-medium`).

### Create a new utility class to avoid deep stacking

If a recurring combination of stacked typography classes is used many times,
group them into a single utility class to keep the global system intact.

```
# instead of stacking many text-* classes on every instance
text-style-subtitle
```

But be careful: too much grouping breaks the global control. If
`text-size-large` is consumed into `text-style-subtitle`, future updates to
`text-size-large` must be applied to both.

## When to create a custom class instead

The utility system will not work for every use case. Create a custom class
when:

- The text is unique and specific.
- A particular grouping of text needs to be managed as a group.
- The text needs custom responsive default overrides.

### Examples

#### Unique and specific text

```
footer_copyright-text
```

For copyright: very small, special grey, all-caps, different styles across
breakpoints. Specific identifiable element.

#### Manage a particular grouping of text

```
footer_link
```

Applied 8 times in the footer. Change the size once, all update.

#### Customize responsive default

```
faq-template_heading-text
```

H1 follows the default on desktop and tablet, but a long string requires a
size reduction on mobile. Use a custom class to apply the responsive size
override.

## Built-in typography utility classes

Reference (full catalog in `references/06-utility-class-systems.md`):

### Heading style switch

```
heading-style-h1
heading-style-h2
heading-style-h3
heading-style-h4
heading-style-h5
heading-style-h6
```

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
