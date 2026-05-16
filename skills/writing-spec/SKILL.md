---
name: writing-spec
description: Use when capturing a design direction in a written document - design spec, light PRD, or design brief. Fires after brainstorming reaches an approved direction, or when stakeholders ask for written documentation
---

# Writing Spec

## Overview

Produce a **light design spec / PRD** — a 1-2 page document a designer can maintain, that captures what's being built and why. Not the 10-page engineering PRD; not a marketing brief; the designer's-eye document that holds the decision so it doesn't drift.

This skill assumes brainstorming reached an approved direction. Inputs come from `brainstorming` (framing, chosen direction) and `exploring-options` (alternatives considered).

## When to Use

**Use when:**
- Brainstorming reached an approved direction and the project will involve multiple sessions / cross-functional review
- Stakeholders ask for a written spec
- You'll need to remember this decision in a month (most projects)
- The project will hand off to engineering and benefits from a single source of truth

**Skip when:**
- True throwaway work (one-off copy tweak, color update)
- The decision is already documented in a ticket / brief that's adequate
- A heavyweight PRD is owned by PM and yours would duplicate

## What It Produces

A markdown document, ~1-2 pages, saved to `docs/specs/YYYY-MM-DD-<topic>-spec.md`. Structure below.

The spec is **maintained, not written-and-forgotten** — update it when scope shifts, decisions change, or open questions resolve.

## The Spec Template

```markdown
# [Feature / Project Name] — Design Spec

**Date:** YYYY-MM-DD
**Owner:** [designer name]
**Status:** Draft / Approved / Building / Shipped
**Related:** [ticket / brief / Figma link]

## Problem
[1 paragraph. The user/business problem, not the feature. Why does this matter now?]

## Users & JTBD
[Who is this for, what are they trying to accomplish, when, with what constraints.]
- **Primary user:** [role, context]
- **Secondary user(s):** [if any]
- **Job to be done:** [user's words, present tense]

## Approach
[2-3 paragraphs. What we're doing and why this approach over the alternatives.]

### Alternatives considered
[Brief — pulled from exploring-options. For each: name, tradeoff, why not chosen.]

## Key Flows / Screens
[Bulleted list, each with 1-2 sentence description and a link to the Figma frame.]

- **[Flow/Screen name]** — [what it does] — [Figma link]
- ...

## Key Design Decisions
[The 3-5 most important decisions that shape this work. Document them so future-you doesn't re-litigate.]

- **Decision:** [the choice made] — **Why:** [reasoning] — **Alternatives:** [what was considered]
- ...

## Constraints
- **Platform:** [iOS / Android / web / responsive / etc.]
- **Brand / system:** [design system, brand guidelines, components used]
- **Regulatory / compliance:** [if relevant]
- **Technical:** [eng constraints affecting design]
- **Timeline:** [deadline, milestones]

## Success Criteria
[How we'll know it worked. Behavior, metric, or qualitative signal.]
- [criterion 1]
- ...

## Out of Scope
[What we deliberately are NOT solving in this project. As important as what's in.]
- [thing not solved 1]
- ...

## Open Questions / Risks
[Anything unresolved. Track here so it doesn't go in the design and surprise people later.]
- [question 1] — [who owns answering it]
- ...

## Handoff Pointers
[High-level pointers for engineering. Full handoff details live in the Figma file and the `handoff` skill output.]
- States: [link to states in Figma]
- Edge cases: [link or list]
- Motion: [link or list]
- Accessibility: [notes]

---

## Changelog
- YYYY-MM-DD — initial draft
- YYYY-MM-DD — [what changed]
```

## The Process

### 1. Gather inputs

Before writing, collect:
- The framing from `brainstorming` (problem, users, JTBD, constraints, success criteria)
- The options from `exploring-options` (3+ directions with tradeoffs)
- The Figma file(s) — get frame links for each key screen
- Any existing brief / ticket / prior decision docs

If brainstorming hasn't happened yet, **stop and invoke `brainstorming` first.** You can't write a spec for an un-framed problem.

### 2. Draft each section

Work through the template top to bottom. Lean concise — if a section is empty or trivial, write "n/a" and move on. Don't pad.

### 3. Self-review pass

Before showing to the user, look at the draft with fresh eyes and check:

1. **Placeholders:** any "TBD", "TODO", "[fill in]"? Resolve them or convert to open questions.
2. **Internal consistency:** does the approach match the framing? Does the success criterion match the problem?
3. **Scope:** is this one focused project, or does it secretly contain three? If three, split.
4. **Ambiguity:** could any line be interpreted two ways? Pick one and make it explicit.
5. **Honesty about uncertainty:** are open questions actually listed, or did you smooth them over?

Fix issues inline. Don't ask the user to fix things you can fix yourself.

### 4. Save the doc

Write to `docs/specs/YYYY-MM-DD-<topic>-spec.md`. Create the directory if it doesn't exist.

Filename rules:
- Date in `YYYY-MM-DD` format (sortable)
- Topic in kebab-case, brief but specific (`checkout-progress-bar` not `checkout-improvements`)
- `-spec.md` suffix

If a spec already exists for this topic, **update it** rather than creating a new one. Add a changelog entry.

### 5. User review

Present the saved doc and ask:

> "Spec saved to `[path]`. Please review and let me know what to change. I've flagged [N] open questions at the bottom."

Wait for feedback. Update inline. Re-save.

### 6. Terminal state

Spec is ready when the user has approved it. From there, the work continues:
- Design execution in Figma (you've already done this if you wrote the spec post-design; some teams write the spec before)
- `critiquing` and `design-qa` on the executed design
- `presenting` for stakeholder review (the spec becomes the script's source material)
- `handoff` to engineering (spec + Figma = the handoff package)

## What This Skill Is NOT

- **Not an engineering PRD.** Light, designer-maintained. If your org has a heavyweight PRD owned by PM, your spec complements it (linking) rather than replacing.
- **Not the Figma file.** The spec captures *decisions and reasoning*. The Figma file captures *the design itself*. They reference each other.
- **Not the handoff doc.** Handoff is for engineering implementation detail (every state, every redline). The spec is the higher-level context.
- **Not a write-once artifact.** Maintain it. Stale specs are worse than no specs.

## Common Pitfalls

- **Over-specifying.** If a section doesn't have content yet, leave it brief or write "n/a." Don't pad with platitudes.
- **Under-specifying open questions.** Designers hide uncertainty under polished prose. Surface it.
- **Confusing problem and feature.** "Add a progress bar to checkout" is a feature. "Users abandon checkout when they don't know what's left" is a problem. Spec leads with the problem.
- **Decisions without reasoning.** If you wrote "we chose X" with no "because Y", future-you will undo X without knowing why.
- **Out-of-scope list missing.** Naming what's NOT solved is the easiest way to prevent scope creep.

## Pairs With

- `brainstorming` — must precede this skill. Spec captures the brainstorm's output.
- `exploring-options` — alternatives section comes from this skill's output.
- `presenting` — the spec is source material for the stakeholder script.
- `handoff` — spec + Figma + handoff doc = the engineering package.

## Iteration Notes (v0.1)

The template above is the suggested baseline. Real projects will pressure it:
- Marketing-y projects may need an "Audience & messaging" section
- Compliance-heavy projects may need a "Regulatory checks" section
- B2B SaaS may need a "Role/permission impact" section

Don't force-fit. Adapt the template, save the variations, and let real usage shape the v0.2 template.
