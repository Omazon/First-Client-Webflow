# Folders strategy

Source: https://finsweet.com/client-first/docs/folders-strategy

Most of this page is about strategies for custom class folders. Different
projects need different folder organization.

> There is often no right or wrong to class naming. There is only more and
> less efficient.

Use multiple strategies per project, but not all strategies at once. Have a
unified folder naming plan before development starts.

## Types of folder organization

### One folder

#### One folder level, general folder name

Helpful for components that are not specific to any page or content. Use
when the element recurs globally.

```
one-folder_name-of-element
```

Example: a slider used on multiple pages.

#### One folder level, specific folder name

Helpful for any type of custom folder, regardless of project size. Add the
page name or content-specific keywords.

```
one-specific-folder_name-of-element
```

Good for smaller custom websites that don't require much global
organization. Good for sections, components, and elements created for a
specific page.

#### One folder level, page name as folder name

A folder of classes specific to an identifiable page.

```
page-folder_name-of-element
```

**Important:** do not use a page-name folder and reuse the class on other
pages. That leads to disorganization. If the class is reused, use the
"specific folder name" strategy instead.

#### One folder level, page name as element prefix

Create a unique variation of a component by page while staying in the
component folder.

```
one-folder_page-name-element
slider_culture-pane
```

Useful when every slider shares styles, but the homepage has a unique
arrow UI. The variation isn't enough to be a new component, but it is
visually distinct.

A combo class can also be used (`slider_pane is-culture`) if combo class
inheritance makes sense.

### Nested folders

Helpful in larger sites with complex organization. Two folder levels don't
have to be site-wide — use them only for parts of the project that need
deeper organization.

> Just because we have the power of nested folders doesn't mean we should
> always use them. Only nest when there is a clear organizational win.

#### Nested folders, page folder first

Identify a collection of components by page name first.

```
page-folder_keyword-folder_name-of-element
```

Good when the same component category has unique variations on many
different pages.

#### Nested folders, keyword folder first

Identify a component by keyword first, then by page name.

```
keyword-folder_page-folder_name-of-element
```

Good when each page has its own version of a recurring component.

#### Nested folders, any organization

Above are clear use cases, but not every naming decision is clear. Custom
organizations are accepted as long as the strategy is clear.

```
anything_anything_name-of-element
```

## Page name in class name

The decision to add a page name to a class name is powerful.

### When to add the page name

- **Element is styled for one page only:** add the page name to the class.
  Two naming options:
  - `page-component_element-name` (one folder)
  - `page_component_element-name` (two folders)

Examples:

```
home-slider_arrow        # one folder
home_slider_arrow        # two folders

team-slider_arrow        # one folder
team_slider_arrow        # two folders

portfolio-slider_arrow   # one folder
portfolio_slider_arrow   # two folders
```

### When NOT to add the page name

If the class is reused across the project, keep the keyword as the base
folder:

```
slider_arrow              # general, reused
header_image-right
subscribe_form-input
clients-logos_row
```

## One folder vs. two folders

The decision depends on the project size and the level of organization
required. Different parts of the project can use different folder depths.

### Computer analogy

- A master's degree student with hundreds of files needs nested folders:
  `Personal / School / University / university-test-scores.xls`.
- A young primary school student with 12 files does not:
  `School / geography-test-scores.xls`.

If a folder has 100 items, consider nesting. If it has 12, probably not.

## Component libraries

Component libraries like Relume Library may benefit from nested folders —
or even many nested folders.

A component library has many reusable components. Naming them
instance-specific doesn't work because they are designed to be reused.

### Without nested folders

```
slider1_component
slider2_component
slider3_component
grid1_component
grid7_component
logo-row1_component
logo-row2_component
```

A flat list of 100 components in a flat list of folders is not easy to
navigate.

### With nested folders

```
slider_1_component
slider_2_component
slider_3_component
grid_1_component
grid_7_component
logo-row_1_component
logo-row_2_component
```

All `slider_*`, `grid_*`, `logo-row_*` types as base folders. Click into
each to see variations.

After pasting into the project, use Finsweet Extension to bulk rename the
folder (`layouts_grid_1_` → `team-grid_`).

## Using the component keyword

In v1, any underscore meant "component". In v2 with Folders, that's no
longer true. The underscore is for organization. To mark a class as a
component, use the literal word `component` as the element identifier.

```
client-slider_component
client-slider_mask
client-slider_grid
client-slider_arrow
```

This tells us that `clients-slider_` is a complete, copy-pasteable
component. Not every folder needs the `component` keyword — only the ones
representing a full reusable component.

Other folders are just for organization (e.g. `styleguide_*` for a style
guide page).

## Folder decision making tree (recap)

1. **Used globally for a specific CSS style?**
   → Utility class folder. Use existing utilities. If a new style is
   needed, create a new utility folder.

2. **Specific to a page?**
   → Add the page name to the class name. Use either a single folder
   (`page-component_element`) or two nested folders
   (`page_component_element`).

3. **Part of a specific component?**
   → Use the specific keyword: `slider-clients_pane` or
   `slider_clients-pane`.

4. **Part of a general reusable component?**
   → Keep the folder name general: `slider_pane`.

## Practical recommendations

- **Small sites (≤5 pages, mostly custom layouts):** one folder, page or
  topic-based, no nesting.
- **Medium sites (5-20 pages, recurring components):** one folder for
  reusable components, optional page-name prefix for unique instances.
- **Large sites (20+ pages, design system):** nested folders for
  components, utility folders for global styles, consistent page-name
  strategy for unique sections.
- **Component libraries:** nested folders with `_component` identifier on
  the parent wrapper of each complete component.
