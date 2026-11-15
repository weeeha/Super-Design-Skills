---
name: reading-analytics
description: Use when a design question needs numbers from product usage - "where do users drop off", "what does the data say", "check the funnel", "how many people use this feature", "analytics for this flow", "did the redesign work", a dashboard, export or metrics screenshot to interpret - or when about to redesign a flow without looking at how it performs today
---

# Reading Analytics

## Overview

Product analytics tell a designer **what happens and how often**. They never say why. This skill reads the numbers for one flow, from a design question, and ends in hypotheses and the cheapest way to check each.

Three rules carry the skill:
1. **A question first.** A dashboard read without a question produces observations nobody acts on.
2. **Every number has a count, a base and a date range.** "42% drop" means nothing. "1,310 of 3,120 users left at step 3, Oct 1 to 31" can be checked.
3. **Where, not why.** The data locates the problem. The cause is a hypothesis until people are watched or asked.

## When to Use

- Before redesigning a flow that is already live
- "Where are we losing people?"
- "Did the redesign work?"
- Someone shares a dashboard, a CSV export or a screenshot of a chart and asks what it means
- Choosing which of several problems deserves design time

**Don't use** for:
- Why people behave that way (`usability-testing`, `analyzing-interviews`)
- Building dashboards, writing warehouse queries or statistics beyond a sanity check. Bring in an analyst or a data tool
- Business reviews of revenue or growth metrics

## What You Need

Ask what exists before anything else:

| Input | What it allows |
|---|---|
| A connected analytics tool | The full process below |
| A CSV or spreadsheet export | The full process, on what was exported |
| Dashboard screenshots or pasted numbers | Steps 1, 4, 6 and 8, on the numbers shown. Steps 2, 3, 5 and 7 need access: list them under "Not verified" |
| Nothing | Skip to step 9 and produce a measurement plan |

Also ask for the event definitions, or who owns them. An event name is not a definition.

## The Process

### 1. Write the question and the decision

```
Question: [what we need to know about this flow]
Decision it informs: [what we will design or not design]
Flow: [first step] to [last step]
Date range: [from, to]
```

### 2. Map the flow to events

| Step | Screen | Event | What exactly fires it |
|---|---|---|---|

Steps with no event are blind spots. List them. Do not guess what happens there.

### 3. Check the data before reading it

- Is the unit users, sessions or events? Do not mix them in one funnel
- Is the date range long enough to cover a weekly cycle?
- Did tracking or the product change inside the range? Releases and renamed events break comparisons
- Are internal users and test accounts excluded?
- How many users enter the flow? State it

Anything that could not be verified goes in the output under "Not verified".

### 4. Build the funnel

Users at each step, the number lost, and the step rate. Find the biggest loss in **users**, not the worst percentage: a 60% drop of 50 users matters less than a 12% drop of 9,000.

### 5. Split the biggest loss

Choose two or three splits before looking, the ones the design question suggests: new and returning, device, plan or role, entry point. The more splits tried, the more likely one differs by chance, so report how many were tried. Report a split only when the groups differ and each has enough users. As a rule of thumb, under about 100 users per group is a hint, not a finding.

### 6. Open the screen

Go to the step where people leave and look at it as they would. Pair the number with what the screen asks for: fields, decisions, waiting, unclear next step. If available, add time on step (median, not average), error counts and repeated clicks.

### 7. Compare over time, carefully

"Did the redesign work?" needs all of these:
- The same definition before and after
- At least two full weeks on each side, so weekly cycles cancel out
- A list of whatever else changed in the period: pricing, campaigns, season, a different mix of users

If one is missing, say the comparison is inconclusive, and why. This skill does not test statistical significance. When the decision rests on a small difference, ask an analyst before calling it.

### 8. Write findings, then hypotheses

A finding is a number with its base and range. A hypothesis is a possible cause, labeled as one, with the cheapest way to check it:

> Finding: 1,310 of 3,120 users left at "Add team members", Oct 1 to 31.
> Hypothesis: the step reads as required, and solo users have nobody to add.
> Check: five solo users in a `usability-testing` session, or make the step skippable and compare.

### 9. Say what to measure next

List the missing events and what each would answer. This is the whole output when no data exists yet, and it belongs in `handoff` as a requirement.

## Output Template

```
## Analytics read - [flow] - [date range]

**Question:** ...
**Decision it informs:** ...
**Source:** [tool / export / screenshots]. Unit: [users / sessions]
**Not verified:** [definitions, exclusions, tracking changes]

### Funnel
| Step | Users | Lost | Step rate |
|---|---|---|---|

### Where it breaks
- [Step]: [count] of [base] left. [What the screen asks of the user]

### Who it affects
- [Split]: [group A count of base] against [group B count of base]

### Findings
1. [number, base, range]

### Hypotheses (not findings)
| Hypothesis | Cheapest check |
|---|---|

### Blind spots and what to measure
- [step with no event] - [what the event would answer]
```

## Common Pitfalls

- **A percentage with no base.**
- **Reading the default date range** the dashboard happened to open with.
- **Mixing users and sessions** in one funnel.
- **Averages for time.** A few very long sessions drag the average. Use the median.
- **Calling every drop a problem.** Some steps are supposed to filter people out.
- **Looking only at people who finished.** The ones who left are the subject.
- **Stating a cause.** The data did not give one.
- **Before and after with no list of what else changed.**

## Pairs With

- `usability-testing` - checks why people leave at the step the funnel points to.
- `analyzing-interviews` - checks the hypothesis by asking about the last time it happened.
- `brainstorming` - the funnel sharpens the problem framing.
- `researching` - outside benchmarks are context only; products define their funnels differently.
- `handoff` - the measurement list becomes an engineering requirement.
- `presenting` - a finding with its count and base is the "what we learned" beat.

## Iteration Notes (v0.1)

Written from method, not from session evidence: this work was rare in past sessions. Watch for:
- Which input is most common in practice: a connected tool, an export or screenshots
- Whether the 100-user rule of thumb is right for the product's traffic
- Whether hypotheses actually get checked, or get treated as findings downstream
