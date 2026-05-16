---
name: learning-a-domain
description: Use when ramping into an unfamiliar product domain - permissions, fintech, claims, trades, healthcare, ad-tech, supply chain, education, etc. Produces a designer's-eye summary of the domain
---

# Learning a Domain

## Overview

Product designers rotate across verticals — one quarter you're designing for ad ops, the next for healthcare claims. This skill produces the **designer's-eye summary** of a domain: just enough to design competently, no more.

It does NOT produce a full business primer. It produces:
1. A short conceptual diagram (mental model of how the domain works)
2. A focused writeup of what a designer needs to know
3. A pointer to other skills you'll likely want for this domain

## What Counts as "Designer's-Eye"

Designers don't need to know everything an operator knows. They need to know:

- **Who the users are** — roles, titles, what they care about, what stresses them out
- **What jobs they're doing** — the verbs, the artifacts, the decisions
- **The vocabulary** — domain terms used differently than common English (a "policy" in insurance ≠ a "policy" in HR)
- **Common screens / flows** — what UI does this domain typically produce, and why
- **Regulatory / compliance constraints affecting UX** — what you CAN'T do or CAN'T skip
- **The pain points** — where current tools fail and where users improvise
- **The mental model** — how practitioners think about the domain (often different from outsiders)

It does NOT need to cover:
- Full financial / operational mechanics
- Internal company politics
- Sales/GTM motion
- Legal nuance beyond UX impact

If you find yourself going deep on those, you've drifted out of "designer's-eye." Pull back.

## The Process

### 1. Pick the right scope

Ask:
- *"What's the specific role you're designing for? (e.g., 'claims adjuster' not 'insurance')"*
- *"What's the immediate project? (helps prioritize which parts of the domain matter most)"*
- *"How deep do you need to go — 30 minutes of context or a week?"*

Most ramp-ups want the 30-min version first. Deeper context comes as the project unfolds.

### 2. Build the mental model (the diagram)

Produce ONE short diagram that maps:
- The actors (boxes) — who interacts with the system
- The artifacts (different shape) — what they create/consume/pass around
- The flow (arrows) — the typical sequence

**Example** (claims processing):

```
[Customer] ──files──> [Claim] ──reviewed by──> [Adjuster]
                          │                         │
                          │                         └──assigns──> [Examiner]
                          │                                            │
                          └────────────decisioned by──────────────────┘
                                            │
                                            ▼
                                       [Payout] or [Denial]
```

This is the spine. Keep it under 10 boxes. If you need more, you're zoomed in too far — pick the most relevant subsystem.

For diagrams, use:
- ASCII for simple flows (fits in chat)
- Mermaid for richer flows (renders in tools)
- A description suitable for a hand-drawn whiteboard if you're prepping a real session

### 3. Write the brief

After the diagram, produce a writeup organized as:

```
## Users & Roles
- [Role 1]: cares about X, measured on Y, time-pressed because Z
- [Role 2]: ...

## Vocabulary (where domain terms surprise outsiders)
- **Term**: how it's used here, vs. what an outsider might think
- ...

## Common Screens / Flows
- [Flow name]: typical UI, why this shape, what variations exist
- ...

## Regulatory / Compliance Notes (UX-relevant only)
- [Regulation]: design implication
- ...

## Where Current Tools Fail
- [Pain point]: workaround users have adopted
- ...

## Open Questions
- What I'm unsure about and should ask the team
```

Keep each section short. The whole brief should be readable in 5 minutes.

### 4. Recommend follow-on skills

End with: *"Given this domain, you'll likely want these skills next:"*

Examples:
- Fintech / claims / health → flag the user toward Anthropic's `legal:compliance-check` if installed, or note compliance is a critical thread
- Domain with a lot of states/flows → `exploring-options` will be heavily used
- Domain with regulatory UI requirements (consent, disclosures) → `design-qa` should include compliance checks
- Domain with novel workflows the team hasn't designed before → `presenting` for exec review will be important (more risk = more framing needed)

This isn't dogma — it's a nudge. The user can ignore the pointer.

### 5. Stay honest about confidence

Each section should include a confidence marker when uncertain:
- *(High confidence: derived from public regulation/widely known practice)*
- *(Medium: inferred from common patterns in similar domains)*
- *(Low: my guess — please verify with a SME)*

This protects the user from designing on bad intel.

## When to Use

- Starting a project in a domain you haven't designed for before
- Joining a new team in a vertical you're unfamiliar with
- Designing for a sub-domain inside a known area (e.g., you know fintech, new to crypto custody)
- About to do user interviews and want to sound credible

**Don't use** for domains you already know — re-summarizing wastes context.

## Common Pitfalls

- **Going too deep, too fast.** Resist the urge to explain everything. Designer's-eye = enough to design competently.
- **Borrowing too heavily from one source.** If your summary reads like one company's product, you've narrowed prematurely.
- **Asserting without flagging confidence.** Domain nuance is where you'll be wrong. Mark uncertainty.
- **Forgetting the "what you don't need" half.** Naming what's out of scope is as valuable as what's in.

## Pairs With

- `brainstorming` — once you have domain context, the brainstorm goes much faster. Invoke `learning-a-domain` before `brainstorming` for unfamiliar verticals.
- `presenting` — domain context helps you frame for exec reviews where the audience is also new to the space
- `exploring-options` — domain conventions inform what "conservative", "native", and "provocative" mean in this space

## Iteration Notes (v0.1)

This skill is intentionally light. As Nick uses it across domains, surface:
- Which domain summaries felt useful vs noisy
- Whether the diagram-first approach holds across domains
- What follow-on skill pointers were actually useful
- Whether confidence markers are read or ignored

Update the skill based on real usage, not assumptions.
