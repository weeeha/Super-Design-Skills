---
name: exploring-options
description: Use when about to commit to a single design direction, when feeling pressure to ship one idea, after the PM/stakeholder pushes a specific solution, or before any review meeting
---

# Exploring Options

## Overview

**Never present one direction. Always present three.**

A single option is a decision in disguise — it forecloses conversation and turns stakeholders into rubber-stampers. Three meaningfully different options force a real conversation about tradeoffs.

**Violating the letter of the rule is violating the spirit of the rule.**

## The Iron Law

```
NO DESIGN REVIEW WITH ONE OPTION
```

If you find yourself preparing to show one direction, stop. Generate two more before continuing.

**No exceptions:**
- Not for "obvious" answers
- Not for "small" changes
- Not for "the PM already decided"
- Not for "we're out of time"
- Not for "I already explored options in my head"

**"In my head" doesn't count.** If you can't articulate three options to a stakeholder, you didn't explore three.

## What Counts as "Three Different Options"

Three options must be **meaningfully distinct** — different mental models, not the same idea in three colors.

| Bad: same idea, different paint | Good: distinct mental models |
|---|---|
| Three navbar variants with different button colors | Top nav vs side nav vs command bar |
| Three login screens with different field layouts | Email/password vs SSO-first vs passwordless link |
| Three onboarding flows with different illustrations | Self-serve tour vs in-product checklist vs human-assisted call |

**Test:** If a stakeholder picks one, do the other two die? If yes — they were real alternatives. If they could all coexist as small variants — they were paint.

## When to Use

**Always:**
- Before any design review or share
- When you catch yourself saying "the obvious answer is..."
- After stakeholder/PM pushes a specific solution
- When stuck on one idea

**Exceptions (ask your partner explicitly):**
- A/B testing a known variant against control (the alternative is already production)
- Pure execution work (color tweak, copy fix) where the decision was already made with options

## The Process

1. **Name the design question.** Not "design a settings page" but "how do users find and change preferences they set months ago?"

2. **Generate at least three distinct directions.** Use these prompts to escape the first idea:
   - **Conservative** — minimum-risk version, builds on existing patterns
   - **Native** — what the platform/system would suggest (iOS HIG, Material, your design system)
   - **Provocative** — break a constraint deliberately ("what if there's no settings page?")

3. **State the tradeoff for each.** What does each option optimize for? What does it sacrifice?

4. **Pick a recommendation.** Three options *with* a recommendation is sharper than three options as a multiple-choice quiz.

5. **Bring all three to the review.** Not just the recommended one. Stakeholders need to see what was rejected and why.

## Output Template

```
Design question: [the question, not the feature]

Option A — [Conservative]
- Tradeoff: optimizes for X, sacrifices Y
- Best when: ...

Option B — [Native]
- Tradeoff: optimizes for X, sacrifices Y
- Best when: ...

Option C — [Provocative]
- Tradeoff: optimizes for X, sacrifices Y
- Best when: ...

Recommendation: [B], because [the deciding tradeoff for this user/context].
```

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "I already explored options in my head" | Articulate them or you didn't. |
| "Three options will confuse stakeholders" | Stakeholders are confused by *one* option that hides assumptions. Three exposes them. |
| "The PM already picked the approach" | The PM picked a *direction*. Designers explore *executions*. |
| "I don't have time for three" | One bad direction wastes more time than three quick sketches. |
| "Two of these are obviously wrong" | Then they show why the third is right. Bring them. |
| "I'll just iterate after feedback" | Iteration without alternatives = guessing harder. |
| "There's only one way to do this" | If true, you're not designing — you're documenting. |

## Red Flags — STOP and Generate More

- About to show one direction
- "It's obvious what we should do"
- "Stakeholders just need a quick answer"
- "I'll just pick one and we'll iterate"
- "The other options would be silly"
- "I already considered alternatives"

**All of these mean: stop. Generate two more distinct directions before continuing.**

## Pairs With

- `brainstorming` — invokes this skill at step 5 (propose 2-3 approaches). Options without a framed problem solve the wrong question; brainstorming does the framing first.
- `critiquing` — once options exist, critique each before recommending.
- `writing-spec` — the chosen option + alternatives feed the spec's "Approach" and "Alternatives considered" sections.
- `presenting` — when you carry options into a stakeholder meeting, presenting tells you how to structure the conversation.
