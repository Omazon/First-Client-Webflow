# Folders

Source: https://finsweet.com/client-first/docs/folders

Folders is a virtual organization tool to group and visually manage classes
inside Webflow Designer. It is part of the **Finsweet Extension** and works
with a simple naming convention.

> Folders work like folders on our computer. We give a name to the folder
> and put items inside. The underscore character is the folder creation
> tool for custom classes.

There are two types of folders: **custom class folders** and **utility
class folders**.

## 1. Custom class folders

> A custom class is a class created for a specific component, page,
> grouping of elements, or single element.
>
> **Custom classes use an underscore in the class name.**

```
nav_primary_logo-wrapper
```

This creates a `nav_` folder, with a nested `primary_` folder, containing
the element `logo-wrapper`.

### Folder underscores

- `folder-one_element-name` — one folder.
- `folder-one_folder-two_element-name` — two nested folders.

The folder name is generated from the keyword(s) that come before each
underscore.

### How to group elements

Depends on the project. Ask:

- How many pages are in the project?
- Is the design and layout for each page unique?
- Are there recurring elements?

Big project → more folders, more nesting. Small project → fewer folders,
fewer nesting.

### Nest folders with purpose

Only nest if meaningful. Many projects have one folder level with no
nesting. Over-nesting makes the project harder to manage.

### One underscore equals one folder

```
home-testimonials_wrapper
home-testimonials_headshot
home-testimonials_text-small
header-top_content
header-top_image
header-top_accent-left
careers_custom-padding
careers_title-animation
careers_scroll-trigger
```

Two underscores equal two nested folders:

```
home_testimonials_wrapper
home_testimonials_headshot
home_testimonials_text-small
home_header-top_content
home_header-top_image
home_header-top_accent-left
home_careers_custom-padding
home_careers_title-animation
home_careers_scroll-trigger
```

## 2. Utility class folders

> A utility class is a class created with a specific combination of CSS
> properties that can be applied to elements across the project.
>
> **Utility classes do not use an underscore in the class name.**

Any class without an underscore goes into the Utility folder. Classes with
dashes only are utility classes. Folders will automatically group classes
by matching keywords.

### Examples

```
text-color-primary
text-color-secondary
text-color-brand
text-size-small
text-size-medium
text-size-large
padding-top
padding-large
page-wrapper
page-padding
```

### Matching keywords by index

Finsweet Extension looks for matching keywords by position and organizes
classes inside the Utility folder.

For `text-color-primary`:

- `text` = firstword
- `color` = secondword
- `primary` = thirdword

A folder is always created from `firstword`. The "text" folder is created
regardless of other class namings.

If at least one other class shares both "text" as firstword and "color" as
secondword, a "color" folder is created inside "text".

Two classes starting with `text-color-` → "text" folder with "color"
subfolder.

### No matching keywords at secondword

If a class like `text-indent-large` is the only `text-indent-*` class, it
stays in the "text" folder. No "indent" folder is created until another
`text-indent-*` class is added.

### No matching keywords at firstword

If a class has a unique firstword (e.g. `filter-blur-extend` with no other
"filter" classes), a "filter" folder is created with that one class.

### Scaling utility folders

Add or remove folders from the Utility folder as needed per project.
Matching keywords create nested folders.

```
shadow-box-large
shadow-box-medium
shadow-box-small
shadow-circle-large
shadow-circle-medium
shadow-circle-small
shadow-blur-x
shadow-blur-y
```

Creates a `shadow` folder with `box`, `circle`, and `blur` subfolders.

## Folder decision making tree

Ask, in order:

1. **Is this class used to create a specific CSS style that can be used on
   any element?**
   Yes → use Utility Class folders. Use the existing utility classes
   (`text-`, `heading-`, `page-`, `icon-`). If a new utility style is
   needed, create a new utility folder (e.g. `shadow-small`,
   `shadow-medium`, `shadow-large`).

2. **Is the element specific to this page?**
   Yes → add the page name to the class name:
   - `[page]-slider_pane`
   - `[page]_slider-pane`
   - `slider_[page]-pane`

3. **Is this element part of a specific component?**
   Yes → use the specific keyword in the class name:
   - `slider-clients_pane`
   - `slider_clients-pane`

4. **Is this element part of a general component used anywhere?**
   Yes → keep the folder name general:
   - `slider_pane`

## Workflow enhancements

### Folder rename (bulk class rename)

Rename every class inside a folder in one bulk process. Useful when
importing a component from Relume Library and renaming it for the project.

### Class/Folder data and page influence

Open the class details to see how the class is used — elements affected on
this page and elements affected on other pages.

### Copy class name to clipboard

Copy any part of the class name based on where you open the class details.
Copy the folder name from the folder level. Copy the entire class name from
the element identifier level.
