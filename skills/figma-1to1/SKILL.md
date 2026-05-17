---
name: figma-1to1
description: Use when implementing a Figma design with pixel-perfect fidelity required - production-grade code that must visually match the design exactly, with verification at every step
---

# Figma 1:1 Implementation

## Overview

Implement a Figma design as production-grade code that matches the design **exactly** — same colors, spacing, radii, typography, icons, layout. Not "approximately". Not "looks similar". 1:1.

The reason existing Figma-to-code flows produce mismatches is that they do **one pass with no verification loop**. Implement, claim done, move on. Mismatches survive because nothing compared the output to the source.

This skill fixes that by enforcing TDD-for-design: extract tokens first, build atom-up, and *visually verify each step against the Figma source* before proceeding.

## When to Use

- The Figma design is the source of truth and the code must match it
- You're starting a new project from scratch (no existing component library that conflicts)
- The code will ship (or will become the visual baseline for ship)
- Pixel fidelity matters more than implementation speed
- You're vibe-coding the implementation yourself, or building for an engineering team to take over

**Don't use** for:
- Throwaway prototypes (`prototyping` is the right skill — faster, less strict)
- Retrofitting an existing codebase (different problem — `prototyping` patterns are closer)
- Designs that aren't finalized yet (you'll waste cycles verifying against a moving target)

## The Two Iron Laws

```
1. NO raw values in component code
2. NO component "done" without visual verification
```

### Law 1 — No raw values

Every color, spacing, radius, font size, shadow, line-height in component code MUST reference a token derived from Figma. No exceptions.

❌ `<div className="bg-[#3b82f6] p-[16px] rounded-[12px]">`
✅ `<div className="bg-primary p-4 rounded-lg">`

If a Figma value doesn't have a corresponding token yet, **stop and create the token**. Don't inline it "just for now."

### Law 2 — No visual verification skip

A component is not done when the code compiles. It's done when a screenshot of the implementation, compared to the Figma source, shows no meaningful mismatch.

❌ "I wrote the Button component, looks fine, moving on"
✅ "I wrote the Button. Screenshot vs Figma: bg slightly off (#2563eb vs #2978ed). Fixed. Re-verified. Now done."

**Violating the letter of these laws is violating the spirit.** Both laws exist because the alternative — informal implementation — produces the mismatches you came here to solve.

## The 5-Phase Process

```
Phase 1: Token Extraction       (the foundation)
    ↓
Phase 2: Component Inventory    (the plan)
    ↓
Phase 3: Atom-up Build          (verification loop)
    ↓
Phase 4: Screen Composition     (atoms → screens)
    ↓
Phase 5: Final Visual Diff      (the proof)
```

### Phase 1 — Token Extraction

**Before writing any UI component, extract every design token from Figma and set up the styling system.**

Steps:

1. **Get Figma variables.** Use `figma-remote:get_variable_defs` for the file. Pull all colors, spacing scales, radii, type styles, shadows.

2. **If Figma has no variables** (common — designer never tokenized):
   - Walk every layer via `figma-remote:get_metadata` and `get_design_context`
   - Extract every unique color used → cluster near-duplicates (#3b82f6 and #3b83f8 are probably the same intent)
   - Extract every unique spacing value → cluster to a scale (e.g., 4, 8, 12, 16, 24, 32, 48, 64)
   - Extract every unique radius
   - Extract every unique font size + weight + line height combo
   - Show the inferred token list to the user. **Get explicit approval before continuing.**

3. **Set up the styling system.** Default stack: Tailwind CSS v4 (CSS-only theme) + shadcn.
   - Write `src/styles/tokens.css` with all tokens as CSS custom properties under `:root`
   - If light/dark mode exists in Figma, mirror it: `[data-theme="dark"] { ... }`
   - In `globals.css`, use Tailwind v4's `@theme inline` to bind every CSS var to a Tailwind utility
   - This means: `bg-primary` → `var(--color-primary)`, `p-4` → `var(--spacing-4)`, etc.

4. **Configure shadcn** to use these tokens. Edit `components.json` and `components/ui/*` to reference your tokens, not shadcn's defaults.

5. **Lint enforcement** (optional but recommended): add an ESLint rule banning raw hex in TSX, or just enforce by discipline.

**Phase 1 output:**
- `src/styles/tokens.css` — every design token
- `src/styles/globals.css` — Tailwind theme inline binding
- An approved token sheet shown to the user
- shadcn installed and themed

Do NOT start building components until Phase 1 is signed off.

### Phase 2 — Component Inventory

**Before atom-up build, plan every component.**

For each unique Figma component:

| Figma component | Has shadcn primitive? | Customization needed | Status |
|---|---|---|---|
| Primary Button | Yes (`button`) | Match radius, padding, color | Pending |
| Search input | Yes (`input`) | Match icon position | Pending |
| Stats card | No — custom | Build from scratch | Pending |
| Pricing toggle | No — custom (built from `tabs`?) | Investigate | Pending |
| Icons | Lucide closest match | Manual mapping list | Pending |

For icons specifically — Lucide is the default, but Figma often uses custom icons or different libraries. List every Figma icon, find Lucide closest match, flag any that need manual SVG import.

**Phase 2 output:** the component inventory table, agreed with the user.

### Phase 3 — Atom-up Build (the verification loop)

**The heart of this skill.** Build smallest components first. For each:

```
implement → screenshot → compare → list mismatches → fix → re-verify → done
```

Detailed loop:

1. **Implement the component** using tokens only (Law 1). Place it on a dev-only route like `/dev/<component-name>` or in a `__components__.tsx` showcase file. The point: each component must be renderable in isolation.

2. **Start the dev server.** Use `Claude_Preview:preview_start` to launch on a known port.

3. **Take implementation screenshot.** Use `Claude_Preview:preview_screenshot` at the component's URL.

4. **Pull Figma reference screenshot.** Use `figma-remote:get_screenshot` for the exact frame, at matching dimensions.

5. **Visually compare** — Claude reads both images and produces a structured mismatch list:

```
## Mismatches — Button (primary, default state)

### Color
- Implementation: bg = oklch(0.5 0.2 250)
  Figma:          bg = oklch(0.52 0.21 248)
  Action: update --color-primary in tokens.css

### Spacing
- Implementation: padding = 12px horizontal, 8px vertical
  Figma:          padding = 16px horizontal, 10px vertical
  Action: button uses px-4 py-2.5 (assuming 4/2.5 maps to 16px/10px in your scale)

### Radius
- Match ✓

### Typography
- Implementation: font-weight 500
  Figma:          font-weight 600
  Action: update Button component class to font-semibold

### Icon (if any)
- Match ✓
```

6. **Fix every mismatch.** Don't skip "small" ones. A 2px padding mismatch compounds across the design.

7. **Re-verify.** Screenshot again, compare again. Loop until the diff is empty or only flagged as "acceptable drift" (e.g., subpixel anti-aliasing differences).

8. **Mark complete.** Move to next atom.

**Order: smallest atoms first.**
- Iconography → Buttons → Inputs → Badges → Tags → Avatars → small composite elements → Card-like → Forms → Modals/Sheets

Don't compose anything until its constituent atoms are verified.

### Phase 4 — Screen Composition

**Compose verified atoms into screens.** Verification continues at the screen level.

Steps for each screen:

1. **Build the screen** using only verified components and tokens.
2. **Screenshot the implementation** at production-target dimensions (typically 1440×900 for desktop screens, 375×812 for mobile).
3. **Pull the Figma frame screenshot** at matching dimensions.
4. **Visual diff at screen level:**
   - Layout — grid columns, gaps, alignment
   - Sectional padding / margin
   - Vertical rhythm between sections
   - Sticky / fixed positioning if any
   - Responsive behavior across breakpoints (if Figma has breakpoint variants)
5. **Fix mismatches**, re-verify.

**Don't proceed to the next screen** until current one matches.

### Phase 5 — Final Visual Diff

**End-to-end fidelity check before declaring complete.**

1. Screenshot every screen at every breakpoint Figma defines
2. Side-by-side with Figma frames
3. Produce a final diff report grouped by severity:

```
## Final Visual Diff — <Project> — YYYY-MM-DD

### Blockers (must fix before declaring done)
1. ...
2. ...

### High (visible deviation, should fix)
1. ...

### Medium (catchable polish, fix if time)
1. ...

### Low (subpixel / anti-aliasing, accept)
1. ...

### Looks good
- All buttons, inputs match
- Card spacing matches
- Color palette matches across light/dark
- Typography matches
```

4. User reviews and decides accept / fix blockers / iterate.

Phase 5 mirrors `design-qa` output format because it IS design-QA, applied to the implementation.

## Tools the Skill Uses

| Need | Tool |
|---|---|
| Read Figma variables | `figma-remote:get_variable_defs` |
| Read Figma component context | `figma-remote:get_design_context` |
| Reference screenshots | `figma-remote:get_screenshot` |
| Figma layer/metadata walk | `figma-remote:get_metadata` |
| Find shadcn primitives | `Shadcn_UI:get_component`, `get_component_demo` |
| Install shadcn components | `bunx shadcn@latest add <name>` |
| Start dev server | `Claude_Preview:preview_start` |
| Screenshot implementation | `Claude_Preview:preview_screenshot` |
| Visual comparison | Claude's vision capability (reads two images, produces diff) |
| Icon lookup | `lucide-react` (default), manual SVG import if missing |

## Stack Defaults

- **Framework:** Vite + React + TypeScript (or Next.js if user prefers)
- **Styling:** Tailwind CSS v4 (CSS-first theme)
- **Components:** shadcn/ui (latest), customized to your tokens
- **Icons:** lucide-react, manual SVG fallback
- **Package manager:** bun (fallback pnpm, fallback npm)

Configurable. If the user has different preferences, ask early in Phase 1.

## Output Structure

```
<project>/
├── README.md                          # 1:1 implementation notes
├── package.json
├── vite.config.ts (or next.config.ts)
├── tailwind.config.ts (or v4 inline)
├── components.json                    # shadcn config
├── src/
│   ├── styles/
│   │   ├── tokens.css                 # ALL Figma variables as CSS vars
│   │   └── globals.css                # Tailwind + theme bindings
│   ├── components/
│   │   ├── ui/                        # shadcn primitives (themed)
│   │   └── custom/                    # custom components built from tokens
│   ├── pages/ (or app/)               # screens
│   └── lib/utils.ts
├── dev/                               # dev-only routes for component isolation
│   └── components-showcase.tsx
└── docs/
    └── visual-diff-report.md          # final diff report from Phase 5
```

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "I'll just use `#3b82f6` here, fix the token later" | You won't. Stop and create the token. |
| "The diff is small, close enough" | Small diffs compound. Fix it. |
| "Visual verification slows me down" | One mismatch caught early = 10 minutes. Mismatch discovered at end = an hour rebuilding. |
| "shadcn's Button is basically what Figma has" | "Basically" = the source of the mismatch you came here to fix. Customize. |
| "I'll batch the visual checks at the end" | You'll skip them. Do them per-atom. |
| "Figma doesn't have variables so I can't extract" | Then walk the layers and infer them. Approval first, then proceed. |
| "Icons are close enough" | They almost always aren't. Map every icon explicitly. |
| "Final diff was clean, no need to re-check" | Re-check anyway. The diff lies sometimes. |

## Red Flags — STOP

- About to write a raw hex value or px in component code
- About to mark a component "done" without screenshot comparison
- About to compose components when an atom hasn't been verified
- About to skip Phase 1 because "shadcn defaults are fine"
- About to declare the project complete without a final visual diff report

**All mean: stop. Return to the iron laws.**

## Pairs With

- `prototyping` — if you just need clickable, not pixel-perfect, use `prototyping` instead
- `design-qa` — runs after Phase 5 to catch any remaining issues (different lens — `design-qa` reviews the design itself, this skill verifies the implementation matches)
- `handoff` — if engineering takes over, the handoff doc references the verified atoms + diff report

## Iteration Notes (v0.1)

Things to watch as the skill gets real usage:
- Is Tailwind v4 (CSS-first) the right default, or does v3 work better for some Figma → Tailwind mappings?
- Is `Claude_Preview` reliable enough for the verification loop, or do we need a different screenshot path?
- How often does Figma lack variables — and when it does, is the inference step fast enough?
- Does the per-atom verification loop scale to designs with 50+ components, or does it become tedious?
- Is the diff report format readable, or does it need a different structure?

Bring observations back to refine v0.2.
