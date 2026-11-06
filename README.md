<div align="center">

<a href="#install"><img src="https://img.shields.io/badge/install-npx%20skills%20add%20crowgent%2Faestra-FF5A2B?style=flat-square&labelColor=0D0D0B" alt="Install: npx skills add crowgent/aestra" /></a>
<a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-2E2C26?style=flat-square&labelColor=0D0D0B" alt="License: MIT" /></a>

</div>

**Aestra** is an agent skill for clean, polished, production-grade UI/UX — new builds and redesigns.

> One accent colour on under 10% of the pixels. Borders over shadows. Real type contrast. Small
> radii. No gradients, no pill-everything, no marketing filler.

Works in any `SKILL.md`-compatible agent — Claude Code, Cursor, Codex, Copilot, Windsurf, OpenCode.

---

## Install

```bash
npx skills add crowgent/aestra
```

> Add `-g` to install globally, `--list` to preview without installing, or `--skill aestra -g -y`
> to skip the prompts.

Then describe the interface you want.

```text
Build a pricing page for a developer tool. Editorial taste, one accent colour, no gradients.
```

```text
This UI looks AI-generated. Audit it and remove the tells.
```

---

## What it does

- **Build** — new websites, apps and desktop surfaces, from tokens up.
- **Redesign** — audit an existing UI, keep its flows, raise the bar.
- **Design systems** — tokens, theming, light/dark, component APIs.
- **Polish** — spacing, hierarchy, contrast, dark mode, motion.

## The CRAFT method

| Step | Name | What happens | Reference |
|:----:|------|--------------|-----------|
| **C** | Context | Product, audience, platform, stack — before drawing. | `platform-guidelines.md` |
| **R** | Rhythm | Colour, type, space, radius, elevation tokens. | `design-principles.md` |
| **A** | Architecture | Tokens → primitives → components → patterns → screens. | `design-system.md` |
| **F** | Feel | Motion and states that explain hierarchy. | `motion-and-interaction.md` |
| **T** | Test | Contrast, responsive, themes, a11y, performance. | `workflow-and-checklist.md` |

> Also inside — [`anti-ai-look.md`](aestra/skill/references/anti-ai-look.md): the tells of
> AI-generated UI and how to remove them · [`component-recipes.md`](aestra/skill/references/component-recipes.md):
> exact specs for buttons, inputs, cards, nav, tables and their states.

---

## Compatibility

A plain `SKILL.md` skill following the Agent Skills standard — no scripts, no network calls, no
build step.

## License

[MIT](LICENSE) © 2026 crowgent

<div align="center">
<br />
<a href="https://skills.sh/crowgent/aestra"><img src="https://img.shields.io/badge/skills.sh-crowgent%2Faestra-2E2C26?style=flat-square&labelColor=0D0D0B" alt="skills.sh" /></a>
</div>
