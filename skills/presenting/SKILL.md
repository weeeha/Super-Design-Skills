---
name: presenting
description: Use when preparing to show or present design work to stakeholders - a presentation, deck, slides, demo, pitch or walkthrough for internal crits, PM/Eng design reviews, exec/leadership reviews, user research readouts, customer/sales previews, or async loom/doc walkthroughs
---

# Presenting

## Overview

Turn finished design work into a stakeholder narrative. The work doesn't speak for itself. A good presentation tells the story: what problem, what we learned, what we tried, what we recommend, what we need from you.

Different meetings need different shapes. This skill picks the right structure for the meeting type and produces a talking script + the key question to ask.

## The Meeting Types

Six archetypes. Each has a different audience, decision ask, and pacing.

| Type | Audience | What they want | Decision ask |
|---|---|---|---|
| **Internal crit** | Design peers | Sharp feedback on the work | "Where is this weakest?" |
| **PM / Eng design review** | Cross-functional team | Alignment + tradeoffs + buy-in | "Are we ready to build this?" |
| **Exec / leadership review** | VP/director-level | Decision + risk + framing | "Approve direction X over Y?" |
| **User research readout** | Whoever ordered it | Findings → implications → recs | "What do we do about this?" |
| **Customer / sales preview** | Sales, CSM, sometimes a customer | Story + value + roadmap teaser | "Can we share this externally?" |
| **Async loom/doc walkthrough** | Anyone, asynchronously | Self-contained understanding | (Comment / approve in writing) |

**Ask the user which type** before generating the script. If unclear, propose the most likely two and ask.

**Start from the pack.** If a `meeting-pack` exists for this meeting, take the audience, the history and the open decisions from it instead of asking again. The pack's own meeting type is not one of the six above: still pick one, proposing the closest.

## The Universal Structure

These are the beats a presentation draws from. The meeting type decides which are kept and how long each gets:

1. **The hook** — why this matters right now
2. **The problem** — the framing from `brainstorming`
3. **What we learned** — research, data, constraints discovered
4. **What we tried** — options from `exploring-options`
5. **The recommendation** — the chosen direction + why
6. **The risks / open questions** — what could go wrong, what we don't know
7. **The decision ask** — what you need from this meeting

Different meeting types weight these beats differently, and some drop a beat entirely (an internal crit skips the hook). See sections below.

## Per-Meeting-Type Playbook

### Internal Crit (15-30 min, peers)

Goal: get sharp design feedback before stakeholders see it.

Beats:
- (skip hook)
- (very short framing — peers know the project)
- Show 2-3 options with tradeoffs
- Your current lean and *why you're uncertain*
- **Ask:** "Where is this weakest? What would you push back on?"

Tone: open, vulnerable. The worst crit is one that confirms what you already think.

### PM / Eng Design Review (30-60 min, cross-functional)

Goal: alignment on direction so engineering can scope.

Beats:
- Hook (1 min)
- Problem framing (2 min)
- What we learned, including any UX risks (3 min)
- Options considered (5 min)
- Recommendation + walkthrough (10 min)
- Tradeoffs / open questions (5 min)
- **Ask:** "Are we aligned to build this? What's blocking 'yes'?"

Tone: collaborative. Engineering will surface feasibility; PM will surface scope. Both are inputs.

### Exec / Leadership Review (15-30 min, senior stakeholders)

Goal: decision on direction. Often the only one of these you'll get.

Beats:
- Hook tied to business goal (30 sec)
- Problem in one sentence
- Recommendation FIRST (not last)
- Why this over alternatives (2-3 sentences each)
- Risk and mitigation
- **Ask:** "Approve direction X to move into build?"

Tone: confident, lean. Execs want the answer first, the reasoning second. Bury the lede and you lose the room.

### User Research Readout (30-45 min)

Goal: convert findings into shared understanding + action.

Beats:
- What we asked, who we asked, how many
- Top 3-5 findings (each with a representative quote or video)
- What this means for the work
- Recommendations
- **Ask:** "Which of these do we act on, in what order?"

Tone: evidence-led. Resist the urge to interpret too early — show the data, then the implication.

### Customer / Sales Preview (15-30 min)

Goal: equip the field. Or test reactions on a friendly external audience.

Beats:
- Hook tied to customer pain
- The problem we're solving (their words back at them)
- What it looks like (demo or walkthrough)
- What's coming next
- **Ask:** "Can we share this externally? Who would benefit from a preview?"

Tone: outside-in. Strip internal jargon. Talk to the customer, not the org.

### Async Loom / Doc Walkthrough

Goal: self-contained understanding for someone watching alone, later, distracted.

Beats:
- TL;DR up top (3 sentences max)
- Problem
- Walkthrough with explicit pointers ("notice the empty state here…")
- Recommendation
- **Ask in writing:** "Please comment / approve by [date]."

Tone: clear, structured, no surprises. Async means no chance to clarify in real time — over-document.

## The Output

For any meeting type, produce:

1. **A short script** (talking points, not paragraphs) — what to say beat by beat
2. **The decision ask** — one specific question to put on the table
3. **Anticipated pushback** — top 2-3 likely objections + how you'd respond
4. **What to cut if running long** — what's nice-to-have vs core
5. **A slide list**, when the meeting needs a deck (see Slides below)

### Output Template

```
## [Meeting Type] — [Topic] — [Date]

**Audience:** [names/roles]
**Time:** [duration]
**Decision ask:** [the one question]

---

### Beat 1 — [name] ([target time])
- talking point
- talking point
- (slide / artifact: [what to show])

### Beat 2 — ...

---

### Anticipated pushback

1. "Q: ..." → A: ...
2. "Q: ..." → A: ...

### Cut-list if running long
- [least-essential beat]
- [next least-essential]

### Slide list (only when there is a deck)
| # | Beat | Title (the claim, as a sentence) | Shows |
|---|---|---|---|
| 1 | Hook | ... | [real screenshot / frame / recording] |
```

## Slides (when the meeting needs a deck)

Script first, slides second. The slides illustrate the beats; they never replace the script.

1. **Ask where the deck lives.** Which tool (Figma Slides, Keynote, Google Slides, a doc), and whether the team has a template. Build it there when a tool for it is connected. Otherwise hand over the slide list for the user to fill.
2. **One slide per beat.** The walkthrough beat may take two or three. Rough sizes: exec review 5 to 7 slides, design review 8 to 12, internal crit none (open the file instead).
3. **The title is the claim.** "Three of five users missed the filter", not "Filters". Someone who reads only the titles should get the argument.
4. **One artifact per slide, and it is the real work.** A screenshot, a frame, a prototype recording. Do not redraw the work for the deck; redrawn work drifts from what will ship.
5. **Async decks stand alone.** Each slide gets one line of speaker note written out, because nobody will be there to say it.
6. **Rehearse the hard part.** You ask, the user answers: the five hardest questions this audience could raise, one at a time. Tighten each answer the user gives and put it into "Anticipated pushback", replacing the drafted response for that question.

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "The work speaks for itself" | It doesn't. People bring their own filter. |
| "I'll wing it, I know this work" | You'll over-explain and lose the decision. Script it. |
| "I'll just show Figma and talk through it" | That's a walkthrough, not a presentation. They're different. |
| "I don't know what decision to ask for" | Then you're not ready. Figure that out before the meeting. |
| "Everyone already knows the context" | They don't. Even the PM forgot since last week. |

## Red Flags

- About to walk into a meeting without a written decision ask
- "I'll just show them what I made"
- "I don't need to script it, I have slides"
- "I'll handle pushback live"

## Pairs With

- `brainstorming` — the problem framing feeds the "Problem" beat
- `exploring-options` — the options feed the "What we tried" beat
- `writing-spec` — if a spec exists, it's the source material for the presentation
- `design-qa` — fix QA blockers BEFORE the share. Don't present broken work.
- `meeting-pack` - comes before this skill. It supplies the audience, what was decided last time and the open decisions.
- `prototyping` - a clickable demo for the walkthrough beat.
- `sketching` - the sketches not chosen are material for the "What we tried" beat.
