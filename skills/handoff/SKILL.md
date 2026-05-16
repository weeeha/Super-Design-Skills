---
name: handoff
description: Use when delivering completed designs to engineering - covers states, edge cases, motion, copy, redlines, token mapping, and acceptance criteria
---

# Handoff

## Overview

The artifact engineering needs to build the design without guessing. The goal is to eliminate "I assumed you meant…" conversations after build starts.

This skill assumes the design has passed `design-qa`. Don't hand off broken designs.

## What Handoff Produces

A handoff document (in the Figma file, a doc, or both) covering:

1. **Component inventory** — what's used, where, with which props/variants
2. **States** — every interactive element with all states defined
3. **Edge cases** — empty, loading, error, success, long content, no data, slow network
4. **Motion** — durations, easings, sequence (if applicable)
5. **Copy** — final strings (no "Lorem ipsum"), including microcopy for errors and empty states
6. **Redlines** — spacing, sizes, colors with their token references
7. **Accessibility notes** — focus order, ARIA labels for non-obvious controls, keyboard alternatives
8. **Acceptance criteria** — how engineering will know they built it right
9. **Open questions** — anything you deferred or weren't sure about

## The Handoff Checklist

Before delivering:

- [ ] All interactive elements have hover, focus, active, disabled states defined
- [ ] Empty state exists for every data-driven list/section
- [ ] Loading state exists for every async data area
- [ ] Error state has both display AND a clear recovery action
- [ ] Long content behavior defined (truncate? wrap? scroll? + which)
- [ ] Mobile / responsive breakpoints called out
- [ ] Dark/light theme parity (if applicable)
- [ ] All colors mapped to tokens
- [ ] All spacing mapped to scale values
- [ ] Copy is real, not placeholder
- [ ] Microcopy for errors/empty states is written, not "TODO"
- [ ] Focus order makes sense for keyboard navigation
- [ ] Any animation has duration + easing + trigger
- [ ] Open questions documented (don't hide them)

## Output Template

```
# Handoff — [Feature / Screen]

**Figma file:** [link]
**Specs doc:** [link]
**Design QA status:** ✅ Passed [date]

## Acceptance Criteria
- [ ] User can [action] from [entry point]
- [ ] [Edge case] is handled with [behavior]
- [ ] [Accessibility requirement] is met

## Component Inventory
| Component | Variant(s) | Where used |
|---|---|---|
| ... | ... | ... |

## States (per interactive element)
| Element | Default | Hover | Focus | Active | Disabled | Loading | Error |
|---|---|---|---|---|---|---|---|
| ... | ✅ | ✅ | ✅ | ✅ | ✅ | n/a | ✅ |

## Edge Cases
- **Empty state:** [behavior]
- **Loading:** [behavior, e.g. skeleton, spinner]
- **Error:** [display + recovery action]
- **Long content:** [truncate / wrap]
- **No network:** [behavior]

## Motion
| Element | Trigger | Duration | Easing |
|---|---|---|---|
| ... | ... | ... | ... |

## Copy
All final copy in the Figma file. Notable:
- Error messages: [...]
- Empty state copy: [...]
- Confirmation copy: [...]

## Tokens
- Colors: see Figma variables, all mapped
- Spacing: see Figma variables, all mapped
- Type styles: see text styles, all applied

## Accessibility
- Focus order: [described]
- ARIA: [non-obvious labels noted]
- Keyboard: [alternatives for any mouse-only interactions]

## Open Questions
- [things deferred to eng's judgment or product's decision]
```

## Common Pitfalls

- **Hidden assumptions.** "Engineering will figure out the loading state" → no they won't, and you'll get whatever's easiest. Define it.
- **Lorem ipsum at handoff.** Real copy reveals layout issues placeholder text hides.
- **No empty/error states.** These are the most-skipped, most-forgotten parts of a design.
- **Token drift in handoff doc vs Figma.** Keep one source of truth.

## Pairs With

- `design-qa` — runs immediately before handoff. Fix blockers first.
- `presenting` — handoff often coincides with the PM/Eng design review. Run `presenting` for that meeting.
