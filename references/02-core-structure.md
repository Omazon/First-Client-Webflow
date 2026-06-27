# Core Structure strategy

Source: https://finsweet.com/client-first/docs/core-structure-strategy

A set of classes and principles to create a strong HTML base around page
content. Small sites, big sites, beginner sites, and advanced sites use the
same structure.

The core structure is "layers" of Div Blocks surrounding page content. Each
layer has a specific use.

## The 6 core structure classes

```
page-wrapper
└── main-wrapper   (HTML tag: <main>)
    └── section_home       (HTML tag: <section>, uses section_[identifier])
        └── section_about
            ├── padding-global
            │   └── container-large
            │       └── padding-section-large
            │           └── (content)
            └── ...
```

### 1. `page-wrapper`

Outermost parent of all elements on the page. Wraps every element.

- **Styles:** optional. Should not be heavily styled.
- **Use cases:**
  - Copy-to-clipboard the entire page to paste into a different page.
  - Site-wide global class (e.g. `overflow: hidden` to prevent horizontal
    scroll — but be aware this also disables CSS sticky on nested elements).
  - Avoid applying classes and unique styles directly to the `<body>` tag.
    Limit body styles to typography and `background-color`. Use
    `page-wrapper` for everything else.

### 2. `main-wrapper`

The main content of the page. Wrap all or most content sections in a
**`<main>`** HTML tag.

- The nav and footer should NOT be inside `<main>`.
- **Styles:** optional.
- **Use case:** accessibility best practice — screen readers and search
  engines identify the main content.

### 3. `section_[identifier]`

Wraps an entire section of content. Set the HTML tag to **`<section>`**.

- Primary use: better workflow inside Webflow Designer. Organizes the
  Navigator panel. Anchor-scrolls the section when clicked in Navigator.
- Gives the client a clear sitemap view of the page.
- All section classes live in the `section_` folder.

#### Naming

```
section_home
section_about
section_how-it-works
section_testimonials
section_contact
section_pricing
section_cta
section_footer  # only if you keep a separate page footer
```

#### Styles

Avoid applying styles if possible. If a global style is needed across
sections (e.g. a dark variant), create an add-on class:

```
section_home section-style-dark
```

`section-style-dark` holds `color: white`, `background-color: black` and
acts as a global add-on.

### 4. `padding-global`

Global horizontal spacing. Manages left and right padding of page content.

- Only `padding-left` and `padding-right` on this class. No other properties.
- Unified site-wide left/right padding.
- Global controller to manage entire website's universal left/right padding.

#### Default implementation

```
main-wrapper
└── section_[identifier]
    └── padding-global
        └── container-large
            └── (content)
```

`padding-global` is decoupled from `container-*` so they can be used
independently. We can put `padding-global` as a parent of the container, a
child of the container, or both.

### 5. `container-[size]`

A unified global container system. Centered with `margin: 0 auto`,
`width: 100%`, and a `max-width`.

Built-in sizes:

| Class | Default max-width |
| --- | --- |
| `container-small` | ~48rem |
| `container-medium` | ~64rem |
| `container-large` | ~80rem |

Values are editable. Add or remove sizes as needed.

Use for centering and setting unified max-width across the project. For
nested max-width, use the `max-width-*` utility classes instead (see
`references/06-utility-class-systems.md`).

### 6. `padding-section-[size]`

A unified global vertical spacing system for sections. Creates top and
bottom padding inside a section.

Built-in sizes: `padding-section-small`, `padding-section-medium`,
`padding-section-large`.

Apply `padding-section-*` to the same div as `padding-global` to reduce
nesting:

```
section_home
└── padding-global padding-section-large
    └── container-large
        └── (content)
```

If a section's vertical padding is unique, either:

- **Recommended:** use spacing blocks on the top and bottom of the section
  (see `references/05-spacing-strategy.md`).
- Or apply the unique padding to the `section_[identifier]` class.
