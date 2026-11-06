# Anti-AI-Look

AI-generated UI has a recognizable signature. Users feel it instantly even if they can't name it.
This file is the "taste layer" — how to make generated UI look **hand-crafted and intentional**
instead of template-y. Read this before designing, and again before shipping.

## The tells (if you see these, you are producing the generic AI look)

**Color**
- Purple → indigo → pink gradient used as the primary accent on everything.
- Glow/bloom halos around buttons, cards, or text.
- Multiple saturated accents competing; nothing neutral to rest against.
- Everything tinted; no true neutrals to create contrast.
- Default `#6366F1`/`#8B5CF6`/"AI violet" as if it were a brand.

**Shape & depth**
- Uniform, oversized radius (20–28px) on every element → bubbly, toy-like.
- Pill-shaped buttons by default.
- Heavy/blurry black drop shadows, or no depth logic at all.
- Glassmorphism (frosted blur) sprinkled on ordinary surfaces.

**Layout**
- Centered hero: headline + one-line subtext + two pill CTAs + three identical feature cards.
- Every section perfectly centered with equal huge whitespace; no rhythm, no tension.
- A 3-column "Features" grid where each card = rounded icon-square + bold title + gray paragraph.
- Everything the same size/weight → no hierarchy; walls of 16px gray text.
- Perfect symmetry everywhere; no asymmetry, no editorial grid, no deliberate grouping.

**Type**
- Default Inter/Geist at default sizes; headings only slightly bigger than body.
- Loose tracking on large display text; no optical sizing.
- Emoji used as icons (🚀 ✨ 🔥) in the UI.

**Components**
- Identical cards with identical padding regardless of content importance.
- Buttons with no hover/active/press states (or only a tiny opacity change).
- Generic rounded-square icon tiles above every title.
- Decorative dots beside a brand, status, or language when they carry no information.
- Repeated separators (`·`, `|`, `→`) and numbered micro-labels used as visual seasoning.
- Scroll reveals and staggered entrances applied to every section by default.
- A visible “Built with AI / skill” credit on a portfolio where it is not real product content.

**Copy**
- Filler marketing language: "Empower", "Seamlessly", "Unlock", "Elevate", "Supercharge",
  "Take your X to the next level". Repetitive, interchangeable, says nothing.

## The fix — commit to a taste

The single biggest upgrade: **pick a real design direction and obey it**, instead of averaging
everything into beige. Choose one and let it drive every decision:

| Direction | Signals |
|-----------|---------|
| **Editorial / Swiss** | Strong type scale, tight tracking on display, hairline rules, generous margins, asymmetric grid, few colors, one bold accent |
| **Neo-grotesk product** | High contrast type, restrained neutrals, precise 4/8 rhythm, tiny radii, borders over shadows, one accent |
| **Terminal / devtools** | Monospace accents, near-black, sharp corners, subtle grid, minimal color, real density |
| **Brutalist / print** | Hard edges, visible structure, big type, off-register accents, no gloss |
| **Soft / tactile** | Warm neutrals, layered subtle shadows, generous spacing, muted accents (sparingly) |

The portfolio/landing version of this skill uses **iridescent terminal editorial** — that is *one*
taste, not the default. Always name the taste explicitly before building.

## When the user provides a visual reference

Treat the reference as a **constraint**, not a loose mood board.

1. Read its hierarchy, typography, whitespace, palette, control shape, density, and motion separately.
2. Match the qualities the user points to; do not blindly copy unrelated browser chrome or content.
3. Do not add a logo mark, dot, accent color, badges, stats, or animations that are absent from the
   reference unless the product genuinely needs them.
4. Before building, write a short reference map: “keep / avoid / adapt.” Check the result against it.
5. “Clean and rich” means precise type, strong contrast, intentional spacing, and considered controls;
   it does not mean extra visual effects or decorative metadata.

## Rules that kill the AI look

1. **Restraint on color.** One accent, used on ~5–10% of pixels. Everything else neutral.
   No rainbow gradients unless the brand really is that.
2. **Borders before shadows.** Hairline 1px borders read as "designed"; soft default shadows do not.
3. **Type carries the hierarchy.** 4–5 distinct steps with real scale jumps (e.g. 14 → 20 → 32 → 56).
   Tighten tracking as size grows. Consider one distinctive display face.
4. **Smaller radii, consistently.** Pick md (8–12px) for most UI; reserve large radius for specific
   surfaces (modals, media), not everything.
5. **Break symmetry on purpose.** Mixed column spans, off-center focal points, an editorial grid.
   Not everything centered.
6. **Design the details.** Optical alignment, precise spacing rhythm, numbered/labelled sections,
   deliberate iconography (a real set, not emoji), focus rings as a design element.
7. **Specific copy.** Real product nouns and verbs. Kill every "seamlessly/unlock/empower".
8. **Real content in the mock.** Use plausible names/numbers/labels, never lorem or "Feature One".
9. **States are designed.** Hover, active/press, focus-visible, disabled, loading — visible and
   intentional. Missing press feedback is a top AI tell.
10. **One surprising detail.** A custom cursor on a terminal, an iridescent accent, a mono label —
    one deliberate signature beats ten generic flourishes.
11. **Remove ornamental punctuation.** A dot, star, arrow, or section number must communicate
    something or be removed. Do not use punctuation glyphs as fake brand identity.
12. **Make motion earn its place.** No reveal-on-scroll or stagger by default. Keep content visible
    immediately and use small, fast state feedback only where it improves understanding.
13. **Use fewer, stronger elements.** Remove stats, badges, labels, and metadata that do not help
    the visitor decide what to do next. Restraint is not an empty template; it is editing.

## Buttons specifically (most common tell)

The default AI button: pill, filled AI-violet, no gradient, no press state, oversized.

Do instead:
- Rectangular-ish radius (8–12px), not a pill — unless the brand is explicitly pill.
- Solid accent for primary; **hairline-bordered surface** for secondary; transparent ghost for tertiary.
- Height 32/40/48 (sm/md/lg) with matching horizontal padding and an 8px icon gap.
- Real interaction states: hover shifts background ~6% (no scale), active translates 1px + darkens,
  focus-visible shows a 2px ring with 2px offset, loading keeps width and swaps label for a spinner.
- Label 14px/500–600, sentence case, tight tracking. Icons optically centered, not just flex-centered.
- Restraint: usually only **one** primary button per view.

## Self-check before shipping

- [ ] Can I name the taste/direction in one phrase?
- [ ] Is there exactly one accent color, on <10% of the surface?
- [ ] Do I use borders + type for structure rather than default shadows and boxes?
- [ ] Is there real scale contrast in the type, with tight tracking on display text?
- [ ] Are radii small and consistent (not everything bubbly)?
- [ ] Does anything break symmetry with intent?
- [ ] Is every button's hover/active/focus/disabled/loading designed?
- [ ] Zero marketing filler words; all copy specific and real?
- [ ] If I removed the accent color, would the layout still hold up (grayscale test)?
- [ ] Are all dots, stars, arrows, separators, section numbers, and status markers meaningful?
- [ ] Does the page remain complete and visible without JavaScript or animation?
- [ ] Did I remove scroll-reveal/stagger motion that adds no information?
