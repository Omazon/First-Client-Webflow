# Overview

Source: https://finsweet.com/client-first/docs/intro

## Client-First definition

**Client-First = We put our clients' interests first in the Webflow build
process.**

By making clients the top priority, the style system satisfies their needs
and makes us better Webflow developers.

## Goals of Client-First

1. To create an organization system for the project.
2. To enable speed and flexibility in Webflow Designer.
3. To define a strategy for class usage.
4. To standardize a core structure shared across all pages.
5. To create a Webflow build that is scalable and easily manageable.
6. To help developers, clients, or anyone understand the project.

## What clients want

1. A scalable Webflow project.
2. A project built quickly, without losing quality.
3. A project that many people in the agency can manage.
4. A project that can be handed off to a different Webflow developer/agency
   if the client changes vendors.
5. A project that a client can manage inside Designer.

## Disclaimer

This is not following every best practice of traditional HTML and CSS build
conventions. This is Webflow. Webflow has redefined how HTML and CSS can be
managed visually. Client-First is built specifically for Webflow Designer
workflow and organization.

## Naming convention mindset

A Webflow developer, client, or any person should be able to understand what
a class is doing based on the class name alone, even without prior
Client-First knowledge.

### Goals of the naming convention

- Empower a non-technical person to manage the website.
- Be clear, informative, and descriptive.
- Give the reader as much context into the purpose of the class.
- No abbreviations, no shorthand, no confusion.
- Use keywords that can be searched in the Styles panel.
- Visualize the purpose of a class based on its name.

### Questions to ask when naming

- "What is this class doing in the project?"
- "What is the purpose of this class?"
- "How can I give the most context into what this class is responsible for?"

### Keywords go from general to specific

Within a class name, keywords go from general to specific:

- `text-size-large`: `text` (general) → `size` (specific CSS property) →
  `large` (specific value).
- `team-list_headshot-wrapper`: `team-list` (general folder) → `headshot`
  (specific element) → `wrapper` (specific role).

This convention powers intelligent class search and clean Folders
organization.

## Webflow-focused strategies

- **Classes strategy** — custom vs utility, deep stacking rules.
- **Core structure strategy** — page-wrapper, main-wrapper, section, padding.
- **Typography strategy** — default HTML tags, utility class system.
- **Spacing strategy** — utility blocks/wrappers, custom CSS Grid.
- **Folders strategy** — underscore folder system, utility folder system.

## When a non-Client-First question comes up

- For a question about **Webflow as a platform** (not CF-specific), do not
  load this skill. Load a general Webflow skill.
- For a question about **accessibility, HTML semantics, or ARIA** in general
  (not CF-specific), the CF skill still applies because CF codifies these
  practices — but the underlying guidance comes from
  `references/13-semantic-html.md` and `references/14-accessibility.md`.
- For a question about **Finsweet Extension specifically** (not CF
  conventions), this skill only covers the Folders and PX to REM Migrator
  parts of the Extension. Defer to Finsweet docs for other Extension tools.
