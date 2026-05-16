---
name: critiquing
description: Use before sharing design work, after a first draft, when reviewing peer work, or when a design feels off but you can't name why
---

# Critiquing

## Overview

A structured pass to surface conceptual problems with a design — *is this the right thing to build?* — distinct from `design-qa` which asks *is the right thing built well?*

Critique looks at hierarchy, intent, narrative, and fit with the framed problem. QA looks at pixels.

## When to Use

- After your first complete draft, before iterating further
- Before sharing with stakeholders (catch issues before others do)
- When reviewing a peer's work
- When the design "works" but feels uncomfortable and you can't name why
- After a long stretch in the file (fresh-eyes pass)

## The Critique Frame

Run these passes. Report what's strong AND what's weak — critique without affirmation is hostility.

### 1. Fit to the framed problem
- Does the design solve the problem from `brainstorming`?
- Does it solve a different problem instead?
- Does it solve more than the problem? (scope creep)
- Does it solve only part?

### 2. Hierarchy
- What's the most important thing on the screen? Does the design say so?
- What's the next thing? And the next?
- Are there competing primaries fighting for attention?

### 3. Intent
- What does this design *want the user to do*?
- Is the path obvious from a 3-second glance?
- Are there secondary actions louder than primaries?

### 4. Narrative / Story
- If a user reads top-to-bottom, does the sequence make sense?
- Does each section earn its place, or is it filler?
- Are decisions deferred to the user that should be made by the design?

### 5. Edge cases
- What happens with no data? Long data? Bad data?
- What happens for the user with a disability? On slow connection? On a small screen?
- What happens after the happy path? (success state, error recovery)

### 6. System fit
- Is this an extension of the design system or a fork from it?
- If a fork: is it justified, or is it accidental drift?
- Will this scale to the next 3 features in this area?

## Output Template

```
## Critique — [feature/screen]

### What's working
- [specific strength 1]
- [specific strength 2]

### What's not working
1. [issue] — [why it's an issue] — [what to consider]
2. ...

### Open questions
- [question for the designer / team]
- ...

### Suggested next moves
- [most important thing to address first]
- [next thing]
```

## Pitfalls

- **Don't redesign.** Critique surfaces problems; it doesn't solve them. Save solutions for a separate pass.
- **Don't critique style alone.** "I don't like the color" isn't critique — "the color signals premium when this feature is for budget users" is.
- **Don't pile on.** Three strong critiques are more useful than ten weak ones.

## Pairs With

- `brainstorming` — critique tests fit to the framed problem from brainstorming
- `design-qa` — runs *after* critique (no point QAing a design that fails the critique pass)
- `exploring-options` — if critique reveals fit problems, return to options
