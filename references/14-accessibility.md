# Accessibility

Source: https://finsweet.com/client-first/docs/accessibility

This page is not specific to Client-First — it covers accessibility inside
Webflow as a platform. Apply these practices in any Webflow project.

## What is accessibility?

> "Accessibility refers to the design of products, devices, services, or
> environments for people who experience disabilities."

In web development:

> "Web a11y means that **anyone** at **any moment** can use your website."

### Why web accessibility matters

A11y is not just for severe disabilities. There are three categories:

1. **Permanently disabled** — blindness, deafness.
2. **Temporarily disabled** — short-term physical or mental impairment.
3. **Conditionally/situational disabled** — slow internet, browsing while
   eating, bright sunlight on a screen.

## Keyboard navigation

Many users rely on the keyboard instead of a mouse.

### Basic controls

#### Tab key

Move focus through focusable elements. `Shift+Tab` reverses direction.

- All elements a mouse user can click must be focusable with Tab.
- All focusable items should have a focus state styled, otherwise the user
  cannot tell what is currently focused.

#### Enter key

When focusing an element, Enter should:

- **[Finsweet solution coming soon]** Activate links or buttons.
- Send forms.

#### Space key

- **[Finsweet solution coming soon]** Activate buttons.
- Activate toggle states (checkboxes, radios, accordions).

#### Arrow keys

- **[Finsweet solution coming soon]** Navigate through grouped children of
  a component (Tab links, Radio buttons, Accordion toggles).
- Change the value of an element (range sliders, number inputs).

#### Esc key

Allow the user to exit states:

- **[Finsweet solution coming soon]** Close a modal.

## Focusability

All clickable elements should be focusable. Use the `tabindex` attribute
when needed:

- `tabindex="0"` — focusable, follows natural order.
- `tabindex="X"` (X > 0) — explicit focus order.
- `tabindex="-1"` — disables focus for a native focusable element with no
  interactivity.

### Programmatic focus

**[Finsweet solution coming soon]**

Programmatically focus an element when a condition is met — for example,
focusing the close button right after opening a modal.

Always think about UX. Don't auto-focus elements that pop up unexpectedly,
like when switching Tabs.

## HTML semantics

### Using `<button>` tags in Webflow

`<button>` triggers actions on the page: expanding/collapsing (accordions),
showing/hiding (hamburger menu, dropdown), or custom app-like functionality.

**Do not confuse `<button>` with Webflow's Button component.** The Webflow
Button component is just an `<a>` tag with styles.

Webflow does not allow using `<button>` directly. To use one, apply a
`<div>` with these attributes:

- `role="button"`
- `tabindex` (to make it keyboard-focusable)
- **[Finsweet solution coming soon]** click event on Enter or Space
- `aria-pressed` for toggle states **[Finsweet solution coming soon]**
- `aria-expanded` for elements that control other elements' visibility
  **[Finsweet solution coming soon]**

### Creating HTML tables in Webflow

`<table>` is not available natively in Webflow. Build accessible tables
with regular Divs and the ARIA table roles:

- `role="table"` — `<table>`
- `role="rowgroup"` — `<tbody>`
- `role="rowheader"` — `<thead>`
- `role="row"` — `<tr>`
- `role="columnheader"` — `<th>`

## Hiding elements

### Hide from screen readers only

Use `aria-hidden="true"` on visual elements that provide no context to
screen readers (styled divs, SVGs).

### Hide from regular users only

Use the visually-hidden CSS technique to hide content visually but keep it
available to screen readers and crawlers. Useful for SVG titles.

```css
.fs-a11y_visually-hidden {
  position: absolute;
  clip: rect(1px, 1px, 1px, 1px);
  clip-path: inset(0px 0px 99.9% 99.9%);
  overflow: hidden;
  height: 1px;
  width: 1px;
  padding: 0;
  border: 0;
}
```

## ARIA

> "Accessible Rich Internet Applications (ARIA) is a set of attributes that
> define ways to make web content and web applications (especially those
> developed with JavaScript) more accessible to people with disabilities."

Webflow's native components (Navbar, Slider, Tabs) already use the correct
ARIA attributes with the required JS.

### ARIA roles

When using semantic HTML elements (`<button>`, `<nav>`, `<a>`, `<input>`),
roles are not needed — the browser and screen reader already understand
their purpose.

Common roles:

- `role="button"` — element acting as a button.
- `role="listbox"` — element with a list of options.
- `role="option"` — single option in a list. Use `aria-selected` too.
- `role="table"`, `role="rowgroup"`, `role="rowheader"`, `role="row"`,
  `role="columnheader"` — table structure.

### ARIA attributes

#### `aria-label`

How an element is announced by a screen reader. Add to elements that have
no content or whose content doesn't describe the action.

#### `aria-labelledby`

Reference another element's ID to provide context.

#### `aria-describedby`

Reference another element's ID as a description.

#### `aria-controls`

Identifies the element(s) controlled by the current element. E.g. the
button that opens a modal has `aria-controls="modal"`.

#### `aria-expanded` **[coming soon]**

State of the controlled element. `true` / `false` set via JS.

#### `aria-haspopup`

Complimentary to `aria-expanded`. Defines what was expanded:

- `"menu"`, `"listbox"`, `"tree"`, `"grid"`, `"dialog"`.

#### `aria-pressed` **[coming soon]**

Toggled state of an element (e.g. switch on/off).

#### `aria-current`

Identifies the "current" item in a set:

- `"page"` — link to the current page.
- `"location"` — current page description (breadcrumbs).
- `"date"` — current date in calendars.
- `"step"` — current step in a multi-step process.

Note: Webflow's `Current` state in Designer only adds `w--current` — it
does NOT add `aria-current`. Add it manually for accessibility.

#### `aria-selected` **[coming soon]**

Marks the currently selected option in a custom selection interface
(custom dropdown, combo box). Set via JS.

#### `aria-hidden` **[coming soon]**

Hides an element from screen readers. Set `aria-hidden="true"`.

## Commonly used components

### Accordions

**Trigger:**

- Use `<div>` with `role="button"` since `<button>` is not natively
  available.
- Add `tabindex` for keyboard navigation. Style the focus state.
- Use `aria-controls` to define the collapsible content.
- **[coming soon]** `aria-expanded` to define the state.

**Content:**

- Should NOT be hidden by default. Rely on JS to hide it on load (so users
  with disabled JS can still see it).
- Use `aria-labelledby` to define the trigger.

## Bad practices

### Not using HTML semantic elements when available

```
# Good
<a href="https://www.google.com">Go to Google</a>

# Bad
<div role="link" onclick="window.location.replace('https://www.google.com')">
  Go to Google
</div>
```

### Adding redundant WAI-ARIA attributes

```html
<!-- This will be read as "Form, Form" -->
<form role="form"></form>
```

## Accessibility cloneable

Finsweet has a cloneable for accessible Filter UI components:
[Accessible Form Filter Components](https://webflow.com/made-in-webflow/website/accessible-form-filter-components).

## Checklist sources

- [A11y Project Checklist](https://www.a11yproject.com/checklist/)
- [Webflow's Accessibility Checklist](https://webflow.com/accessibility/checklist)
