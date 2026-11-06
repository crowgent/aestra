---
name: aestra
description: Design and build clean, polished, production-grade UI/UX — for new builds and redesigns — using design tokens, component specs, motion rules, and anti-AI-look taste guidance. Use when the user asks to design, build, restyle, modernize, or polish a user interface, landing page, dashboard, app screen, design system, or component library.
license: MIT
metadata:
  version: 1.0.0
  author: crowgent
  email: crowgent@gmail.com
---

# Aestra

A design agent for producing **clean, polished, production-grade UI/UX** across web, mobile,
and desktop (Windows / macOS / Linux). It works two ways:

1. **Greenfield** — create a new website, web app, mobile app, or desktop app.
2. **Redesign** — take an existing interface and raise it to a modern, coherent standard.

The goal is not "make it pretty". The goal is a **coherent design system** — tokens, components,
states, motion, and accessibility — that looks intentional on every platform and scales as the
product grows.

## When to use

Invoke this skill whenever the task is about how software *looks and feels*:

- Build a new UI: landing page, dashboard, SaaS app, mobile app, desktop app.
- Redesign / modernize / restyle an existing UI or component.
- Create or extend a design system, theme, tokens, or component library.
- Fix polish issues: inconsistent spacing, weak hierarchy, harsh motion, poor dark mode, a11y.
- Explore multiple design directions before committing to one.

Do **not** use it for pure backend, data, or infrastructure work with no UI surface.

## The CRAFT method

This skill runs on an original five-step method — **C.R.A.F.T.** — that turns any design request
into a coherent, ship-ready system. Every phase has an owner reference file.

| Step | Name | What happens | Reference |
|------|------|--------------|-----------|
| **C** | **Context** | Nail the product, audience, platform, stack, and constraints before drawing anything. | [platform-guidelines.md](references/platform-guidelines.md) |
| **R** | **Rhythm** | Build the token foundation — color, type, space, radius, elevation. One scale, no magic numbers. | [design-principles.md](references/design-principles.md) |
| **A** | **Architecture** | Structure tokens → primitives → components → patterns → screens with a clean component API. | [design-system.md](references/design-system.md) |
| **F** | **Feel** | Add motion, states, and interaction feedback that explain hierarchy — never decoration. | [motion-and-interaction.md](references/motion-and-interaction.md) |
| **T** | **Test** | Harden: contrast, responsive, themes, states, a11y, performance, cross-platform parity. | [workflow-and-checklist.md](references/workflow-and-checklist.md) |

For greenfield work, run C→R→A→F→T. For a redesign, run **C-Context first on the existing product**,
then T-audit before R/A/F so you know exactly what to preserve.

## Core philosophy

- **Name the taste first.** Every build commits to one explicit design direction (editorial/Swiss,
  neo-grotesk, terminal, brutalist, soft/tactile). Never average everything into a generic template.
  See [anti-ai-look.md](references/anti-ai-look.md) — this is the difference between "designed" and
  "AI-generated".
- **Design tokens over hard-coded values.** Never scatter raw hex codes, magic pixel numbers,
  or ad-hoc shadows through components. Everything references a token.
- **Explore before you commit.** For any non-trivial screen, generate **2–3 distinct directions**
  first (vary layout, density, type scale, color temperature), then converge on one. One option is
  a guess; three options is a decision.
- **Motion is meaning, not decoration.** Animate to explain hierarchy, state change, and
  spatial relationships — never to show off. Restrained, fast, interruptible, and respectful of
  `prefers-reduced-motion`. Default to no entrance animation: content is visible immediately;
  do not add scroll-reveal/stagger/parallax unless it communicates real information.
- **Edit out decoration.** Every dot, star, arrow, separator, badge, stat, and label must carry
  meaning. If it is only there to make the design look “designed,” remove it.
- **Honor visual references.** Extract their hierarchy, type, whitespace, palette, controls, and
  motion. Do not invent marks, accents, metadata, or effects the reference does not call for.
- **Every state is designed.** Default, hover, focus, active, disabled, loading, empty, error, and
  success are all part of the component — not afterthoughts.
- **Accessible by default.** Contrast, focus rings, hit targets, semantics, and keyboard flows are
  built in, not retrofitted.
- **Platform-native where it matters.** Respect iOS/Android/Material and Windows(Fluent)/macOS(HIG)
  conventions for navigation, controls, and gestures — while keeping the brand consistent.

## Workflow

Follow these phases. Skip phases only when the task is genuinely trivial.

### 1. Understand (do not skip)
Establish: product & audience, primary user task, platform(s) & tech stack, brand constraints,
existing design assets/system, and success criteria. If the request is vague, ask **at most 3**
sharp questions — or state your assumptions explicitly and proceed.

### 2. Choose the architecture
Decide the target platform and stack before designing, because it dictates tokens and components.
See [platform-guidelines.md](references/platform-guidelines.md) and
[design-system.md](references/design-system.md).

- **Web** → HTML/CSS or React/Next + Tailwind + CSS custom properties; Motion for animation.
- **Mobile** → React Native / Expo, Flutter, SwiftUI, or Jetpack Compose.
- **Desktop** → Tauri / Electron (web stack), macOS SwiftUI, or Windows WinUI 3 / Fluent.

### 3. Establish the design foundation
Define tokens **first**: color (semantic roles), type scale, spacing scale, radius, elevation,
motion. See [design-principles.md](references/design-principles.md) and
[design-system.md](references/design-system.md). Document them as the single source of truth.

### 4. Explore directions (2–3 variants)
Produce 2–3 genuinely different options for the key screen(s). Each variant must be a complete,
buildable direction — not a color swap. Present them with a one-line rationale each, then converge.

### 5. Build with component architecture
Compose from tokens + primitives → components → patterns → screens. Keep components small,
props-driven, and state-complete. Mirror the folder/architecture conventions in
[design-system.md](references/design-system.md).

### 6. Add motion & interaction
Apply entrance, transition, gesture, and layout motion using the duration/easing tokens. See
[motion-and-interaction.md](references/motion-and-interaction.md).

### 7. Review & harden
Run the full pass in [workflow-and-checklist.md](references/workflow-and-checklist.md): contrast,
responsive behavior, all states, dark mode, motion-reduction, performance, and cross-platform
consistency.

## Redesign mode

When modernizing an existing UI, never break behavior:

1. **Audit** — inventory current screens, components, and inconsistencies; capture the real
   problems (spacing chaos, weak hierarchy, low contrast, dated type, heavy motion).
2. **Preserve intent** — keep information architecture, flows, and copy unless asked to change them.
3. **Re-tokenize** — map existing hard-coded values to a new token set; this is where most of the
   lift happens.
4. **Restyle incrementally** — apply the new system component by component; show before/after.
5. **Verify parity** — every old state and edge case still works; then improve it.

See [workflow-and-checklist.md](references/workflow-and-checklist.md) for the detailed redesign flow.

## Non-negotiables

- No hard-coded colors, spacing, or shadows outside the token layer.
- WCAG AA minimum (4.5:1 text, 3:1 UI); focus visible on every interactive element.
- Touch targets ≥ 44×44pt (iOS) / 48×48dp (Android) / 40px (desktop pointer, with larger hit areas).
- Motion ≤ ~300ms for UI transitions; honor `prefers-reduced-motion`.
- No scroll-reveal, stagger, parallax, or looping motion by default; essential content is visible
  immediately without JavaScript.
- Light **and** dark themes both fully designed.
- Loading, empty, error, and offline states designed for every data surface.
- **No generic AI look:** one accent on <10% of pixels, borders over default shadows, small
  consistent radii (no bubbly pill-everything), real type-scale contrast, break symmetry on purpose,
  designed press/hover/focus states, zero marketing filler copy. See
  [anti-ai-look.md](references/anti-ai-look.md).
- Components match the exact specs in [component-recipes.md](references/component-recipes.md)
  (button/input/card/nav/table/… sizing, variants, and the full state matrix).

## Reference files

| File | Use it for |
|------|-----------|
| [anti-ai-look.md](references/anti-ai-look.md) | Tells of the generic "AI look" and how to make UI hand-crafted; taste directions |
| [component-recipes.md](references/component-recipes.md) | Exact specs for buttons, inputs, cards, nav, tables, modals, states |
| [design-principles.md](references/design-principles.md) | Visual fundamentals: hierarchy, type, color, spacing, layout, states, a11y |
| [design-system.md](references/design-system.md) | Token architecture, component API, theming, folder structure, cross-platform mapping |
| [motion-and-interaction.md](references/motion-and-interaction.md) | Durations, easings, gestures, layout animation, reduced-motion, performance |
| [platform-guidelines.md](references/platform-guidelines.md) | Web, iOS, Android, macOS, Windows conventions and breakpoints |
| [workflow-and-checklist.md](references/workflow-and-checklist.md) | Step-by-step build/redesign flow and the final QA checklist |
