---
name: verifying-before-shipping
description: Use when about to claim design work is complete, ready, approved, or shippable - before saying "done", before stakeholder share, before handoff to engineering, before closing a project
---

# Verifying Before Shipping

## Overview

A verification pass before declaring design work done. The end of a project is when discipline is weakest — deadlines are pressing, you've stared at the file for too long, and "good enough" feels like enough. This skill exists for that moment.

**Saying "done" is a claim. Verify before claiming.**

## The Iron Law

```
NO "DONE" WITHOUT THE CHECKLIST
```

Verbal "done", written "done", "ready for review", "ready for handoff", "approved to ship" — all of these require the verification pass. No exceptions for:
- "Tiny" projects
- Projects where "everyone knows what it does"
- Projects you've done before
- Projects where the PM/manager said "ship it"

If you find yourself about to declare done without the checklist, **stop and run the checklist.**

## When to Use

- Before saying "design is complete"
- Before sharing with stakeholders for approval
- Before handoff to engineering
- Before closing a ticket / project
- Before posting in Slack: "design is done"
- Before moving to the next project

## The Verification Checklist

Run through every item. Mark each: ✅ passed / ⚠️ partial / ❌ failed / N/A.

### Process verifications

- [ ] **Brainstorm artifact exists.** The framing from `brainstorming` is captured (in spec, ticket, or doc).
- [ ] **Three options considered.** `exploring-options` was run. Alternatives are documented, not just in your head.
- [ ] **Direction has explicit approval.** Stakeholder said "yes, this direction" — not "looks good" (polite ≠ approved).
- [ ] **Spec exists (if cross-functional).** `writing-spec` ran or was deliberately skipped (and skip was justified).

### Design verifications

- [ ] **Critique pass complete.** `critiquing` was run on the design — fit, hierarchy, intent, narrative, edge cases, system fit.
- [ ] **Design QA pass complete.** `design-qa` was run — alignment, spacing, type, contrast, states, tokens.
- [ ] **All states defined.** Every interactive element: default, hover, focus, active, disabled. Plus loading, error, success, empty where applicable.
- [ ] **Edge cases addressed.** Empty data, long content, slow network, no permissions, error recovery.
- [ ] **Accessibility considered.** Keyboard nav, focus order, contrast, screen-reader labels for non-obvious controls.
- [ ] **Responsive / multi-platform.** If the design ships on multiple breakpoints or platforms, each is designed (not just mocked at one size).
- [ ] **Copy is real.** No Lorem ipsum. Real strings for errors, empty states, microcopy.

### System verifications

- [ ] **Tokens used.** Colors, spacing, type from system variables, not raw values.
- [ ] **Components instances, not detached copies.** Edits go back to the system, not into one-off forks.
- [ ] **No drift from the system without justification.** If you broke a pattern, the reason is documented.

### Stakeholder verifications

- [ ] **Stakeholders aligned.** PM, Eng, design peers have seen and approved the work.
- [ ] **Open questions are listed, not hidden.** The questions you don't have answers to are visible at the bottom of the spec/Figma.
- [ ] **Handoff doc exists (if applicable).** `handoff` skill output is ready — engineering won't be guessing.

### Honesty verifications

- [ ] **You didn't smooth over uncertainty.** If something is risky or you're unsure, it's surfaced — not hidden under polished pixels.
- [ ] **You haven't been staring at this for so long you stopped seeing it.** If yes, sleep on it or have a peer do a 10-min review before declaring done.

## What "Failed" Means

If any item is ❌, **work isn't done**. You can:
- Fix it now (preferred)
- Justify the skip explicitly in writing (acceptable if reasoning is real)
- Push the deadline (last resort)

What you cannot do: claim "done" with checklist items failing. That's lying to your stakeholders.

## Output

When verification passes, declare done with the checklist:

```
## Verification — [project name] — [YYYY-MM-DD]

Process: ✅
Design: ✅
System: ✅
Stakeholder: ✅
Honesty: ✅

Ready for: [handoff / share / approval]

Open items deferred to follow-up:
- [item, owner, when]
```

If verification doesn't pass, write what failed and what's left:

```
## Verification — [project name] — NOT YET READY

Failed: [item] — [why] — [action to fix]
Failed: ...

Estimated time to ready: [hours / days]
```

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "PM said ship it" | PMs ship features. Designers verify designs. Different jobs. |
| "Everyone knows what it does" | They don't. The next designer will not know what you didn't write down. |
| "It's a small change" | Small changes still need state coverage, accessibility, and a real copy pass. |
| "We can fix issues in a follow-up" | Follow-ups don't happen. They get prioritized away. Fix now. |
| "The Figma file is the source of truth" | Then the checklist verifies the Figma file. The pass still happens. |
| "I'll trust the engineering review to catch issues" | Engineering reviews for buildability, not design quality. They're different audits. |
| "I've done this dozens of times, I know it's right" | Confidence is the most reliable predictor of skipped checks. |

## Red Flags — STOP

- About to type "design is done" without running the checklist
- "Just ship it, we can iterate"
- "Verification is overkill for this"
- Skipping the honesty section because "obviously I wasn't dishonest"
- About to close a ticket without an "open items deferred" list

**All of these mean: stop. Run the checklist.**

## Pairs With

- `critiquing` and `design-qa` — these feed the design verification section
- `handoff` — verification gates the handoff. Don't hand off until verified.
- `presenting` — verification gates the share. Don't present un-verified work.
- `writing-spec` — verification confirms the spec is complete and current
