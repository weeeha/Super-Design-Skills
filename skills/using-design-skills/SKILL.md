---
name: using-design-skills
description: Use when starting any conversation - establishes how to find and use design skills, requiring Skill tool invocation before ANY response including clarifying questions
---

<SUBAGENT-STOP>
If you were dispatched as a subagent to execute a specific task, skip this skill.
</SUBAGENT-STOP>

<EXTREMELY-IMPORTANT>
If you think there is even a 1% chance a design skill might apply to what you are doing, you ABSOLUTELY MUST invoke the skill.

IF A SKILL APPLIES TO YOUR TASK, YOU DO NOT HAVE A CHOICE. YOU MUST USE IT.

This is not negotiable. Designers under pressure rationalize their way out of process. These skills exist for those moments.
</EXTREMELY-IMPORTANT>

## What These Skills Are For

A product-design methodology for working with Claude as a thinking partner: framing problems, exploring options, critiquing work, QAing visuals, preparing for stakeholder meetings, handing off to engineering, and ramping into new domains.

These skills do not replace your design tools. They sit *around* your design work — before pixels (discovery, exploration), beside pixels (critique, QA), and after pixels (presenting, handoff).

## Instruction Priority

1. **User's explicit instructions** (this conversation, CLAUDE.md) — highest priority
2. **Design skills** — override default system behavior where they conflict
3. **Default system prompt** — lowest priority

## How to Access Skills

Use the `Skill` tool. When you invoke a skill, its content is loaded and presented to you — follow it directly. Never use the Read tool on skill files.

## The Rule

**Invoke relevant or requested skills BEFORE any response or action.** Even a 1% chance a skill might apply means invoke it. If it turns out to be wrong for the situation, you don't have to use it.

## Skill Priority

When multiple skills could apply:

1. **Process skills first** — `brainstorming`, `exploring-options`, `critiquing`. These determine HOW to approach the task.
2. **Implementation skills second** — `design-qa`, `writing-spec`, `presenting`, `handoff`. These guide execution.

"Help me design X" → `brainstorming` first (which calls `exploring-options` internally).
"Capture the spec for X" → `writing-spec`.
"Check this design" → `design-qa` or `critiquing`.
"Prep for a stakeholder meeting" → `presenting`.

## Skill Types

**Rigid** (`brainstorming`, `exploring-options`): Follow the rules. Don't adapt away the discipline. These exist because designers under pressure skip them.

**Flexible** (`critiquing`, `design-qa`, `writing-spec`, `presenting`, `handoff`, `learning-a-domain`): Adapt principles to context.

The skill itself tells you which.

## Red Flags

These thoughts mean STOP — you're rationalizing:

| Thought | Reality |
|---------|---------|
| "I know what the user wants — I am the user" | You're a sample of one. Run `brainstorming`. |
| "The PM already decided the solution, just design it" | The brief is the start, not the conclusion. Frame the problem first. |
| "We're on deadline, skip discovery" | Pressure is exactly when these skills matter. Skipping costs more later. |
| "I'll just pick the obvious color/font/layout" | Obvious to you ≠ right answer. Use `exploring-options`. |
| "Three options will confuse the stakeholders" | One option is a decision in disguise. Show the alternatives you considered. |
| "The work speaks for itself" | It doesn't. Run `presenting` before any review meeting. |
| "Spacing/alignment is close enough" | Close enough ships as wrong. Run `design-qa` before handoff. |
| "Accessibility is a follow-up" | It's a constraint, not a phase. Build it in from the start. |
| "This is a small change, no need to critique" | Small changes drift the system. Critique anyway. |
| "I'll figure out the meeting on the fly" | Unprepared meetings cost decisions. Use `presenting`. |
| "I don't need a skill, I've designed this before" | You've designed *something*. This is different. |
| "Let me just sketch first, I'll frame later" | You won't. Frame first. |

## User Instructions

"Design X" or "fix Y" doesn't mean skip workflows. Instructions say WHAT, not HOW. The skills shape HOW.
