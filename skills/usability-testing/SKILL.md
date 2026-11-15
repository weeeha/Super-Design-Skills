---
name: usability-testing
description: Use when the user wants to test a design or product with real people - "usability test", "user test this", "test the prototype", "write a test script", "tasks for testers", "what did the test sessions show", notes or recordings from test sessions to analyze - or when a design decision is being argued from opinion and something testable already exists
---

# Usability Testing

## Overview

A usability test answers one thing: can people do what the design is for, and where do they fail. It does not answer whether they like it.

Three rules carry the skill:
1. **Tasks are situations, not instructions.** "You need last month's invoices for your accountant" tests the design. "Click Export" tests whether someone can follow an order.
2. **Watch what people do.** What they say they would do is weaker evidence than what they just did.
3. **Count participants.** "3 of 5 did not find Export", never "60%".

## When to Use

- Before committing engineering time to a new flow
- When two people disagree about whether something is clear
- After a prototype exists (`prototyping`) or on the live product
- When session notes or recordings exist and nobody has analyzed them

**Don't use** for:
- What users need or how they work today (`analyzing-interviews`)
- How many users hit a problem (`reading-analytics`)
- An expert review with no participants (`critiquing`, `design-qa`). Run one of those first: do not spend participants on problems you can see yourself.

## Three Entry Points

Ask which one the user is at, then start there:

| Stage | The user has | This skill produces |
|---|---|---|
| **Plan** | Something testable, no sessions yet | Test plan and script |
| **Run** | Sessions scheduled | Moderator rules and a note grid |
| **Analyze** | Notes, recordings or transcripts | Issue list with severity, and a one-page report |

## Plan

1. **The question and the decision.** What do we need to learn, and what will we change depending on the answer? If nothing would change, the test is not needed.
2. **What is being tested, and what is fake.** For a prototype, read its README: anything listed as faked cannot be part of a task.
3. **Participants.** Define them by role and situation ("schedules crews weekly"), not demographics. Five per distinct user group: enough to surface the common problems in that group, not the rare ones. Write 3 to 5 screener questions about past behavior, none of which reveal the wanted answer. Recruiting is the user's job; say so.
4. **Tasks.** Three to six. Each has four parts:

   | Part | Rule |
   |---|---|
   | Scenario | A situation and a goal. No words that appear on the screen |
   | Starting point | The exact screen or URL |
   | Success | Something observable: "the invoice PDF is downloaded" |
   | Limit | The time after which you move on |

   Order them from easy to hard. The first task should be one most people complete.
5. **Format.** Moderated with think-aloud is the default: 30 to 45 minutes, recorded with consent. Unmoderated only when tasks are simple and the prototype cannot dead-end.
6. **Script.** Intro (we are testing the design, not you; think aloud; I will not be able to help), one warm-up question about their work, the tasks, after each task "what did you expect to happen?", a closing question, thanks.
7. **Pilot.** Run it once with a colleague. Fix every task they misread.

## Run

Rules for whoever moderates:
- Read each scenario word for word
- Do not help, explain or defend. When someone is stuck, count to ten, then ask "what are you looking for?"
- Neutral prompts only: "what are you thinking?", "what would you do next?". These are not help
- Anything that points at the answer is help. If it happens, mark the task "helped"
- When the limit is reached, say "let's move on" and mark the task not done

One row per task, per participant:

```
| Task | P# | Result (done / with difficulty / helped / not done) | Time | Wrong turns | Their words | What I saw |
```

Fill "Their words" word for word. "What I saw" is behavior only: where they looked, clicked, hesitated.

Time, wrong turns and "What I saw" need a recording or a live observer. From a transcript or hand notes they are often missing: leave them blank and say so in the report. Do not estimate them.

## Analyze

1. **Fill the grid** from the notes or transcripts, one session at a time. Read the transcript, not a summary of it.
2. **Write issues.** One issue is one thing that went wrong in one place. For each: what happened, on which screen, which participants (P1, P3, P4).
3. **Rate severity.**

   | Severity | Meaning |
   |---|---|
   | **Blocker** | The participant could not complete the task, or completed it only with help |
   | **Major** | Completed alone, but it cost them: an error message, backtracking more than one step, about a minute or more lost, or visible frustration |
   | **Minor** | A hesitation or a single wrong click, recovered within seconds |

   Between two levels, choose by what it cost the participant and note the reason. Order the list by severity, then by number of participants.
4. **Keep three things apart** for every issue: the observation (what happened), the likely cause (your inference, labeled), and the fix options. A report that merges them cannot be checked.
5. **Record what worked.** Tasks everyone completed are findings too. They say what not to change.

## What the Numbers Can and Cannot Say

- Five participants find the common problems of one user group. Rare problems, and the problems of groups not recruited, stay hidden.
- A test does not measure how common a problem is. Use `reading-analytics` for that.
- No percentages. Write "3 of 5".
- "I would use this" and "I like it" are not findings. Leave them out or mark them as opinion.
- Say who was not tested: the user groups, devices and languages that were left out.

## Output Templates

**Test plan**

```
## Usability test - [what] - [date range]

**Question:** ...
**Decision it informs:** ...
**Testing:** [prototype or product, link]. Faked: [...]
**Participants:** [N] x [role and situation]. Screener: [questions]
**Format:** [moderated / unmoderated], [minutes], recorded: [yes / no]

### Tasks
| # | Scenario (read aloud) | Start | Success | Limit |
|---|---|---|---|---|

### Script
[intro, warm-up, tasks with follow-up question, close]
```

**Report (one page)**

```
## Usability test results - [what] - [date]

**Tested:** [N participants, who]. Not tested: [...]
**Bottom line:** [one sentence]

### Task results
| Task | Done | With difficulty | Helped | Not done |
|---|---|---|---|---|

### Issues, most severe first
| # | Severity | What happened | Where | Who | Likely cause (inference) | Fix options |
|---|---|---|---|---|---|---|

### What worked - keep
- ...

### Fix first
1. ...

### Still unknown
- ...
```

## Common Pitfalls

- **Task wording that gives the answer.** If the scenario uses the label on the button, the task is void.
- **Helping.** One hint and the task is "helped", not done. Record it that way.
- **Testing the faked part.** The participant fails because the prototype ends, not because the design does.
- **Opinions reported as findings.** "Users loved it" is not a result.
- **Percentages from five people.**
- **Fixing before ranking.** Twenty issues with no order means the minor ones get fixed because they are easy.

## Pairs With

- `prototyping` - builds what gets tested. Its README says what is faked.
- `critiquing` and `design-qa` - run before the test, to remove what an expert can already see.
- `analyzing-interviews` - for interviews with no tasks: what people need, rather than what they can do. Everything from a test session, including the talk after each task, stays in this skill.
- `reading-analytics` - to learn how many users hit an issue the test found.
- `exploring-options` - when testing two directions, alternate which one each participant sees first.
- `presenting` - the report feeds the research readout meeting type.

## Iteration Notes (v0.1)

Written from method, not from session evidence: this work was rare in past sessions. Watch for:
- Whether the three entry points match how tests actually arrive
- Whether the severity scale needs a fourth level
- How notes arrive in practice (transcripts, recordings, hand notes) and what the grid loses from each
