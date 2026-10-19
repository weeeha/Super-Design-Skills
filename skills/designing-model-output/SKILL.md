---
name: designing-model-output
description: Use when designing, reviewing or building any surface that renders model output - chat and assistant turns, streamed answers, reasoning or thinking traces, plans, tool calls, citations and sources, agent runs, AI playgrounds, or the design-system components that render them. Also use when a mock shows one perfect AI answer and nothing else
---

# Designing Model Output

## Overview

Model output is content you never see in advance. It streams, it arrives in a shape the model chose, and it can stop halfway. Design the renderer for every shape the protocol can send. The tidy transcript in the mock is one shape of many.

## When to Use

- Designing or reviewing a chat, assistant, copilot, agent or playground surface
- Adding reasoning, plans, tool calls, citations or file outputs to an existing surface
- Building or auditing the components a design system uses to render model output
- A mock or prototype shows a single happy answer

**Not for:** what the model says or how it behaves, such as writing a prompt so it cites more reliably, or running evals. Not for a general visual pass either: run `design-qa` for spacing, type and contrast once this skill's passes are done.

## Inputs

1. **The protocol.** The list of events or message parts the stream can carry: text, reasoning, tool input and output, sources, errors, finish reasons. Take it from the API or SDK docs. If nobody on the team can name it, that is the first finding.
2. **The surface.** A running build, or a Figma link or screenshots. Ask which if it's unclear.
3. **Real transcripts,** if they exist: at least one long answer, one with a tool call, one that failed.

### Running build vs. static screens

A running build is best: most of these failures only show up in real paint. With only Figma or screenshots, review what the frames show and mark these checks **unverified** instead of guessing:

- Pass 2: whether the shipped CSS keeps list markers (a frame shows the intent, not the reset)
- Pass 4: layout jump and scroll behaviour while streaming
- Pass 8: live regions, focus movement, keyboard reach

Each unverified check becomes a line in Acceptance Criteria below.

## The Passes

Run in order. Report findings grouped by severity, using the `design-qa` levels (Blocker, High, Medium, Low). Severity for this skill:

| Severity | Here it means | Examples |
|---|---|---|
| **Blocker** | The reader gets a wrong or invisible answer | Error events swallowed, truncated answer shown as complete, a list rendered as plain lines, a tool state that lies |
| **High** | The answer is right but hard to trust or read | Reasoning louder than the answer, citations not tied to claims, no stop control, a missing fixture from the list below |
| **Medium** | Polish that affects some readers | Unlabeled copy button, hover-only cited spans, table squashed on mobile |
| **Low** | Nitpicks | Inconsistent "Thought for Ns" wording |

### 1. Map every event to a component

Write a table: event or part, the component that renders it, the states that component has. An event with no row renders as raw text or as nothing.

**Common misses:**
- A tool plan rendered in the answer's style, so the reader can't tell working notes from the reply
- Error events swallowed, so the turn just stops
- A `length` finish reason (the answer was cut off) shown exactly like a complete answer

### 2. Markdown survives the CSS reset

Models write Markdown: bullets, numbered steps, nested lists, tables, code, quotes, headings, links. CSS resets such as Tailwind's preflight remove list markers and padding, and a prose layer has to put them back.

Check in the rendered surface:
- Bullets and numbers are visible, and nested lists indent
- Tables scroll sideways on narrow screens instead of squashing columns
- Code blocks scroll and never wrap mid-token
- Links look like links

**Common misses:**
- A list rendered as plain lines because the reset set `list-style: none` and nothing restored it. This shipped in a production AI playground in 2026.
- Prose styles fixed screen by screen instead of once, in the shared renderer

### 3. The answer outranks the work

Reasoning traces, plans and tool calls are evidence. The answer is what the reader came for. Evidence sits quieter: smaller or secondary text, collapsed once the answer arrives, one click to reopen.

**Common misses:**
- A reasoning trace set larger or darker than the answer under it
- Every tool call open by default, so the answer sits below two blocks of JSON

### 4. Streaming has states

Design each of these:
- Waiting for the first token
- Streaming, including half-written Markdown (an unclosed code fence, half a table)
- Done
- Stopped by the reader
- Cut off by length
- Failed mid-stream

Layout must not jump as text arrives. Auto-scroll follows only while the reader is already at the bottom.

**Common misses:**
- No stop control while streaming
- A truncated answer that looks complete
- A half-rendered table that flickers between layouts

### 5. Tool calls tell the truth

Each call shows its name, its arguments, its result, and a lifecycle state that matches what actually happened: pending, running, waiting on a person, completed, error, denied. The state word carries the meaning for screen readers; colour alone does not.

- A failure renders as a sentence the reader can act on, with the raw payload behind a disclosure
- A call waiting on the reader asks inline, in the turn. A modal closes and leaves no record that the question was asked
- Both buttons name their outcome. "Confirm" and "Cancel" mean nothing when read alone

**Common misses:**
- A spinner that never resolves when the call errors
- Asking permission for an act that undoes itself (do it, then report it)
- A state string invented by the UI that the protocol never sends

### 6. Citations point somewhere

A claim that came from a source links to that source: at the span when the API gives offsets, otherwise at the sentence. Opening a source lands on the cited passage. A "used N sources" summary closes the turn.

**Common misses:**
- Citation chips with no accessible name
- Sources listed at the end but never tied to the claims they support
- Cited-span highlighting that only works on hover, so it vanishes on touch screens

### 7. Honesty states

Output fails in ways the UI has to name:
- No answer (a refusal, or an empty response)
- No sources found, so the answer comes from the model's memory
- A tool failed and the model answered anyway
- Truncated
- Built on stale data

The model saying it succeeded is not a success state. Show what actually ran.

**Common misses:**
- An answer with zero sources styled exactly like a grounded one
- "Thought for 2s" shown when no reasoning happened

### 8. Access and control

- The transcript is one live region (`role="log"`). Do not add a second one per message
- Focus moves somewhere predictable when the model asks for input
- Icon-only actions (copy, retry, rate, regenerate) have accessible names
- Keyboard reaches every citation and disclosure
- With reduced motion, shimmer and spinners stop looping and the state text stays

## Fixtures to Design With

A mock passes this skill only when it shows all of these. Each one missing is a **High** finding:

- A long answer using every Markdown element above
- A tool call that errors, and one waiting on the reader
- A refusal, and an answer with zero sources
- An answer stopped halfway, and one cut off by length
- A citation whose source title is three times the expected length

## Acceptance Criteria

Write the behaviours worth locking in as acceptance criteria. They go into the review, and into `handoff` if one follows. One line each: the behaviour, how to check it, and where the check must run.

- **Prose styles are checked in a real browser.** jsdom applies no stylesheet, so a style assertion there passes while proving nothing.
- **Every style check names the change that makes it fail, and that change was tried once.** A style test can pass because an unrelated class happens to be generated in the dev build, so delete the rule on purpose and confirm the check goes red before trusting it.
- **One fixture per state in pass 4 and pass 5,** rendered in every theme the product ships.
- **Every check marked unverified** in a static review.

## Output Template

```
## Model output review: [surface]

**Protocol source:** [doc or SDK + version, or "unknown" as the first finding]
**Reviewed in:** [running build / Figma / screenshots]

### Event to component map
| Event or part | Component | States designed | Gap |
|---|---|---|---|
| ... | ... | ... | ... |

### Findings
#### Blockers
1. [issue] - [where] - [which pass] - [why it blocks]
#### High
1. ...
#### Medium
1. ...
#### Low
1. ...

### Fixtures still missing
- ...

### Unverified (static review only)
- [check] - [pass] - [what would verify it]

### Acceptance criteria
- [behaviour] - [how to check] - [runs in: real browser / unit / manual] - [change that should make it fail]

### Looks good
- [specific things that pass]
```

## Common Pitfalls

- **Designing from one transcript.** The happy answer is the least informative fixture.
- **Showing reasoning off.** Reasoning is evidence. Tuck it away once the answer lands.
- **Fixing per screen.** Stripped lists, unlabeled chips and raw errors are renderer bugs. Fix them once, in the shared component.
- **Trusting a green style test.** See Acceptance Criteria: make it fail once first.

## Pairs With

- `design-qa`: the visual pass on the same screens, after this one
- `critiquing`: whether the surface should show the work at all
- `handoff`: the event-to-component map goes into the handoff
- `verifying-before-shipping`: run the fixtures before calling it done
- `learning-a-domain`: when the model's protocol itself is new to you

<!-- Testing (v0.1 light approach, 2026-10-19): read cold by a fresh agent (fixed: static-review fallback, severity table, acceptance criteria aimed at the designer, prompt-writing excluded); trigger test pending a plugin update. Drawn from a teardown of a production AI playground (stripped list markers, reasoning louder than the answer, unlabeled icon buttons) and from the Minimal Design System's Tool and Confirmation usage contracts. -->
