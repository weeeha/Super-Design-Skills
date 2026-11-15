---
name: sketching
description: Use when a screen, flow or concept needs to be drawn before it is designed - "possible layouts for this screen", "wireframe this", "draw your thoughts in Figma or FigJam", "map the flow", "concept map", "how could this page be arranged", "sketch it" - or when about to produce polished UI without a low-fidelity pass
---

# Sketching

## Overview

A sketch answers one question cheaply: how could this be arranged, in what order does it happen, or how do these things relate. It is drawn in minutes, in grey boxes and real words, and it is meant to be thrown away.

Same spine as the rest of this plugin: **for a layout, three sketches, never one.** One sketch is a decision in disguise, and the three must differ in structure, not in styling. A flow, concept map or storyboard is one drawing when its structure is given, with the alternatives you rejected named in a line each.

## When to Use

- "What are the possible layouts for this screen?"
- A flow has more than three steps or more than one branch
- A concept has more than four objects or roles and people are talking past each other
- Before `prototyping` or any polished mockup of something new
- When the user points at a FigJam board or Figma page and says "draw it here"

**Don't use** for:
- Choosing a product direction (that's `exploring-options`; sketches illustrate directions, they don't replace choosing one)
- Polished mockups or anything using the real design system (design it, then `design-qa`)
- A clickable artifact (`prototyping`)

**Frame before you draw.** If nobody has said who this is for and what they are trying to do, write that in one line first, or run `brainstorming`. A sketch of an unframed problem is decoration.

**Order with `brainstorming`.** A request to design something new ("help me design X") starts with `brainstorming`, which calls for sketches when it needs them. This skill goes first only when the question is already about arrangement, order or relationships, and the one-line frame can be written without asking.

## Pick the Kind of Sketch

| Kind | The question it answers | What to draw |
|---|---|---|
| **Layout** | How could one screen be arranged? | 3 arrangements of the same content |
| **Flow** | In what order does this happen, and where does it branch? | 1 flow with the unhappy path, plus 2 alternative orderings if the order is in doubt |
| **Concept map** | How do these objects and roles relate? | 1 map, 12 nodes at most |
| **Storyboard** | What is the person's situation before, during and after? | 4 to 6 frames |

If the request spans two kinds, draw the flow first. The layout question usually changes once the order is known.

## Fidelity Rules

These keep a sketch a sketch:

- **Grey boxes and real words.** Real field names, real button labels, real counts ("12 projects", not "Item 1, Item 2"). Lorem ipsum hides the layout problems that real content reveals.
- **No design system, no color.** One accent is allowed, to mark the single thing the sketch is about.
- **One size.** State it: desktop 1440, or mobile 390.
- **Ten minutes each.** A sketch that takes longer is a mockup.
- **Label each one** with the idea in three words: "List first", "Map first", "Inbox first".

## Where to Draw

Ask once if it is not obvious, then stay there:

| Surface | When | How |
|---|---|---|
| **In chat** | Quick layout questions, first pass | Text boxes, as in the example below |
| **FigJam board** | Flows, concept maps, storyboards, anything a team will react to | Shapes and connectors. If a Figma tool is connected, load its own usage skill before drawing |
| **Figma design file** | Layout sketches that will sit next to real designs | Wireframe frames on a page named `Sketches - [date]`. Never on a page that holds finished work |
| **A local HTML page** | Nothing is connected and the sketches need to be seen side by side | Plain boxes, no styling |

Example of three layout sketches in chat, for a screen that shows a call in progress:

```
A. Contact first          B. Transcript first       C. Split
+-------------------+     +-------------------+     +---------+---------+
| Photo  Name  00:42|     | Name 00:42   [End]|     | Photo   | Live    |
| Company           |     +-------------------+     | Name    | transcr.|
+-------------------+     | Live transcript   |     | Company |         |
| Notes field       |     |                   |     +---------+         |
|                   |     |                   |     | Notes   |         |
+-------------------+     +-------------------+     +---------+---------+
| [Mute] [Hold][End]|     | Notes (collapsed) |     |[Mute] [Hold] [End]|
+-------------------+     +-------------------+     +-------------------+
```

## The Process

1. **Name the question** the sketch answers, in one line. If you can't, go back to framing.
2. **Pick the kind** from the table.
3. **Collect the real content**: object names, field names, counts, the longest realistic label. From the spec, the product, or the user.
4. **Draw.** For a layout: three that differ in structure. Vary what is primary (the list, the detail, the canvas). Changing a sidebar from left to right is not a different sketch. For a flow, concept map or storyboard: one drawing. Add alternatives only when the order or the structure itself is in doubt, and then vary the order or where the decision sits.
5. **Annotate each** with two lines: what it makes easy, what it makes hard.
6. **Recommend one** and say why, then ask. Keep the sketches not chosen; they are the "what we tried" beat in `presenting`. For a single flow or map, name the alternatives you rejected instead.
7. **Say what the sketch does not show**: states, empty and error cases, responsive behavior. Those belong to the next step.

## Output Template

```
## Sketches - [what] - [kind] - [size]

**Question:** [the one question these answer]
**For:** [who, doing what]

### A. [three-word label]
[sketch, or link to the frame]
- Makes easy: ...
- Makes hard: ...

### B. [three-word label]
...

### C. [three-word label]
...

**My lean:** [A / B / C], because ...
**Not shown yet:** [states, edge cases, other sizes]
**Next:** [exploring-options / prototyping / critiquing]
```

For a single flow, concept map or storyboard, use one section instead of A, B and C, and replace "My lean" with "Alternatives I rejected", one line each.

## Common Pitfalls

- **Three sketches that are one sketch.** Same structure, different decoration. Vary what is primary.
- **Placeholder content.** "Title, subtitle, item" lets every layout look fine.
- **Creeping fidelity.** Real components, shadows and brand color turn the conversation to styling.
- **Sketching on the real page.** Low-fi frames next to finished work get mistaken for it. Use a separate page or board.
- **Skipping the unhappy path in a flow.** The branch where it fails is usually where the design is.

## Pairs With

- `brainstorming` - supplies the frame. Run it first when the problem is not stated.
- `exploring-options` - chooses between directions. Sketches make each direction visible.
- `prototyping` - takes the chosen sketch and makes it clickable.
- `critiquing` - a sketch can be critiqued for hierarchy and flow before any pixels exist.
- `presenting` - the two sketches not chosen are the "what we tried" beat.

## Iteration Notes (v0.1)

Written from session evidence: the recurring asks were "let's think about possible layouts for this call screen" and "can you draw your thoughts here in Figma". Watch for:
- Whether ten minutes per sketch is realistic when drawing on a FigJam board through a tool
- Whether flows deserve their own skill once they are common
- Whether the chat sketches are readable enough, or the user always asks for the board
