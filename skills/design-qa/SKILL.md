---
name: design-qa
description: Use when checking visual quality on completed or near-completed designs - alignment, spacing rhythm, type scale, contrast, state coverage, token usage, and consistency. Accepts Figma links and screenshots
---

# Design QA

## Overview

A designer's-eye pass over completed design work. Catches the things you stop seeing after staring at the file for two hours: misaligned edges, inconsistent spacing, off-token colors, missing states, drift from the system.

This is **not** engineering review. This is the pass you'd want a sharp peer to do before handoff.

## When to Use

- Before sharing work with stakeholders
- Before handoff to engineering
- After a long stretch on the same file (fresh eyes)
- When something feels "off" but you can't name it
- On a peer's work when asked to review

## Inputs

Two modes:

### Mode A — Figma link
The user pastes a Figma URL. Use the Figma MCP (`figma-remote` tools) to fetch:
- `get_design_context` — structure and variables
- `get_screenshot` — visual reference
- `get_variable_defs` — token usage
- `get_metadata` — layer hierarchy

This gives the richest QA — you can verify tokens, see real spacing values, and check structure.

### Mode B — Screenshot
The user pastes/uploads an image. QA proceeds visually. You can still catch most issues, but token verification is unavailable.

**Always ask which mode** if it's unclear from the request.

## The QA Checklist

Run these passes in order. Report findings grouped by severity.

### 1. Alignment

- Edges align to a baseline grid (typically 4px or 8px)
- Text baselines align across cards/sections
- Optical alignment for icons next to text (icons often need -1px nudge to look centered)
- Repeated elements (cards, list items) align their internal anchors

**Common misses:**
- Section headings off-grid by 1-3px
- Icons visually misaligned despite snapping to bounds
- Cards in a row with different internal padding

### 2. Spacing Rhythm

- Spacing follows a defined scale (4, 8, 12, 16, 24, 32, 48, 64 — or whatever the system uses)
- No "magic" spacing values (e.g. 17px, 23px)
- Vertical rhythm is consistent within a section
- Group/separator spacing tells the right story (closer = related, farther = unrelated)

**Common misses:**
- Inconsistent gaps between cards in the same grid
- Tight spacing where breathing room is needed (and vice versa)
- Section padding that contradicts the visual hierarchy

### 3. Typography

- Sizes pulled from a defined type scale, not free numbers
- Line-height consistent for matching styles
- Letter spacing appropriate for size (tighter at large sizes, default at body)
- Weight hierarchy is intentional (don't use 5 weights when 2 would do)
- Truncation/wrap behavior defined for long content

**Common misses:**
- Body text using one size on desktop and another on mobile without scale reasoning
- Heading weights inconsistent across sections
- Caption-size text doing the job of body

### 4. Color & Contrast

- Colors pulled from tokens, not raw hex
- Foreground/background contrast meets WCAG 2.1 AA at minimum (4.5:1 body, 3:1 large text)
- Disabled, hover, focus, active states are all defined — not just default
- Dark mode and light mode both work (if applicable)
- Color isn't the only signal (icons/text reinforce status)

**Common misses:**
- Brand color used as body text — fails contrast on most backgrounds
- Disabled state at 40% opacity — often unreadable
- Status communicated by red/green only — fails colorblind users

### 5. Token Usage (Figma mode)

- Colors use variables, not hex
- Spacing uses variables, not numbers
- Text styles applied, not local overrides
- Component instances, not detached copies
- No "Color/Primary/500" alongside "color-primary-500" — naming consistent

**Common misses:**
- A few colors hardcoded after a system update
- Spacing variables on most elements but raw numbers on a few
- Detached components after edits

### 6. State Coverage

For every interactive element, check:
- Default
- Hover
- Focus (keyboard)
- Active / pressed
- Disabled
- Loading (if applicable)
- Error (if applicable)
- Success (if applicable)
- Empty (if data-driven)

**Common misses:**
- No keyboard focus state
- No empty state for lists
- No loading state for async data
- Error state shown but no recovery action

### 7. Consistency Across Screens

If multiple screens are in scope:
- Same component used the same way in different places
- Same action labeled the same way ("Save" everywhere, not "Save"/"Submit"/"Confirm" mixed)
- Same hierarchy logic (primary action position, secondary action treatment)
- Same data shapes rendered with the same component

**Common misses:**
- Modal action positions differ across modals
- "Cancel" sometimes left, sometimes right
- Same data (e.g. a user row) rendered differently in different views

## Severity Levels

| Severity | Definition | Example |
|---|---|---|
| **Blocker** | Ships as broken. Must fix before handoff. | Missing focus state on primary action, fails AA contrast |
| **High** | Visible inconsistency, system drift, ships as off. | Inconsistent card padding across grid |
| **Medium** | Catchable polish issue. Fix if time, flag if not. | Icon optical misalignment, off-token spacing |
| **Low** | Nitpick. Note for awareness. | Slightly tight letter-spacing at large size |

## Output Template

```
## Design QA — [screen/feature name]

**Mode:** Figma / Screenshot
**Files reviewed:** [link or "1 image"]

### Blockers
1. [issue] — [where] — [why it's a blocker]
2. ...

### High
1. ...

### Medium
1. ...

### Low
1. ...

### Looks good
- [specific things that pass — be concrete]
```

Be specific about *where* — "the third card in the products grid", not "some cards."

## Common Pitfalls in QA

- **Don't critique the design.** This is QA, not critique. If you think the *concept* is wrong, that's `critiquing`, not `design-qa`.
- **Don't add scope.** If you spot a great UX improvement, note it separately as "future iteration", don't bundle it into the QA pass.
- **Don't be vague.** "Spacing is inconsistent" is useless. "The gap between Card 1 and Card 2 is 16px; between Card 2 and Card 3 is 20px" is actionable.
- **Be honest about Mode B limits.** Without Figma access you can't verify tokens. Say so.

## Pairs With

- `critiquing` — for concept-level review (is this the right design?)
- `handoff` — design-qa is the gate before handoff
- `presenting` — fix blockers before any stakeholder share
