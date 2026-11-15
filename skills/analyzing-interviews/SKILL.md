---
name: analyzing-interviews
description: Use when there are user or stakeholder interviews to make sense of - "analyze these interviews", "what did people say in the interviews", "find themes in these transcripts", "synthesize the research calls", "summarize the customer calls", interview notes or recordings to process - or when a claim about what users want is being made from memory of a few conversations
---

# Analyzing Interviews

## Overview

Interviews become evidence only when they are analyzed the same way every time. This skill turns transcripts into themes that can be checked against the source, then into what they mean for the design.

Four rules carry the skill:
1. **Quotes are word for word**, with who said it and where in the transcript.
2. **Count people, not mentions.** One participant who raises something six times is one participant.
3. **What was said and what it means stay separate.**
4. **Contradictions stay in.** A participant who disagrees with the theme is data, not noise.

## When to Use

- A round of user or customer interviews is finished, or partly finished
- Stakeholder interviews at the start of a project
- Sales or support calls that someone wants mined for product insight
- "Users want X" is being repeated and nobody can say how many users

**Don't use** for:
- Sessions where people performed tasks, including the talk around the tasks (`usability-testing`)
- Public reviews and forum posts (`researching`, user voice)
- How many users behave a certain way (`reading-analytics`)
- What was decided in an earlier meeting (`meeting-pack`)
- Writing the interview guide. No skill in this plugin owns that yet

## What You Need

| Input | Strength | Note |
|---|---|---|
| Transcripts | Best | Quotes can be exact |
| Recordings, through a notes or transcription tool | Good | Get the transcript, not the tool's summary |
| Hand notes | Weaker | Treat every line as paraphrase unless it is marked as a quote |

Ask three things: how many interviews, who the participants are (role and segment), and what the study set out to learn.

**Privacy.** Use participant codes (P1, P2) in every output. Keep names, companies and anything identifying out unless the user asks for them. Work from the notes or transcription tool the team already uses, and do not paste transcripts into any other outside service.

## The Process

### 1. Restate the research questions

Two to four questions the study was meant to answer. If nobody wrote them down, derive them from the interview guide and confirm with the user. Sales, support and stakeholder calls have no guide: ask the user what they want to learn from them, and record under the limits that the calls were not held to answer it. Themes are judged against these questions.

### 2. One debrief sheet per interview

Read each transcript in full, one at a time. A summary of a transcript drops the details that matter. For each interview, fill the sheet in the template below. Keep two kinds of statement apart:

- **What they do**: described past behavior. "Last week I exported it to a spreadsheet and fixed it there."
- **What they say they want**: opinions, wishes, predictions. "I'd probably use a dashboard."

Also mark whether the participant raised a topic alone or was asked about it.

### 3. Build themes from the sheets

Group observations that describe the same thing across participants. Name each theme as a statement, not a topic: "Schedulers rebuild the plan in a spreadsheet every Monday", not "Spreadsheets".

Build from the observations up. Do not start from the directions the team already favors and look for support.

### 4. Count and split

For each theme: how many participants, out of how many, and which segments. "6 of 9, all four schedulers." No percentages.

### 5. Weigh the evidence

Stronger to weaker:
1. Past behavior, described with specifics
2. A workaround the participant built
3. A problem raised without being asked
4. An opinion given when asked
5. A feature request, or a prediction about their own future behavior

Mark each theme:
- **Strong**: rests on levels 1 to 3, from three or more participants or from most of one segment.
- **Weak**: rests only on levels 4 and 5, or comes from fewer than three participants. Give the reason next to the mark.

### 6. Keep contradictions and outliers

For each theme, list who said the opposite, with a quote. One outlier can be a segment nobody recruited enough of. Say so.

### 7. Turn themes into implications

For each strong theme: the insight (why it matters) and the implication for the design. Each implication cites its theme. An idea with no theme behind it is yours, not the research's. Put it under "Our ideas".

### 8. State the limits

Who was interviewed and who was not, how they were recruited, leading questions in the guide if there was one, and what the study cannot say.

## Output Templates

**Debrief sheet (one per interview)**

```
## P[n] - [role, segment] - [date] - [minutes]

**Context:** [their situation in two lines]

### What they do (past behavior)
- [observation] - "[exact quote]" ([timestamp or line])

### Workarounds
- ...

### What they say they want (opinion)
- ... (raised alone / asked)

### Surprises
- ...
```

**Synthesis**

```
## Interview synthesis - [study] - [date]

**Research questions:** ...
**Interviews:** [N], [who]. Source: [transcripts / notes]
**Not covered:** [segments, limits]

### Themes
| # | Theme (a statement) | Who | Strength | In their words |
|---|---|---|---|---|
| 1 | ... | 6 of 9 (P1, P2, ...) | strong / weak | "..." (P3) |

### Contradictions
- Theme [#]: P[n] said the opposite - "..."

### What it means for the design
1. Because theme [#], ...

### Our ideas (not from the research)
- ...

### Still unknown
- ...
```

Quotes may be shortened with [...]. They may not be reworded.

## Common Pitfalls

- **Quote hunting.** Picking the lines that support a direction already chosen.
- **Counting mentions.** The most talkative participant becomes the majority.
- **Requests read as needs.** "I want an export button" is a clue about a problem, not the problem.
- **Summarizing summaries.** Each layer drops who said what.
- **Tidied quotes.** A cleaned-up quote is a paraphrase.
- **Merging segments.** A theme true for admins and false for field users is two findings.
- **Percentages from nine people.**

## Pairs With

- `usability-testing` - for what people can do with the design, where interviews cover what they need.
- `reading-analytics` - to learn how common a described behavior is.
- `researching` - public user voice complements interviews with the team's own users.
- `brainstorming` - themes feed the problem framing.
- `presenting` - the synthesis is the source for the research readout meeting type.
- `meeting-pack` - stakeholder interviews produce the history a later pack draws on.

## Iteration Notes (v0.1)

Written from method, not from session evidence: this work was rare in past sessions. Watch for:
- Whether debrief sheets get written per interview or skipped under time pressure
- Whether the five-level evidence scale is used or ignored
- How transcripts arrive, and whether timestamps survive
