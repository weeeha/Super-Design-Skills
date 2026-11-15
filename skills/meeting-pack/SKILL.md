---
name: meeting-pack
description: Use when a meeting or call is coming up and the user needs to walk in prepared - "prep for the call with X", "what did we decide last time", "what did we agree on", "questions to ask", "what should I bring", a 1:1, sync, standup, planning session, kickoff or review on the calendar, or a first meeting with someone new. Use even when no design work will be shown
---

# Meeting Pack

## Overview

Meeting prep is assembly, not authorship. Almost everything a designer needs before a call already exists somewhere: the notes from the last call, the state of the work, the invite. This skill gathers it into **one page the user edits for 15 minutes** instead of rebuilding from memory for two hours.

The rule that makes the page trustworthy: **nothing about a past meeting is written from memory.** Every "we decided" carries the date of the notes it came from, or it is marked as a guess.

## When to Use

- Any meeting on tomorrow's or today's calendar
- "What did we decide last time?" asked on its own, without a meeting coming (answer with the "Since last time" block only)
- A first meeting with a new person or team
- Before `presenting`: the pack supplies the audience, the history and the open decisions; `presenting` supplies the script

**Don't use** for:
- The script and slides for showing design work (that's `presenting`, after this)
- Job interviews
- Notes after the meeting. Out of scope here, though the next pack depends on those notes existing somewhere

## The Process

### 1. Identify the meeting

Find: who is in it, when, how long, and why it exists. Read the calendar invite if a calendar tool is connected. If the purpose is not in the invite and not obvious from past notes, ask the user one question: *"What do you need to walk out of this meeting with?"*

Then pick the type, because the type decides what the page leads with:

| Type | The pack leads with |
|---|---|
| **Recurring review or sync** | What was decided last time, and what changed in the work since |
| **1:1 with a manager** | What shipped, what is blocked, what the user needs from them |
| **Kickoff or first meeting** | Who these people are, what they own, what the user needs to learn from them |
| **Planning or prioritization** | The candidate items, a recommended order, and the tradeoff behind it |
| **Standup or status** | Three lines: done, next, blocked |
| **Decision meeting** | The one decision, the options, the recommendation. Then go to `presenting` |

If the meeting is in a domain the user has not worked in, run `learning-a-domain` now, before step 2, and add its vocabulary list to the pack.

### 2. Gather the sources, in this order

Use whatever is connected. Say at the bottom of the pack which sources were found and which were missing.

1. **Notes or transcripts of earlier meetings with the same people.** A meeting-notes tool, a notes folder, or files the user points at. Read the most recent one in full, not only its summary: summaries drop owners, numbers and exact wording.
2. **The next steps from that meeting, and where each stands now.** Check the real thing: the repo, the Figma file, the tracker, the pull requests. "I owed a revised table" is checked against the table.
3. **What changed in the work since then.** Commits, new frames, a new prototype link.
4. **Messages since the last meeting** (email, chat), only when the user asks or the thread is the reason for the meeting.

If there are no notes from earlier meetings, write "No record of earlier meetings found" and build the pack from the work and the invite. Do not reconstruct a history.

### 3. Write the pack

One page. Three minutes to read. Use the template below and delete any section that has nothing true to say.

### 4. Mark what is a guess

- A decision or commitment from a past meeting: cite the notes date.
- A question they will probably ask: mark whether it comes from past meetings (they asked it before) or is a guess.
- Anything inferred from a title, an attendee list or a file name: say so.

### 5. Hand on

- Design work will be shown and a decision is needed: run `presenting` next, and pass it the pack. The types in the table above are not `presenting`'s six meeting types; it picks its own.
- The pack shows a decision is needed but there is only one option to show: run `exploring-options` before the meeting, not after.

## Output Template

```
## Pack - [meeting name] - [date, time, length]

**With:** [names and roles]
**Why this meeting exists:** [one line]
**What I need out of it:** [1 to 3 outcomes, most important first]

### Since last time ([date of last meeting])
- Decided: ... (notes, [date])
- I owed: ... -> done / not done / changed, with a link
- They owed: ... -> status, if it can be checked

### What changed in the work
- ... ([link, frame or file])

### Decisions I need
1. [The question] - my recommendation: ... - if undecided: [what stalls]

### They will probably ask
1. "..." -> [short answer] (asked before / guess)

### My questions
1. ...

### Not ready - say so first
- ...

Sources: found [...]. Missing [...].
```

For a standup, the whole pack is three lines. For "what did we decide last time?", return only the "Since last time" block with its sources.

## The Standing Questions

Every pack answers these before it is done. Edit this list to match how you work; it is the part of the skill that should be yours.

1. What is the one thing I need from this meeting? (answered in "What I need out of it")
2. What did I promise last time, and can I show it? ("Since last time", the "I owed" line)
3. What will they ask that I cannot answer yet? ("They will probably ask" and "Not ready")
4. What am I showing, and is it in a state to be shown? ("What changed in the work" and "Not ready")
5. What happens next if nobody decides anything? ("Decisions I need", the "if undecided" part)

A question added here needs a place in the template too.

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "I remember what we decided" | The notes disagree more often than you expect. Read them. |
| "It's just a sync, no prep needed" | Syncs are where commitments get lost. Three lines are enough. |
| "There are no notes, I'll summarize what probably happened" | That is a guess presented as a record. Say there is no record. |
| "I'll put everything in so nothing is missed" | A pack longer than a page does not get read before the call. |
| "The summary of the last call is enough" | Summaries drop who owns what. Read the notes themselves. |

## Red Flags

- A "we decided" line with no date next to it
- A next step marked done without opening the thing it refers to
- The pack is two pages
- No "What I need out of it" line

## Pairs With

- `presenting` - comes after the pack when work is shown. The pack is its source for audience and history.
- `learning-a-domain` - comes before the pack for a first meeting in an unfamiliar vertical.
- `exploring-options` - when the pack shows a decision is coming and only one direction exists.
- `writing-spec` - a spec, when one exists, is the source for "what changed in the work".

## Iteration Notes (v0.1)

Written from session evidence: the recurring asks were "what did we decide on the last meeting?" and "give me top questions to ask him". Watch for:
- Whether the one-page limit holds for recurring reviews with long histories
- Which sources are usually missing at a new company in the first weeks
- Whether the standing questions get edited, or ignored
