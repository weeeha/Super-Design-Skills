---
name: prototyping
description: Use when building a clickable code prototype - from Figma designs, screenshots, a sketch, a written idea, or a change to an existing live app - for user testing, stakeholder demos, or de-risking before engineering handoff
---

# Prototyping

## Overview

Turn designs into a clickable, runnable browser prototype. The source can be Figma frames, screenshots, a sketch, a written idea, or an app that already exists. **Vite + React + TypeScript + Tailwind + shadcn**, opinionated defaults, throwaway code quality. Goal: from "I have screens in Figma" to "here's a URL you can click" in under 30 minutes.

This is NOT a production codebase. The prototype's job is to feel real enough to test or demo. The code is meant to be deleted after the design decision lands.

## When to Use

- After `exploring-options` — test one of the directions in code, not just sketches
- Before `presenting` — clickable demo lands better than static slides
- Before `handoff` — de-risk what engineering is about to commit to
- During `design-qa` when something feels off — prototype the fix to see it
- For user testing — need a thing real users can click

**Don't use** for:
- The actual engineering build (that's `handoff` plus the eng team)
- Static visual mockups (Figma is better)
- Motion/animation-heavy concepts (Framer / Principle / After Effects beat this stack)
- Throwaway sketches under 5 min (a Figma prototype with hotspots is faster)

## Inputs

Four modes. A and B mirror `design-qa`. C and D start without finished designs:

### Mode A — Figma link (preferred)
User provides a Figma URL. Use the connected Figma MCP server. Tool names below carry no server prefix, because the prefix depends on the setup:
- `get_design_context` — structure, hierarchy, variants
- `get_screenshot` — visual reference per frame
- `get_variable_defs` — design tokens (colors, spacing, typography)
- `get_metadata` — layer tree
- `get_code_connect_map` — if components are mapped to code

Richest mode. Use this whenever possible.

### Mode B — Screenshots
User pastes/uploads images. Visual analysis only. Tokens have to be inferred. Lossier but works for designs you can't link to.

### Mode C - Sketch or written idea
The source is a `sketching` output, a spec, or a paragraph. There is no visual source of truth, so:
- Take the layout from the sketch and the content from the spec
- Use shadcn defaults, or the project's design system when the user names one. Do not invent a brand
- Record every visual decision the source did not make in the README, under "Decisions I made"

### Mode D - Existing live app
The user wants to try a change inside a product that already exists, and gives a URL or a repo.
- With a repo that is the user's to change: reuse its components and tokens, on a branch
- With only a URL: capture the current screens, match the look in Tailwind, and build in a separate folder
- Prototype only the flow that changes. Screens that are just context can stay as static screenshots

**Ask which mode** if it's unclear. Modes can mix (Figma for structure, screenshot for one missing screen, a sketch for the screen nobody has designed yet).

## The Process

### 1. Read the design

In Mode A:
1. Call `get_metadata` to see the frame structure
2. Identify which frames are "screens" vs which are "components/states"
3. Call `get_design_context` on each screen frame
4. Call `get_variable_defs` to pull color/spacing/type tokens
5. Call `get_screenshot` on each screen for visual reference

In Mode B:
1. Read each screenshot
2. Identify screens, components, states
3. Infer colors, spacing (round to Tailwind scale: 4, 8, 12, 16, 24, 32, 48), typography

In Mode C:
1. Read the sketch or spec. List the screens and the one flow to click through
2. Collect the real content: labels, object names, realistic counts
3. List every visual decision the source does not make. You will make them and report them

In Mode D:
1. Open the app in a browser tool, or read the repo's routes and components
2. Capture the current screens the change touches
3. Pull the look from the repo's tokens, or from computed styles: font, radius, spacing, colors
4. Mark which screens change and which are only context

Note what you can't determine — flag it in the README later.

### 2. Plan the prototype

Before scaffolding, write a quick plan to the user:

```
## Prototype plan

### Screens (routes)
- /home — home screen
- /onboarding — onboarding flow
- /settings — settings

### Components needed (shadcn primitives)
- Button, Input, Card, Dialog, Sheet, Select

### Custom components
- DataTable (no shadcn equivalent)

### Interaction wiring
- Home → "Get Started" CTA → /onboarding
- Onboarding → "Continue" → /settings
- Settings → form fields editable but not persisted

### What I'll fake
- Charts → placeholder div with bounding-box dimensions
- Real user data → 3 mocked items in useState

Proceed?
```

Wait for "yes" before scaffolding. Don't burn time on the wrong shape.

### 3. Scaffold

Mode D with a repo: skip this step. Work on a branch of that repo and put the changed screens behind their own route. Every other case, including Mode C and Mode D with only a URL, scaffolds in `prototypes/` as below.

Create the prototype directory:

```bash
PROTOTYPE_DIR="prototypes/<kebab-topic>-$(date +%Y-%m-%d)"
mkdir -p "$PROTOTYPE_DIR"
cd "$PROTOTYPE_DIR"
```

Initialize the stack. Use `bun` (faster than npm), fall back to `pnpm` then `npm` if bun isn't available:

```bash
# Pick package manager
PM=$(command -v bun >/dev/null && echo bun || (command -v pnpm >/dev/null && echo pnpm || echo npm))

# Scaffold Vite + React + TS
$PM create vite@latest . --template react-ts -- --no-git
$PM install

# Tailwind (latest — let shadcn init handle the config)
$PM add -d tailwindcss@latest @tailwindcss/vite

# Router
$PM add react-router-dom

# shadcn — init with sensible defaults
$PM dlx shadcn@latest init -d
```

Configure `vite.config.ts` for the Tailwind plugin and `@/*` path alias. Configure `tsconfig.json` for the alias.

If `vercel:shadcn` skill is available, consult it for the exact current setup commands — Tailwind/shadcn evolves and the source of truth is that skill.

### 4. Translate Figma → React

Build screen-by-screen. For each screen:

1. Identify the shadcn primitives needed (see translation table below)
2. Install them: `$PM dlx shadcn@latest add <component>`
3. Compose the screen using primitives + Tailwind for layout/spacing
4. Pull colors and typography from Figma variables → Tailwind classes
5. Wire navigation: `useNavigate` from `react-router-dom`
6. Wire local state: `useState` (no global state, no zustand, no redux)

In Mode C there are no Figma variables: compose from the sketch with shadcn defaults. In Mode D, match the look captured in step 1 instead.

### 5. Wire clickability

**Clickable level (default):**
- Primary CTAs navigate to next screen
- Form fields accept input (controlled via useState)
- Toggles, checkboxes, selects work locally (state in component)
- Tabs work (state-driven)
- Dialogs/sheets open and close
- Lists render from a mocked array in useState

**Not in clickable mode (skip unless asked):**
- Form validation
- Persistence (localStorage / DB)
- Real async / loading states (use instant transitions)
- Animations / motion libraries
- Authentication / authorization
- Error states beyond the obvious

If the user wants any of those, escalate to "fully wired" — say so explicitly: *"You're asking for X which is beyond clickable. Adding it as a one-off."*

### 6. Write the README

In the prototype directory, write a `README.md`:

```markdown
# <Topic> — Clickable Prototype

Built from: <Figma URL, "screenshots", sketch or spec link, or the app's URL>
Built on: YYYY-MM-DD

## Run

\`\`\`bash
bun install
bun dev
\`\`\`

Opens at http://localhost:5173.

## Screens

- `/home` — home screen. Clickable: "Get Started" CTA → /onboarding
- `/onboarding` — onboarding flow. Clickable: ...
- `/settings` — settings. Form fields editable, not persisted.

## What's wired

- Navigation between all screens
- Form inputs accept text
- Toggles and selects work locally
- Modal opens/closes

## What's faked

- Charts rendered as bounding-box placeholders
- User data is mocked (3 hardcoded items)
- No real API calls
- No data persistence (refresh resets)
- No animations (transitions are instant)

## Known mismatches from the design

- <thing 1, e.g. "icon X not available in lucide, substituted with similar">
- <thing 2>

## Decisions I made (Modes C and D only)

- <visual or layout decision the source did not make, e.g. "two-column layout on the detail screen">

## Stack

- Vite + React + TypeScript
- Tailwind CSS
- shadcn/ui components
- React Router for navigation
```

### 7. Verify

Run `bun dev`. Open the URL. Walk every clickable path. Confirm:
- All routes load
- All CTAs navigate correctly
- Form fields accept input
- Modals open/close
- No console errors

Report results back. If anything is broken, fix and re-verify.

## Translation Rules (Figma → React)

| Figma | shadcn / Tailwind |
|---|---|
| Button frame | `<Button variant="...">` from shadcn |
| Input field | `<Input />` from shadcn |
| Textarea | `<Textarea />` from shadcn |
| Card / container | `<Card>` with `<CardHeader>`, `<CardContent>`, `<CardFooter>` |
| Modal / overlay | `<Dialog>` from shadcn |
| Side panel / drawer | `<Sheet>` from shadcn |
| Tab navigation | `<Tabs>` from shadcn |
| Dropdown select | `<Select>` from shadcn |
| Toggle | `<Switch>` or `<Toggle>` |
| Checkbox | `<Checkbox>` |
| Radio | `<RadioGroup>` |
| Avatar | `<Avatar>` |
| Badge / chip | `<Badge>` |
| Tooltip | `<Tooltip>` |
| Toast / notification | `<Toast>` via `sonner` |
| Dropdown menu | `<DropdownMenu>` |
| Layout grids | Tailwind `grid grid-cols-N gap-X` |
| Flex rows | Tailwind `flex items-center gap-X` |
| Spacing tokens | Tailwind scale (4, 8, 12, 16, 24, 32, 48) — map closest match |
| Colors | Tailwind CSS vars from Figma variables; fallback to closest Tailwind color |
| Typography | Tailwind `text-{size}` + `font-{weight}` from Figma styles |
| Icons | `lucide-react` — closest visual match |
| Charts | placeholder `<div>` with bounding-box dimensions (skip the lib) |
| Custom complex component | Build minimally with Tailwind, no fancy abstraction |

When shadcn doesn't have a primitive: build the simplest React + Tailwind version. Do NOT invent reusable component libraries for a throwaway prototype.

## Output Structure

```
prototypes/<topic>-YYYY-MM-DD/
├── README.md
├── package.json
├── vite.config.ts
├── tsconfig.json
├── tailwind.config.js (or @tailwindcss/vite config)
├── components.json (shadcn config)
├── index.html
└── src/
    ├── main.tsx
    ├── App.tsx              # router setup
    ├── index.css            # tailwind + theme vars
    ├── pages/
    │   ├── HomePage.tsx
    │   ├── OnboardingPage.tsx
    │   └── SettingsPage.tsx
    ├── components/
    │   ├── ui/              # shadcn primitives (auto-added)
    │   └── custom/          # one-off prototype components
    └── lib/
        └── utils.ts         # cn() helper from shadcn
```

Keep flat. No nested feature folders. Throwaway = readable, not "scalable."

## What This Skill Doesn't Do

- **Production code quality** — no lint, no tests, no perfection
- **Real backends** — mock everything in useState
- **Motion / animation** — use Framer / Principle / Lottie outside this skill
- **Accessibility audit** — `design-qa` does that after, not as part of this
- **Performance optimization** — irrelevant for throwaway
- **Multi-developer collaboration** — no shared state libs, no monorepo, no CI

## Common Pitfalls

- **Over-engineering.** Don't add Zustand for two state values. `useState` is enough.
- **Faithful copy of bad designs.** If the Figma has issues, this isn't the moment to fix them — that's `critiquing`. Build what's in Figma; flag concerns separately.
- **Forgetting the README.** Without it, the prototype is unintelligible 3 days later. Always write it.
- **Trying to match pixel-perfect.** Close enough is the goal. If a shadow is 4px off, leave it. If a color is one Tailwind step off, leave it.
- **Skipping the plan step.** Scaffolding without a plan wastes 20 minutes when you discover you needed a different shadcn primitive.
- **Building components that don't exist in Figma.** Prototype what's there, not what should be there. (Modes A and B. In Modes C and D you do make decisions; list them in the README.)

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "I need real form validation" | You don't, for a clickable. Skip it. |
| "Should use Next.js for SSR" | No SSR. Vite is fine for a prototype. |
| "Let me add a state library" | useState is enough for throwaway. |
| "I'll add animation for polish" | Out of scope. That's a different prototype. |
| "Let me make the components reusable" | They're for one prototype. No reuse. |
| "I should test it manually first" | Step 7 IS the manual test. Do that. |

## Pairs With

- `exploring-options` — test one of the directions you generated
- `sketching` - the chosen sketch is the source for Mode C
- `design-qa` — after the prototype is built, QA the visual fidelity against the Figma
- `presenting` — the prototype becomes the demo in stakeholder reviews
- `handoff` — prototype de-risks what engineering will build; handoff doc references it
- `verifying-before-shipping` — confirms the prototype meets its "feels real enough" bar before sharing

## Iteration Notes (v0.1)

Things to watch as this skill gets real usage:
- Is Vite the right default, or is Next.js better for some prototypes?
- Is `bun` reliably available across teammates' machines?
- Does shadcn's component set cover 80%+ of Figma patterns in practice?
- Does Mode B (screenshot only) produce acceptable fidelity?
- How often do users want motion/animation despite the "out of scope" rule?

Bring observations back. This skill will need v0.2.
