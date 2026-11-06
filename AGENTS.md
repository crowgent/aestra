# AGENTS.md

Passive context for agents working **inside this repository**. It applies to every task here —
editing the skill, adding references, or touching the README — and needs no activation.

This is different from [aestra/skill/SKILL.md](aestra/skill/SKILL.md): the skill is *active*
context (loaded only when someone asks for UI work), while this file is *passive* context that is
always read.

## What this repository is

Aestra is a single skill packaged for the [Agent Skills](https://agentskills.io) standard: one
folder containing a `SKILL.md` with YAML frontmatter (`name` + `description`) plus a `references/`
folder that the skill loads on demand.

- **Skill name:** `aestra` — must match the folder that contains `SKILL.md`.
- **Entry point:** [`aestra/skill/SKILL.md`](aestra/skill/SKILL.md)
- **Install:** `npx skills add crowgent/aestra`

## Layout

```text
aestra/                  # repository root
├── AGENTS.md            # this file — instructions for agents in the repo
├── README.md            # human-facing overview (this is what skills.sh displays)
├── LICENSE
└── aestra/
    └── skill/
        ├── SKILL.md     # metadata + routing rule + the CRAFT method
        └── references/  # detail, loaded only when SKILL.md points to a file
```

## Conventions

- **Frontmatter is a contract.** `name` stays `aestra` and must keep matching the folder holding
  `SKILL.md`. `description` is a routing rule, not a title: it must say *what* the skill does and
  *when* to use it, because that is what decides whether the skill loads.
- **Keep `SKILL.md` short.** Progressive disclosure: the body holds the workflow and the
  non-negotiables; anything longer moves into `references/`.
- **Plain Markdown only.** No build step, no dependencies, no scripts, no network calls.
- **Practice what the skill preaches.** Every example in this repo — including README snippets —
  must obey the skill's own rules: one accent under 10% of the surface, borders over default
  shadows, small consistent radii, no gradient, no decorative dots/stars/arrows, real copy.
- **Prose style.** Sentence case for headings, present tense, no marketing filler
  ("seamlessly", "empower", "unlock"). Explain, don't sell.

## Adding or editing a reference file

1. Create or edit `aestra/skill/references/<topic>.md`.
2. Link it from the reference table in `SKILL.md` with a one-line "use it for".
3. List it in `README.md` — in the CRAFT table's Reference column, or the reference note below it.
4. Keep the heading style of the existing reference files so the set reads as one document.

## Before committing

- [ ] `name` in the frontmatter still equals the folder name containing `SKILL.md`.
- [ ] Every reference file linked from `SKILL.md` exists on disk.
- [ ] `README.md` has no broken relative links.
- [ ] The skill is still discoverable: `npx skills add crowgent/aestra --list` reports one skill.
- [ ] No hard-coded colour, spacing, or shadow values were introduced into any example.

## Out of scope

Do not add a build system, bundler, package manifest, or CI pipeline. This repo ships Markdown and
nothing else — keeping it dependency-free is the point.
