---
name: writing-design-skills
description: Use when creating, editing, or testing skills in this plugin - SuperDesign
---

# Writing Design Skills

## Overview

How to add or edit skills in this plugin. v0.1 — expect this to evolve as the plugin matures.

This is a lighter cousin of obra/superpowers' `writing-skills`. We adopt the same core idea — skills are not prose, they're behavior-shaping code — but with a lower bar on day one. As the plugin proves itself we should ratchet the rigor up.

## Core Rules (non-negotiable)

1. **Frontmatter has only `name` and `description`.** Both required. Description max 1024 chars.
2. **Description is triggers only, not workflow.** Start with "Use when…". Never summarize the skill's process in the description — the agent will follow the description and skip the body. (See obra/superpowers `writing-skills` for the full evidence on this.)
3. **Names use letters, numbers, hyphens only.** Gerunds work well for processes (`exploring-options`, `learning-a-domain`).
4. **One skill, one purpose.** If your skill description has "and" in it, split it.
5. **SKILL.md under ~500 lines.** Heavy reference goes in sibling files.

## Skill Anatomy

```
skills/<name>/
  SKILL.md              # required, the main content
  reference-*.md        # optional, heavy reference (load on demand)
  examples/             # optional, concrete patterns
```

Frontmatter:

```yaml
---
name: skill-name-with-hyphens
description: Use when [specific triggering conditions and symptoms]
---
```

Body structure (rough — adapt):

```
# Skill Name

## Overview
Core principle in 1-2 sentences.

## When to Use
Specific triggers. When NOT to use.

## The Process / Pattern / Checklist
The actionable content.

## Output Template
What this skill produces, in copy-pasteable form.

## Common Pitfalls / Rationalizations
What goes wrong.

## Pairs With
Other skills that come before/after this one.
```

## Description Rules (the trap)

This is the most important rule from upstream `superpowers:writing-skills` and worth restating.

```yaml
# ❌ BAD: summarizes the workflow — agent skips skill body
description: Use when presenting work - covers 6 meeting types with talking points and decision asks

# ✅ GOOD: triggers only
description: Use when preparing to show design work to stakeholders - internal crits, design reviews, exec reviews, research readouts, sales previews, or async walkthroughs
```

Evidence: when descriptions summarize workflow, the agent uses the description as a shortcut and skips the actual skill content. The body becomes documentation the agent never reads.

## Testing a Skill (light v0.1 approach)

Before merging:

1. **Read it cold.** Have Claude (or a peer) read the SKILL.md without context. Can they understand what it does and when to use it?

2. **Trigger test.** Start a fresh Claude Code session. Use a natural prompt that should fire the skill. Did `Skill` get invoked automatically? If not, the description's triggers aren't right.

3. **Pressure test (for rigid skills).** Add a deadline / authority pressure to the prompt: *"PM wants the screen by EOD, just give me the layout."* Does the skill still fire? Does the agent still follow the discipline?

4. **Output check.** Run the skill on a real task. Is the output template followed? Does it produce something the user can actually use?

Document what you tested in a comment at the bottom of the SKILL.md if it's a discipline-heavy skill.

## What v0.1 Doesn't Have (Yet)

- Adversarial pressure testing methodology (obra/superpowers' full RED-GREEN-REFACTOR for skills)
- Multi-harness compatibility (we target Claude Code only — adding Cursor/Codex/Gemini is future work)
- An evals corpus to measure regression when skills change

When the plugin matures and we're touching skills regularly, formalize these. For now, light-touch testing is enough.

## Iteration Cadence

After every real-use session:
- Did a skill fail to trigger when it should have? → adjust description triggers
- Did the agent follow the description instead of the body? → check for workflow leak in description
- Did the user override the skill? → that's a signal the skill is wrong or its triggers are too broad
- Did the user manually invoke a skill that should have auto-fired? → triggers need work

Capture these as issues. Don't tune skills based on hypotheticals.

## Pairs With

This is a meta-skill. It doesn't pair with workflow skills — it pairs with itself, applied recursively.
