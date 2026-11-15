---
name: researching
description: Use when the user asks to research a product, competitor, pattern or audience before designing - "research X", "how do others do Y", "what do users like and complain about", "find references", "benchmark this flow", "any examples of Z", "what is the usability of X based on user feedback" - or when about to design a common pattern without looking at how existing products solve it
---

# Researching

## Overview

Design research answers a design question with evidence and ends in what it means for the work. It is not a market report, and it is not a pile of links.

Two rules carry the skill:
1. **A question first.** Research without a question collects forever.
2. **Observed and inferred stay separate.** What a product does, or what a user wrote, is observed. What it means is yours, and labeled as yours.

`learning-a-domain` explains how a vertical works. This skill looks at specific products, patterns and user voices inside it.

## When to Use

- Before designing a pattern that other products have already solved (tables, onboarding, permissions, inboxes, pricing pages)
- "What do people like and hate about X?"
- A stakeholder says "do it like [competitor]" and nobody has looked closely at what the competitor does
- Gathering references before `exploring-options`
- Preparing the evidence for a research readout in `presenting`

**Don't use** for:
- Understanding a whole vertical (`learning-a-domain`)
- Research with the team's own users: interviews, usability tests, surveys. This skill reads what is already public. For the team's own users, see `usability-testing` and `analyzing-interviews`.
- Company or job research

## Pick the Kind of Research

| Kind | The question | Sources | Default budget |
|---|---|---|---|
| **Pattern research** | How do 4 to 6 products solve this one flow? | The products themselves, their docs, public demos | 4 to 6 products, one flow each |
| **Product teardown** | How does this one product work, end to end? | The product, its help center, changelog | 1 product, up to 15 screens |
| **User voice** | What do users praise and complain about? | Reviews, forums, community threads, support boards | 20 to 30 posts by separate people |
| **Reference gathering** | What does good look like for this screen or interaction? | Live products first, galleries second | 8 to 12 examples |

State the kind and the budget before starting. Stop at the budget and report what was covered. Going past it is the user's call.

## The Process

### 1. Write the question and the decision it serves

```
Question: [what we need to know]
Decision it informs: [what we will do differently depending on the answer]
Kind: [pattern / teardown / user voice / references]
Budget: [how many products, screens, posts or examples]
```

If no decision depends on the answer, say so and ask whether the research is still wanted.

### 2. Choose the set

For pattern research, pick 4 to 6 products on purpose: the market leader, a direct competitor, one known for craft, and one from outside the category that solves the same problem. Say why each is in the set.

### 3. Collect evidence

Each item of evidence has three parts: **the source** (link), **the date** (of the page, review or version), and **what it shows**.

- Products: look at the real thing when a browser is available. Take a screenshot of each step. A marketing page is evidence of what the company claims, not of how the product behaves. Without a browser tool, link to the exact page, describe what it shows, and mark the item "not seen directly": medium confidence at most.
- User voice: quote word for word, with the link. Count how many separate people say the same thing. One loud thread is one data point.
- Record what could not be reached: sign-in walls, paid tiers, mobile-only flows.

### 4. Sort before you interpret

- **Patterns:** seen in N of M products. Name which.
- **Outliers:** one product does it differently. Describe what they gain and what they pay for it.
- **Complaints and praise:** ranked by how many separate sources raise them.

### 5. Write the implications

Three statements, each tied to evidence above it:

> Because [evidence], our design should [do / avoid / test] [specific thing].

An implication with no evidence behind it is an opinion. Move it to "Open questions" or drop it.

### 6. Mark confidence and limits

- *(High: seen directly in the product, or raised by many separate users)*
- *(Medium: from documentation or a few sources)*
- *(Low: inferred, or from a single source. Verify)*

Always state the sample: how many products, how many reviews, from which dates.

## Output Template

```
## Research - [topic] - [kind] - [date]

**Question:** ...
**Decision it informs:** ...
**Looked at:** [N products / N sources], dated [range]. Could not reach: [...]

### What we saw
| Product | How it handles [the flow] | Screenshot or link |
|---|---|---|

### Patterns
- [Pattern], in N of M: [which]. (confidence)

### Outliers
- [Product] does [X] instead. Gains: ... Pays: ...

### What users say   (user voice only)
| Theme | Separate sources | In their words | Link |
|---|---|---|---|

### So for our design
1. Because ..., we should ...
2. Because ..., we should avoid ...
3. Because ..., we should test ...

### Open questions (need our own users or the team)
- ...
```

Readable in five minutes. Screenshots and long quote lists go in an appendix or a board, not the summary.

## Common Pitfalls

- **Collecting without a question.** Forty screenshots and no finding.
- **Gallery-driven research.** Shots from design galleries show what looks good in a thumbnail, not what works in use. Live products first.
- **Copying the leader.** "The market leader does it" is a pattern, not a reason. Their constraints are not yours.
- **One source read as a trend.** Count separate people.
- **Old evidence.** A 2022 review of a product redesigned in 2025 describes a different product. Date everything.
- **Invented or tidied quotes.** Word for word, with the link, or leave it out.
- **Stopping at findings.** The implications are the deliverable.

## Pairs With

- `learning-a-domain` - run it first in an unfamiliar vertical; it tells you which products and flows are worth researching.
- `brainstorming` - research feeds the problem framing. When the user asks for research, do the research; do not open a brainstorm first. Inside a brainstorm, this skill is called when a question about existing products comes up.
- `exploring-options` - the patterns define what "conservative" means here; the outliers suggest the provocative option.
- `sketching` - sketch after the patterns are known, not before.
- `presenting` - the research readout meeting type takes this output directly.

## Iteration Notes (v0.1)

Written from session evidence: the recurring asks were "research [product], how is its usability based on user feedback" and "research on user feedback, what people like a lot and what the complaints are". Watch for:
- Whether the budgets hold, or research keeps running past them
- Which sources turn out to be unreachable by the tools in use
- Whether the three implications get used in the design that follows
