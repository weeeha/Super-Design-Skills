---
name: writing-case-study
description: Use when packaging shipped design work into portfolio + career artifacts - after a feature has shipped, when updating portfolio, when prepping for a job change, or when asked "tell me about a project you're proud of"
---

# Writing a Case Study

## Overview

Turn finished, shipped design work into four related artifacts in one pass:

1. **Case study** — long-form portfolio piece with visuals
2. **Resume bullet** — one compressed line of impact (3 variants to pick from)
3. **LinkedIn post** — medium-form, process + reflection (~300-500 words)
4. **Interview pitch** — 2-min STAR-format verbal story

All four derive from one narrative arc: **Problem → Approach → Result → Reflection**. The skill's main job is helping you *extract* that arc through structured questions, then compress/expand into each format.

## When to Use

- A feature has shipped (or is about to) and you want to package it
- You're updating your portfolio site
- You're prepping for a job change / interview loop
- LinkedIn drought — you want to post something substantial
- A recruiter asked for "a project you're proud of"
- You did good work months ago and never wrote it up

**Don't use:**
- Mid-project — wait until something has shipped or reached a stable milestone
- For NDA-locked work you can't share publicly (you can still do interview prep, but skip portfolio/LinkedIn outputs)
- For team projects where you don't have a clear individual contribution

## What This Skill Doesn't Do

- Generate fake metrics or impact
- Write the case study WITHOUT your input (this is collaborative — the questions exist for a reason)
- Replace your judgment on what's portfolio-worthy
- Handle NDA decisions for you — you decide what's shareable, the skill helps frame it

## The Process

### Phase 1 — Gather existing artifacts

Before asking questions, scan for material you've already produced. Saves rework.

Check for:
- **`SuperDesign:writing-spec` output** at `docs/specs/*-<topic>-spec.md` → pulls problem framing, constraints, success criteria
- **`SuperDesign:exploring-options` output** → alternatives considered + tradeoffs
- **`SuperDesign:presenting` script** → stakeholder framing
- **`SuperDesign:verifying-before-shipping` checklist** → impact / honesty checks
- **Figma file** via `figma-remote:get_screenshot` → visuals for the case study

If those exist, summarize what you pulled and tell the user:

> "I found a spec + 3 options doc for this project. I'll use them to prefill problem framing, constraints, and alternatives. Skip those questions unless you want to add."

If nothing exists, all 12 questions go through Q&A.

### Phase 2 — Structured Q&A (one question at a time)

12 questions across the arc beats. Ask **one at a time**, multiple-choice when possible. User can skip with "don't have that" or "skip" — adapt and continue.

**Problem (3 questions)**

1. *"What was the user or business problem? Be concrete — not the feature, the underlying issue."*
   - Bad answer to push back on: "Users wanted a better checkout"
   - Good: "Users abandoned checkout when they couldn't tell if their card type was supported. Support tickets had spiked 40% over 3 months."

2. *"Who was affected and how?"*
   - Push for specificity: which user segment, which moment, what they were trying to do.

3. *"Why did this matter NOW — what made it the right project to take on?"*
   - Tests whether you can defend project selection.

**Approach (3 questions)**

4. *"What was YOUR role, specifically? What did the team do vs what did you do?"*
   - Push back on "we" answers. Force individual contribution clarity.

5. *"What alternatives did you consider and reject? Why?"*
   - If user says "none", probe — "really, you went straight to one solution?"

6. *"What was the key insight or decision that shaped the final direction?"*
   - The thing only someone who actually did the work would know.

**Result (3 questions)**

7. *"What shipped? Be specific."*
   - Feature scope, screens, components.

8. *"What changed for the user or business? Even if you don't have numbers — what's the qualitative shift?"*

9. *"What metrics or signals indicated success? Conversion, support tickets, qualitative feedback, internal stakeholder reaction?"*
   - "No data" is fine — but say so explicitly. Don't fake numbers.

**Reflection (3 questions)**

10. *"What would you do differently if you started over?"*
    - Tests honesty. If they say "nothing", probe gently.

11. *"What did you learn — about users, the domain, design craft, the org, or yourself?"*

12. *"What surprised you?"*
    - Often the most interesting answer.

### Phase 3 — Draft the case study

Use the answers + pulled artifacts to draft the main document at `docs/case-studies/<topic>-YYYY-MM-DD.md`:

```markdown
# <Project Title>

> One-sentence pitch: <problem in a phrase>, <approach in a phrase>, <outcome in a phrase>.

![hero](./assets/<topic>-hero.png)

**Role:** <your role>
**Team:** <team / collaborators>
**Timeline:** <duration>
**Status:** Shipped <date> / In progress

---

## The problem
<2-3 paragraphs. From Q1-Q3. Concrete, with the user/business stakes.>

## Constraints
<from spec if available, otherwise from Q&A>
- ...

## Approach
<2-3 paragraphs. From Q4-Q6. What you specifically did, what alternatives you weighed.>

### Alternatives considered
<table or list — from exploring-options if available, otherwise from Q5>

| Direction | Tradeoff | Why not chosen |
|---|---|---|
| ... | ... | ... |

## What shipped
<screens, key components, link to Figma or live product if shareable>

![screen 1](./assets/<topic>-screen-1.png)
![screen 2](./assets/<topic>-screen-2.png)

## Impact
<from Q7-Q9. Numbers if available. Quotes if available. Qualitative if neither.>

## What I learned
<from Q10-Q12. Honest. One paragraph each for the strongest insights.>

## Tools & skills
- <list — Figma, design system, research methods, collaborations>
```

### Phase 4 — Generate the 3 short-form outputs

Append to the same case study file (or print to chat, user's choice):

```markdown
---

## Career artifacts

### Resume bullet (pick one)

**Impact-led:**
"<verb> <scope>, <metric/result> through <approach>."

**Action-led:**
"Led <scope> of <project>, including <specific contributions>, resulting in <outcome>."

**Scope-led:**
"<Scope description> serving <user count>, where <your contribution> led to <outcome>."

### LinkedIn post (~300-500 words)

<Hook — 1-2 sentences, surprising claim or relatable pain>

<Setup — 2-3 sentences: context, your role>

<Key insight — what changed your thinking, one specific moment or finding>

<Outcome — concrete>

<Reflection — one sentence on what stuck with you>

<Soft CTA — a question or invitation>

<Hashtags: 3-5 relevant ones>

### Interview pitch (STAR — 90-120 seconds spoken)

**Situation** (15-20s):
<context, when, what was going on>

**Task** (10-15s):
<what you specifically needed to do>

**Action** (45-60s):
<what YOU did — focus on individual contribution + specific tradeoffs you weighed>

**Result** (15-20s):
<outcome, with numbers if possible>

#### Alternate framings (for common prompts)

**"Tell me about a project you're proud of":**
<lead with reflection, then condense STAR>

**"Describe a tough trade-off":**
<lead with the alternatives, then how you decided>

**"What would you do differently":**
<from Q10 reflection, framed as growth, not regret>
```

### Phase 5 — Self-review checklist

Before declaring complete, run through:

```
## Self-review — <project>

- [ ] Problem is concrete (not "experience was bad" or "users wanted X")
- [ ] YOUR role is specific (no "we"/"the team did Y" without naming what YOU did)
- [ ] Alternatives are mentioned (shows considered design, not first-idea-wins)
- [ ] Impact is specific (numbers OR concrete qualitative signal — not "users loved it")
- [ ] Reflection includes a real learning, not generic platitude
- [ ] No design jargon a recruiter wouldn't understand (or jargon is defined inline)
- [ ] No NDA violations — revenue figures, codenames, unreleased plans, confidential ratios
- [ ] Screenshots are real (not Lorem-ipsum placeholders)
- [ ] Hero image is set or noted as TBD
- [ ] One-sentence pitch at top is sharp (you could say it out loud and it sounds right)
```

Show the checklist to the user. Wait for sign-off.

### Phase 6 — Save and confirm

Final outputs:
- Main file: `docs/case-studies/<topic>-YYYY-MM-DD.md`
- Assets folder: `docs/case-studies/assets/<topic>-*.png` (user adds screenshots here)

If the user has a separate portfolio repo or CMS, surface that at the end:

> "Case study saved to `docs/case-studies/<topic>-2026-05-17.md`. If you maintain a separate portfolio site, you can copy this file there. Want me to also push it as a draft PR somewhere?"

Don't auto-push to a portfolio repo unless explicitly asked.

## NDA Handling

If at any point during Q&A the user mentions something that signals NDA territory (specific revenue, unreleased product, customer names you suspect aren't public), flag it:

> "FYI — you mentioned <X>. That sounds NDA-sensitive. For the portfolio/LinkedIn outputs I'll either omit, generalize ('a large fintech' instead of 'Acme'), or ask you. For interview pitch, you can be more specific since it's verbal. Let me know what you're comfortable with."

Default to generalization. User can opt into specificity per output.

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "I don't have metrics" | Then say so — qualitative signals work. Don't fake numbers. |
| "It was a team effort, I can't claim it" | Then write the bit YOU did. "I" not "we." |
| "It's too small to write up" | Smaller scope ≠ no story. Even component-level work has the arc. |
| "I'll write it later when I have time" | You won't. The skill exists to remove that excuse. |
| "It was kind of a failure" | Failures + clear reflection are strong case studies. Don't skip them. |
| "I don't remember the details" | Pull from artifacts. If nothing exists, write what you do remember and flag gaps. |
| "Just write me a great case study" | Won't work — the questions exist because YOUR input is the differentiator. Generic case studies read generic. |

## Red Flags — STOP

- About to write a case study without YOUR answers to the questions
- About to invent metrics that weren't real
- About to claim solo work that was team work
- About to share something NDA-sensitive without flagging it
- About to skip the reflection section because "it's too vulnerable"

## Pairs With

- `writing-spec`, `exploring-options`, `presenting`, `verifying-before-shipping` — this skill pulls from their outputs if they exist
- `figma-remote:get_screenshot` — for visuals
- `learning-a-domain` — if you're case-studying a domain you ramped into recently, that skill's output gives useful context

## Iteration Notes (v0.1)

Watch for in real usage:
- Are 12 questions too many? Most useful in practice are Q1, Q4, Q5, Q8, Q10. Consider compressing.
- Does the resume bullet generator produce specific-enough variants?
- Is the LinkedIn post format too uniform? Should it vary by topic?
- Does the interview pitch work for non-American hiring contexts (STAR is regional)?
- What's the failure mode — generic case studies, or hesitation to write at all?

Bring observations back. v0.2 should compress questions based on what gets skipped.
