# Semantic HTML tags

Source: https://finsweet.com/client-first/docs/semantic-html-tags

## What are semantic HTML tags?

A semantic HTML tag clearly describes what an element is. Elements like
`<header>`, `<footer>`, and `<article>` are semantic — they describe the
purpose of the element and the type of content inside.

Semantic tags help users and machines interpret content.

### Why use them

1. Make the site more accessible.
2. Improve how search engines crawl the site.

## How to use semantic tags in Webflow

To change an element's tag in Webflow:

1. Select the element.
2. Go to the settings panel (`D`).
3. Choose a tag from the dropdown.

### Most-used tags

- `<header>` — header for the document or a section.
- `<footer>` — footer for the document or a section.
- `<nav>` — navigation links.
- `<main>` — main content of a document.
- `<section>` — section in the document.
- `<article>` — independent, self-contained content.
- `<aside>` — content aside from the page content.
- `<address>` — contact information.
- `<figure>` — self-contained content like illustrations or photos.
- `<h1>`–`<h6>` — Heading levels from highest to lowest.

## Basic semantic structure

### `<header>`

Most commonly used to wrap a website's navbar. In Client-First, add this tag
to the `nav_component` or equivalent.

Can also specify the header of a section or an article. Both are correct.

A `<header>` cannot be placed within a `<footer>`, `<address>`, or another
`<header>` element.

### `<main>`

Defines the main content. On most pages, wraps everything between the
`<header>` and `<footer>`. Content inside `<main>` should be unique to the
page.

- The header and footer should NOT be inside `<main>`.
- The `<main>` should not contain repeated content (sidebars, nav links,
  copyright, logos, search forms, cookie consent).

In Client-First, add the `<main>` tag to `main-wrapper`.

### `<footer>`

Usually contains:

- Authorship information
- Copyright information
- Contact information
- Sitemap
- "Back to top" links
- Related documents

The `<footer>` relates to the nearest sectioning parent — section or page.

## Sectioning elements

### `<section>`

Used for sectioning the page. Sections should always have a Heading, with
very few exceptions.

Sections can be nested. Articles can contain sections and vice versa.

In Client-First, set the HTML tag of every `section_[identifier]` to
`<section>`.

### `<article>`

Specifies independent, self-contained content. An article should make
sense on its own and be distributable independently.

Common uses:

- Forum post
- Magazine/newspaper article
- Blog entry
- Product card
- User-submitted comment
- Interactive widget

Don't reserve `<article>` for blog posts only.

### `<aside>`

Defines content "aside" from the primary content. Aside content should
relate to the surrounding content.

Use for:

- Page-related sidebars
- Related links
- Related content
- Advertisements
- Tables of content

If the aside relates to a section, place it inside that section. If it
relates to the whole page, place it outside any section (e.g. next to
`<main>`).

### `<nav>`

Specifies a list of navigation links. Use for:

- Navbar links
- Sidebar links
- Table of contents
- Footer links
- Breadcrumbs

## Headings `<h1>`–`<h6>`

### One `<h1>` per page

The `<h1>` should be the page title. When a user lands on the page and
reads the `<h1>`, they should understand what the page is about.

### Nest headings properly

- `<h1>` — page title.
- `<h2>` — subtopics of the `<h1>`.
- `<h3>` — subtopics of the `<h2>`. And so on.

Don't skip levels. Screen-reader users often jump from Heading to Heading;
skipping a level creates confusion.

## Figures, addresses, and others

### `<address>`

Contact information for the author/owner of a page or article. Multiple
`<address>` tags allowed.

- Inside an `<article>` → refers to the article.
- Outside an `<article>` → refers to the whole page.

### `<figure>`

Self-contained content like illustrations, diagrams, photos, code listings.

Removing a figure should not affect the flow of the page. Webflow
automatically wraps Rich Text images/videos with `<figure>` when a
description is added.

The `<figure>` tag is not as critical for accessibility and SEO as adding
`alt` text to visual content.

## Semantic HTML in Client-First

Apply semantic tags to the core structure:

```
page-wrapper
└── <header>          # nav wrapper
│   └── nav_component
└── <main>            # main-wrapper
│   └── section_home     <section>
│   └── section_about    <section>
└── <footer>          # site footer
```

The Client-First Semantic HTML cloneable is available from Finsweet for
visual reference.
