# Super Design Skills

**Problem.** Figma, prototyping tools and Anthropic's `design:*` skills cover the what of design work, and little in Claude Code holds a designer to the how: framing, comparing directions, critique, QA and handoff.

**Idea.** A methodology layer of skills built on one rigid rule: never present one direction, always present three. A SessionStart hook injects a meta-skill so Claude picks up the right skill without being asked.

**Built.** A Claude Code plugin (v0.6.0) with 22 skills (20 methodology, 2 meta), installable from a plugin marketplace and licensed MIT. 19 commits on 6 days, May 16 to Oct 20, 2026.

**Decision.** The skills shape process and leave visual quality to Anthropic's `design:*` skills, the Figma MCP, shadcn and your own design system, instead of trying to make Claude a better visual designer.

A product-design methodology for Claude Code. Skills that help product designers frame problems, explore options, critique work, QA visuals, prep for stakeholder meetings, hand off to engineering, and ramp into new domains.

**This is not a replacement for existing design skills.** It's a methodology layer that wraps around the design work. Where Anthropic's `design:*` skills, `figma-*` skills, and your tools (Figma, prototyping, etc.) handle the *what*, these skills handle the *how* — the discipline around the work.

**Status: v0.6.0.** 22 skills (20 methodology skills plus 2 meta skills). Iterate from real usage.

## Inspiration

Architecture borrowed (with credit and admiration) from [obra/superpowers](https://github.com/obra/superpowers) — same bootstrap-and-meta-skill trick, adapted from software-engineering methodology to product-design methodology.

Where superpowers enforces test-driven development, this plugin enforces **option-driven design**: never present one direction, always present three. That's the rigid disciplinary spine.

## Installation

Register the marketplace, then install:

```bash
/plugin marketplace add weeeha/Super-Design-Skills
/plugin install SuperDesign@SuperDesign-marketplace
```

Restart your session. The plugin's `SessionStart` hook injects the [`using-design-skills`](skills/using-design-skills/SKILL.md) meta-skill at the start of every session, which teaches Claude to invoke the other skills automatically when they're relevant.

Verify it loaded — ask Claude:

> "What design skills do you have available?"

You should see all 22 skills listed under the `SuperDesign:` namespace.

## Skills

### Workflow (the methodology spine)

| Skill | What it does |
|---|---|
| [`brainstorming`](skills/brainstorming/SKILL.md) | Dialogue-first front-end of any project — frames problem, refines through questions, aligns on direction (**rigid**) |
| [`exploring-options`](skills/exploring-options/SKILL.md) | Forces 3+ distinct directions, blocks single-option proposals (**rigid**) |
| [`sketching`](skills/sketching/SKILL.md) | Low-fidelity layouts, flows, concept maps and storyboards before anything polished. Three sketches that differ in structure, in chat, FigJam or Figma |
| [`writing-spec`](skills/writing-spec/SKILL.md) | Captures approved direction as a light PRD / design spec (1-2 pages) |
| [`critiquing`](skills/critiquing/SKILL.md) | Conceptual review — fit, hierarchy, intent, narrative, edge cases |
| [`design-qa`](skills/design-qa/SKILL.md) | Visual QA — alignment, spacing, type, contrast, states, tokens. Figma or screenshot |
| [`meeting-pack`](skills/meeting-pack/SKILL.md) | One-page prep for any meeting - what was decided last time (with sources), what changed, decisions needed, likely questions |
| [`presenting`](skills/presenting/SKILL.md) | Stakeholder narrative — script + decision ask for six meeting archetypes, plus a slide list when the meeting needs a deck |
| [`handoff`](skills/handoff/SKILL.md) | Engineering handoff — states, edge cases, motion, copy, redlines, acceptance criteria |
| [`verifying-before-shipping`](skills/verifying-before-shipping/SKILL.md) | Verification pass before declaring "done" — process, design, system, stakeholder, honesty checks (**rigid**) |
| [`prototyping`](skills/prototyping/SKILL.md) | Clickable code prototype from Figma, screenshots, a sketch, an idea or an existing app — Vite + React + Tailwind + shadcn. For user testing, demos, de-risking |
| [`figma-1to1`](skills/figma-1to1/SKILL.md) | Pixel-perfect production-grade implementation from Figma. TDD-for-design: extract tokens, build atom-up, visually verify each step (**rigid**) |
| [`writing-case-study`](skills/writing-case-study/SKILL.md) | Turn shipped work into portfolio piece + resume bullet + LinkedIn post + interview pitch. Q&A-driven, pulls from spec/options/presenting artifacts |
| [`subagent-driven-design-execution`](skills/subagent-driven-design-execution/SKILL.md) | Parallel development of 3+ options via subagents — experimental, v0.1 |
| [`designing-model-output`](skills/designing-model-output/SKILL.md) | Surfaces that render model output - streaming, Markdown, reasoning, tool calls, citations, honesty states. Event-to-component map plus eight passes |

### Learning

| Skill | What it does |
|---|---|
| [`learning-a-domain`](skills/learning-a-domain/SKILL.md) | Designer's-eye summary of an unfamiliar vertical — diagram + brief + skill-pointer |

### Research

| Skill | What it does |
|---|---|
| [`researching`](skills/researching/SKILL.md) | Desk research: pattern research, product teardowns, user voice and references - dated evidence, then three implications for the design |
| [`usability-testing`](skills/usability-testing/SKILL.md) | Plan, run and analyze tests with real people - situational tasks, a note grid, issues ranked by severity and participants |
| [`reading-analytics`](skills/reading-analytics/SKILL.md) | Usage numbers for one flow, read from a design question - funnel, biggest loss, hypotheses with the cheapest check |
| [`analyzing-interviews`](skills/analyzing-interviews/SKILL.md) | Transcripts into checkable themes - exact quotes, counts by participant, contradictions kept, implications for the design |

### Meta

| Skill | What it does |
|---|---|
| [`using-design-skills`](skills/using-design-skills/SKILL.md) | The bootstrap. Auto-injected at session start. |
| [`writing-design-skills`](skills/writing-design-skills/SKILL.md) | How to add or edit skills in this plugin |

## How It Works

1. Claude Code starts a session.
2. The `SessionStart` hook ([`hooks/session-start`](hooks/session-start)) reads [`using-design-skills/SKILL.md`](skills/using-design-skills/SKILL.md) and injects it as session context.
3. That meta-skill teaches Claude: *if there's a 1% chance a design skill applies, invoke it.*
4. As you work, Claude invokes the relevant skill (`brainstorming` when starting, `exploring-options` before committing, `design-qa` before handoff, etc.).
5. Each skill produces a structured output you can act on — a framed direction, three options, a written spec, a critique, a QA report, a presentation script, a handoff doc, a domain brief.

## The Workflow

```
brainstorming  ──invokes──→  exploring-options (3+ directions)
    ↓                              ↓
    ↓              (optional)  subagent-driven-design-execution
    ↓                              ↓
sketching (low-fi layouts and flows, three of each)
    ↓
writing-spec (light PRD)   [optional, recommended for anything cross-functional]
    ↓
[design in Figma / your tools]
    ↓
critiquing  ←→  design-qa
    ↓
        (optional, any time)
        prototyping (throwaway clickable code)
        figma-1to1 (pixel-perfect production code with verification loop)
    ↓
verifying-before-shipping
    ↓
meeting-pack (before any meeting)  ──then──→  presenting (to stakeholders)
    ↓
handoff (to engineering)
    ↓
[ship]
    ↓
writing-case-study (portfolio piece + resume bullet + LinkedIn post + interview pitch)
```

`prototyping` and `figma-1to1` both turn Figma into code, but at different fidelity bars:
- `prototyping` — clickable, throwaway, "feels right is fine", ~30 min
- `figma-1to1` — production-grade, pixel-perfect, visual verification at each step, slower but matches Figma exactly

Pick `prototyping` when you need a clickable artifact for testing/demos. Pick `figma-1to1` when the code is the implementation that ships (or is the visual baseline for ship).

`learning-a-domain` is sideways — invoke it whenever you hit an unfamiliar vertical, at any point in the flow.

`researching` is sideways too: it looks at specific products, patterns and user feedback, usually before `brainstorming` or `exploring-options`. `meeting-pack` applies to every meeting, including ones where no design work is shown.

The research skills split by the kind of evidence: `usability-testing` for what people can do with the design, `reading-analytics` for how many do it, `analyzing-interviews` for what they say about their work. Each points to the others for the question it cannot answer.

## What This Doesn't Try To Do

- **Make Claude a better visual designer.** Skills shape *process*, not aesthetic outcome. For visual work, lean on Anthropic's `design:*` skills, the Figma MCP, shadcn, and your design system.
- **Replace your design tools.** Figma, FigJam, Loom, Notion, Linear — these all stay. The plugin sits beside them.
- **Cover non-product-design work.** Brand, marketing, illustration, motion graphics - out of scope for now.
- **Support multiple harnesses.** Claude Code only for now. Cursor / Codex / Gemini support is future work if the methodology proves out.

## Versioning

```bash
./scripts/bump-version.sh --check     # see current versions across all manifests
./scripts/bump-version.sh --audit     # also scan repo for stale version strings
./scripts/bump-version.sh 0.2.0       # bump everything to 0.2.0
```

The version is mirrored across `package.json`, `.claude-plugin/plugin.json`, and `.claude-plugin/marketplace.json`. The script keeps them in sync.

## Companion: SuperLead

If you're a design manager (or designer who also manages), check out [SuperLead](https://github.com/weeeha/Super-Design-Lead) — the same architecture applied to design leadership instead of design work. 1:1 prep, career conversations, feedback delivery, hiring loops, coaching.

```bash
/plugin marketplace add weeeha/Super-Design-Lead
/plugin install SuperLead@SuperLead-marketplace
```

The two plugins share the disciplinary spine — *never present one option, always present three.* SuperDesign uses it for design directions; SuperLead uses it for career paths. Same psychology, same trap, same fix.

When both are installed, skills cross-reference each other — e.g., `SuperLead:giving-feedback-to-a-report` (manager-side of feedback delivery) pairs with `SuperDesign:critiquing` (the work itself).

## Roadmap (open questions, not promises)

- Real-usage iteration on the novel skills (`design-qa`, `presenting`, `learning-a-domain`, `subagent-driven-design-execution`, and the v0.6.0 additions `meeting-pack`, `sketching`, `researching`, `usability-testing`, `reading-analytics`, `analyzing-interviews`)
- Trigger tests for the v0.6.0 skills in a fresh session, and real use of the slides step in `presenting`
- A `design-qa` mode that does a side-by-side diff against the prior version of a design
- A visual companion for `brainstorming` (the upstream-style local browser for mockups during dialogue)
- An eval corpus for skill triggering — does `exploring-options` actually fire under deadline pressure?
- A Cursor port (the hook architecture supports it; haven't wired the manifest yet)

## License

MIT.

## Credit

Architecture inspired by [obra/superpowers](https://github.com/obra/superpowers) by Jesse Vincent. The bootstrap hook, the meta-skill pattern, the "if 1% chance, invoke it" rule, the Red Flags table — all originate there. This plugin is a design-methodology dialect of the same idea.
