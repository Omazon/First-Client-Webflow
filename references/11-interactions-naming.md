# Interactions naming

Source: https://finsweet.com/client-first/docs/interactions-naming

## Naming convention

> **Element** [Action + State]

- **Element** is the section/div/button/etc. that the interaction is applied to.
- **Action** describes the interaction.
- **State** is added if valuable for context.

Example:

- Element = **Sort Button Arrow**
- Action = **Rotate**
- State = **Open**
- Full name: **Sort Button Arrow [Rotate Open]**

## Maximum context

The Element and Action phrases should give as much context as possible to
the purpose of the interaction in the project. A new developer entering the
build should know what the interaction does. Use powerful keywords.

## Minimal words

Keep descriptions short. Interaction names should not overflow past the
Designer Interactions UI panel. If they do, the name is too descriptive.

Use capital letters for the first character of each word to improve
scan-ability.

## Square brackets

Separate the Action and State keywords from the Element keywords using
square brackets around `[Action State]`. This visually separates both parts.

## Examples

### General naming

> **Button Arrow [Move In]**
> Default button arrow moves in.
>
> **Button Arrow [Move Out]**
> Primary button effect "out" state moves the arrow to original position.

> **Image [Show Scroll In]**
> Image appears when the user scrolls into the section.
>
> **Image [Hide Scroll Out]**
> Image hides when the user scrolls out.

> **Nav Menu [Open]**
> Primary nav menu open.
>
> **Nav Menu [Close]**
> Primary nav menu close.

### Specific naming

> **Home Hero Lottie [Show]**
> Show and play Lottie explosion on the home hero section.
>
> **Home Hero Lottie [Hide]**
> Hides and resets the Lottie.

> **Jobs Item Modal [Open]**
> Open apply modal, triggered by a jobs item.
>
> **Jobs Item Modal [Close]**
> Close apply modal.

> **Contact Form Input [Height Increase]**
> Increase height of the contact form input.
>
> **Contact Form Input [Height Decrease]**
> Decrease height of the contact form input.

## Keywords

### Action keywords

Use the action that occurs when the interaction runs. Use the least amount
of words to give the most context.

Popular action keywords:

- Show
- Hide
- Move
- Rotate
- Scale

### State keywords

Add a state to communicate a toggling state of a sequence.

Popular state keywords:

- In / Out
- Open / Close
- Increase / Decrease
- Expand / Collapse

### Action and State can mix

We don't need to strictly follow `[Action + State]`. Be flexible inside the
brackets.

- `Element [Action + State]` — both included
- `Element [Action]` — action only
- `Element [State]` — state only
- `Element [Action]` — sometimes a state keyword alone is cleaner

Don't overthink this. Pick something clear and continue working.

### Trigger keywords

Optionally add a trigger if it enhances the context:

- Click
- Hover
- Mouse Move
- Scroll
- While Scrolling
- Load

#### Use trigger keywords carefully

Trigger keywords are technically inaccurate because Webflow interactions
can be triggered by different triggers on different devices. The same
interaction may run on hover on desktop and click on mobile.

Example: an interaction that opens a dropdown nav item.

- Desktop: hover trigger.
- Mobile: click trigger.
- The trigger keyword is wrong because it changes per device.
- "Nav Dropdown [Open]" is the correct name — describes what the
  interaction does, not how it's triggered.

#### When trigger keywords make sense

When the trigger is part of the interaction's purpose, even though
Webflow separates them:

- **Discount Modal [Delay On Load]** — "delay" and "load" are important to
  the action.
- **Blank Div [Open Modal With JS Click]** — this Div listens for a JS
  click. The "click" trigger is part of the design.

### Responsive keywords

Add a responsive keyword at the end when the interaction is created for a
specific breakpoint:

- **Nav Sidebar Slide [Show] [Mobile]**
- **Hero Scroll Trigger Div [In] [Tablet Mobile]**
- **Background Textures [Hover In] [Desktop]**

Only specify the breakpoint if the interaction is for that breakpoint only.

## Naming in conflicts

Don't overthink it. Make a decision and move forward. The decision is not
always clear. That's OK. Pick something and move on.

Breaking workflow to overthink naming is not advised. Happy interacting.
