---
name: brainstorming
description: Use before any product-design work - new feature, screen, flow, system, or modification. Refines ideas through dialogue, frames the problem, explores approaches, and aligns on direction before pixels
---

# Brainstorming

## Overview

The conversational front-end of any design project. Turn rough ideas into a framed, agreed-on direction through natural dialogue. End state: the user has approved a direction and (optionally) a written spec exists.

This is the **first** skill that fires when a design conversation starts. It pulls in `exploring-options` for the option-generation step and (optionally) `writing-spec` for documentation.

<HARD-GATE>
Do NOT open Figma, draft a layout, propose a component, or take any pixel-level action until the user has approved a direction. This applies to every project regardless of perceived simplicity.
</HARD-GATE>

## The Anti-Pattern: "This is too simple to brainstorm"

A button color change, a copy tweak, a small banner — all of them. "Simple" projects are where unexamined assumptions cost the most rework. The brainstorm can be short (3 questions, 5 sentences) for truly simple work, but it must happen.

## The Process

```
1. Read the room (context)
       ↓
2. Ask clarifying questions (one at a time)
       ↓
3. Propose 2-3 approaches  ──invoke──→  exploring-options
       ↓
4. Present chosen direction in sections, get approval per section
       ↓
5. Light spec?  ──yes──→  invoke writing-spec
       ↓
6. Terminal: hand off to design execution
```

### 1. Read the room

Before any question:
- What did the user already tell you in this conversation? Don't ask twice.
- Is there a brief, ticket, Figma file, doc, or prior research? Read it first.
- What domain is this? If unfamiliar, invoke `learning-a-domain` first.

### 2. Ask clarifying questions

**One at a time. Not a list of 5.** Each answer changes the next question.

Prefer multiple-choice — easier to answer, surfaces undecided assumptions:

> Good: "Is this for new users, existing users, or both? (a) new only (b) existing only (c) both — and if both, which is primary?"
>
> Bad: "Tell me about your users."

Focus questions on:
- **Problem** — what's actually wrong / missing
- **Users** — who specifically, what role
- **Job-to-be-done** — what they're trying to accomplish in their words
- **Constraints** — platform, brand, regulatory, technical, deadline
- **Success criteria** — how we'll know it worked

If you get vague answers ("users want better UX"), drill: "Better in what way? What does the current experience fail to do?"

### 3. Watch for scope confusion

If answers involve "and also" three times, the scope is too big. Help decompose:
- What are the independent pieces?
- Which one matters most?
- What order should they be tackled?

Then brainstorm the first piece. Each piece gets its own brainstorm → spec → design cycle.

### 4. Surface assumptions

When the user asserts something like *"users want X"*, ask gently:
- How do we know? Research, support thread, ticket, anecdote?
- If anecdote: that's an assumption to flag, not a fact.

The point isn't to interrogate. It's to make assumptions explicit so they get tested, not designed against.

### 5. Propose 2-3 approaches

Once you understand the problem, **invoke `exploring-options`** to generate 3+ distinct directions with tradeoffs. Bring them back to the conversation.

Walk the user through each option:
- The mental model
- What it optimizes for
- What it sacrifices
- When it's the right choice

Then state your recommendation and *why*. Three options without a recommendation is a quiz; three options with a recommendation is a design conversation.

### 6. Present the direction in sections

Once a direction is chosen, present the design — but in sections short enough to actually digest:

- Information architecture / flow
- Key screens (one at a time)
- Component / pattern choices
- Edge cases & states
- Open questions

After each section, ask: *"does this match what you're imagining? Anything to adjust?"*

Don't dump everything at once. The user can't react meaningfully to a wall of text.

### 7. Optional: write a spec

If the project warrants documentation (anything cross-functional, anything you'll come back to, anything stakeholders need to read async), invoke `writing-spec` to produce a light PRD / design spec.

Skip for true throwaways (a 5-min copy tweak doesn't need a spec).

### 8. Terminal state

The brainstorm ends when **the user has approved a direction.** The next move is design execution — open Figma, draft, iterate.

After execution, the workflow continues:
- `critiquing` (concept review on the first draft)
- `design-qa` (visual quality pass)
- `presenting` (when ready to share with stakeholders)
- `handoff` (when ready for engineering)

## Key Principles

- **One question at a time.** Don't overwhelm with multiple.
- **Multiple choice preferred.** Easier to answer than open-ended.
- **YAGNI ruthlessly.** Cut features that don't serve the framed problem.
- **Always 3 options.** Use `exploring-options` — never present one direction.
- **Incremental validation.** Present in sections, get approval before continuing.
- **Be flexible.** Go back and clarify when something doesn't make sense. The plan-line is not sacred.

## What "Direction Approved" Means

It means the user has explicitly said yes to:
- The framed problem
- The chosen approach (with awareness of alternatives)
- The major design moves (flow, key screens)
- Known constraints and open questions

NOT: "looks good, let's keep going." That's politeness, not approval. Push for explicit yes/no.

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "I know what the user wants, I am the user" | You're a sample of one. Frame on the actual user. |
| "The PM gave me a clear brief" | The brief is the start. Brainstorm tests whether it solves the right problem. |
| "There's no time to brainstorm" | Brainstorm is 15-30 minutes. Wrong-problem design is days. |
| "It's just a small change" | Small changes need framing too. The brainstorm just gets shorter. |
| "Let me sketch first, then frame" | You won't. Frame first. |
| "I'll figure it out in Figma" | Figma is for execution. Brainstorm is for direction. Different tools. |
| "I already discussed this offline" | Then summarize the discussion here and confirm. Don't skip the artifact. |

## Red Flags — STOP

- About to open Figma without an approved direction
- "Let me just throw something together"
- "I'll figure it out as I go"
- "The brief is enough"
- "It's obvious what we need"
- About to present one direction without showing alternatives

**All of these mean: stop. Run the brainstorm.**

## Pairs With

- `learning-a-domain` — if domain is unfamiliar, invoke this BEFORE brainstorming
- `exploring-options` — invoked from inside brainstorming (step 5) to generate 3+ directions
- `writing-spec` — invoked from inside brainstorming (step 7) for the design doc
- `critiquing`, `design-qa`, `presenting`, `handoff` — all come AFTER brainstorming, during/after design execution

## Note on v0.1

Upstream `superpowers:brainstorming` offers an optional **visual companion** — a local browser that renders mockups, diagrams, and option comparisons during dialogue. This plugin doesn't have that yet. For now, brainstorming is text-only; visual artifacts come from Figma or sketches the user shares.
