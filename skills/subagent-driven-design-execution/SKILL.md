---
name: subagent-driven-design-execution
description: Use when 3+ distinct design directions need parallel development before convergence - when each option from exploring-options deserves its own deep mockup, when comparing approaches requires more than sketches
---

# Subagent-Driven Design Execution

> **v0.1 — experimental.** This skill is borrowed-pattern from upstream `superpowers:subagent-driven-development` and adapted for design exploration. The workflow hasn't been adversarially tested yet. Use it, then bring back what worked and what didn't.

## Overview

When `exploring-options` produces 3+ meaningfully distinct directions and you need to develop each one to "compare-able" fidelity before converging, dispatch each direction to its own subagent. They develop in parallel; you (or the main agent) reviews and converges.

This isn't for every option-comparison. Most option comparisons can stay at sketch/wireframe fidelity. Use this skill when the comparison is consequential and the directions are different enough that sketches won't tell you which to pick.

## When to Use

**Use when:**
- 3+ directions from `exploring-options` are genuinely distinct (not paint variants)
- The decision between them is high-stakes (architecture, primary nav, core flow)
- Sketches alone won't be enough to compare — you need real layout/copy/interaction
- You have time to develop in parallel (a few hours, not 5 minutes)

**Don't use when:**
- Options are minor variations (color, copy, layout shift)
- Only one option is plausible and the others are foils
- The decision is small enough that prototyping is overkill
- You're already converging on one direction in conversation

## The Process

### 1. Define the comparison frame

Before dispatching, agree on what makes a direction "good" for this decision:
- What user task is being optimized for?
- What metric/quality matters?
- What constraints must each direction satisfy?

This frame travels with each subagent so they don't drift into different conversations.

### 2. Brief each subagent identically

Each subagent gets:
- The framing (from `brainstorming`)
- The comparison frame (from step 1)
- Their assigned direction with the tradeoff it's optimizing for
- Explicit boundary: develop ONLY this direction, do not invent new ones
- Output format expected (e.g., wireframe + one-paragraph rationale + edge-case list)

Use the `Task` tool with `subagent_type: general-purpose`. Send each in the same message so they run in parallel.

### 3. Review the returns

When subagents come back:
- Read each output cold (don't blend them as you go)
- Apply the comparison frame to each
- Note where each succeeds, where each struggles
- Score against the frame

### 4. Synthesize

Possible outcomes:
- **One clear winner** — pick it, document why, move on
- **Hybrid emerges** — a direction's best move + another's structure. Note it, return to `brainstorming` to validate the hybrid is real (not a mash-up).
- **None work** — the frame was wrong, or the directions weren't right. Return to `exploring-options` with new constraints.

### 5. Document the decision

In the spec (`writing-spec`), the "Alternatives considered" section gets richer:
- Direction A — developed via subagent, here's what we saw, here's why not chosen
- Direction B — ...
- Direction C — ...

This makes future-you (and engineering, and the next designer) able to see what was actually tried, not just what was sketched.

## Output Template (for each subagent's brief)

```
You are exploring ONE design direction in parallel with other subagents
exploring different directions. Do not invent new directions.

## Framing (shared)
[problem statement, primary user, JTBD, constraints, success criteria —
copy from brainstorming output]

## Comparison frame (shared)
[the metric / quality we'll judge directions by]

## Your direction
**Name:** [e.g., "side-nav with collapsible groups"]
**Optimizes for:** [the tradeoff this option owns]
**Boundary:** Stay inside this direction. Don't shift to a different one
even if you think the others are better.

## What to produce
1. A wireframe-level mockup (text-described or sketched) of the key
   screen(s) for this direction
2. One paragraph: why this direction holds up under the comparison frame
3. One paragraph: where this direction struggles
4. A bulleted list of edge cases / states this direction needs to handle
5. Your honest confidence level (high / medium / low)

Do NOT:
- Compare yourself to the other directions (you don't know them)
- Propose merging with another direction
- Suggest the frame is wrong

Return everything in one response.
```

## Common Pitfalls

- **Skipping the frame.** Without a shared comparison frame, subagents drift into different conversations and their outputs aren't comparable.
- **Asking subagents to "be creative."** They'll diverge from the assigned direction. Constraint discipline matters.
- **Blending outputs as you read them.** Read each cold first. Then compare.
- **Treating this as a vote.** Subagents are exploring possibility, not voting. You synthesize.
- **Using when sketches would do.** Subagents are expensive; sketches are cheap. Default to sketches.

## What This Skill Is NOT

- Not for incremental design iteration (use the main agent in dialogue for that)
- Not for parallel screens of the same direction (just design them sequentially)
- Not for "let's try a bunch of things" — that's `exploring-options`, not subagent execution

## Pairs With

- `exploring-options` — provides the 3+ directions to dispatch
- `brainstorming` — provides the framing each subagent uses
- `writing-spec` — documents the parallel exploration in the alternatives section
- `verifying-before-shipping` — confirms the parallel exploration didn't leave loose ends

## Iteration Notes (v0.1)

Things to watch as this skill gets used:
- Do subagents actually stay inside their direction, or drift?
- Is the comparison frame stable, or do subagents reinterpret it?
- Is the time saved worth the parallelism overhead?
- What output format works best for synthesis?

Bring observations back. This skill will need v0.2.
