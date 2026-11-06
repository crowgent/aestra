# Component Recipes

Opinionated, concrete specs so components look **designed**, not generated. Values are defaults —
adapt to the chosen taste, but always be this precise. Every component must define all its states.

Conventions used below: sizes in px; heights are control heights; `radius-md` ≈ 10px; tokens refer
to the design-system layer.

---

## Button

**Anatomy:** container → (optional leading icon) → label → (optional trailing icon).

| Size | Height | Padding-x | Font | Gap | Icon |
|------|--------|-----------|------|-----|------|
| sm | 32 | 12 | 13/500 | 6 | 16 |
| md | 40 | 16 | 14/550 | 8 | 18 |
| lg | 48 | 20 | 15/600 | 8 | 20 |
| touch | ≥44 | 18 | 15/550 | 8 | 20 |

**Variants**
- **primary** — solid accent bg, `accent-contrast` text. One per view.
- **secondary** — `surface` bg + 1px `border` (hairline), `text` color.
- **ghost** — transparent; hover fills `surface-2`.
- **danger** — solid or outline in `danger`.
- **link** — text-only, underline on hover.

**States** (all required)
- hover: bg shifts ~6% (darken/lighten); **no scale-up**.
- active/press: translateY(1px) + bg −4% (this is the tell most AI buttons miss).
- focus-visible: 2px ring in `accent`, offset 2px.
- disabled: opacity .5, `cursor: not-allowed`, no hover.
- loading: preserve width, replace label with a 14px spinner, keep height.

**Do:** sentence case; optically center icons; equal height across a row; radius = `radius-md`.
**Don't:** pill by default; gradients; glow; >1 primary on a screen; drop shadow on ghost.

---

## Icon button

Square: 32/36/40 (sm/md/lg), radius `radius-sm`, icon 18/20. Ghost by default; fills `surface-2` on
hover. Always has an accessible label (`aria-label`).

---

## Input / Textarea

- Height 40 (44–48 touch); radius `radius-md`; bg `surface`; 1px `border`; padding-x 12–14.
- Font **16px minimum on mobile** (prevents iOS zoom); 14px desktop.
- **Label always visible above** (never placeholder-as-label). Optional helper text below.
- States: default → hover (`border-strong`) → focus (1px `accent` border + 2px `accent` ring) →
  invalid (`danger` border + error text) → disabled (`surface-2` bg, muted text) → read-only.
- Placeholder is a short example, muted; not an instruction paragraph.
- Textarea: min 3 rows, vertical resize only.

---

## Select / Dropdown

- Trigger styled like an input; caret icon right, 18px, `text-3`.
- Menu: `surface` bg, 1px border, `radius-md`, shadow-sm, 8px padding, 4px item gap.
- Item: height 36, radius `radius-sm`, hover `surface-2`; selected shows a check, not just color.
- Animate: fade + scale 0.97→1 from the trigger origin, ≤180ms.

---

## Card

- bg `surface`, 1px `border`, `radius-lg`, padding 16–24 (scale with importance).
- Static cards: **no shadow**. Interactive cards: shadow-sm + hover translateY(−3px) + `border-strong`.
- Content order: optional eyebrow/label → title → body → meta/actions.
- Don't make every card identical; vary emphasis (hero card, compact rows).

---

## Navigation bar

- Height 64–72; container max-width with consistent gutters; brand left, actions right.
- Sticky with `backdrop-blur` and a **1px bottom border that appears only on scroll**.
- Nav links: 14/500, `text-2` → `text` on hover, 8–12px padding, `radius-sm` hover bg.
- Mobile: collapse to a menu; keep primary CTA visible.

---

## Badge / Tag

- Height 22–26, padding-x 8–10, radius `radius-full` (tags may be full) or `radius-sm`.
- Font 12/500 mono-optional. Variants: subtle (surface-2 + border), accent (tinted), status
  (success/warning/danger with tinted bg at ~12% opacity + colored text).

---

## Tooltip

- `surface-2` bg, 1px border, radius `radius-sm`, 12/13px text, padding 6–8, max-width 240.
- Fade + 4px rise, origin-aware, delay ~200ms, dismiss on scroll/Esc.

---

## Modal / Dialog

- Backdrop: `rgba(0,0,0,.5)` + subtle blur; panel `surface`, `radius-lg`, shadow-lg, max-width 480–640.
- Enter: backdrop fade + panel scale 0.96→1 & 8px rise (≤220ms). Exit faster (~150ms).
- Trap focus, restore focus on close, close on Esc + backdrop click, `role="dialog"` + labelled.

---

## Toast

- Bottom-right (desktop) / bottom (mobile); `surface` + border + shadow-md; radius `radius-md`.
- Status icon + title + optional action; auto-dismiss 4–6s; slide+fade in, fade out.
- Stack max 3; never block critical UI.

---

## Table (data)

- Header: 12/600 uppercase, `text-3`, letter-spacing +0.04em, bottom hairline.
- Row height 44 (comfortable) / 36 (compact); hover row `surface-2`; zebra optional, subtle.
- Right-align numbers; tabular-nums; sticky header for long lists.
- Empty state inside the table body; skeleton rows while loading.

---

## Tabs

- Underline style: 14/600, active = `text` + 2px `accent` underline; inactive `text-3`.
- Pill style: active = `surface-2` bg, no neon fill. 8px gap, radius `radius-sm`.
- Keyboard: arrow keys move, Enter/Space select.

---

## Empty state

- Centered, max-width 360: icon/illustration → short headline → one-line explanation → primary action.
- Never just "No data". Give context and a next step.

---

## Skeleton / loading

- Shapes mirror the final layout exactly; `surface-2` base.
- Gentle opacity pulse (~1.4s), **not** a fast flash or moving shine by default.
- For actions, use in-button spinners; for pages, use skeletons, not full-page spinners.

---

## Avatar

- Sizes 24/32/40/48; `radius-full` for people, `radius-md` for entities/logos.
- Fallback = initials on a neutral tinted bg (deterministic color per user), never a random gradient.

---

## Focus, motion & a11y baseline (applies to every component)

- Focus-visible ring: 2px `accent`, offset 2px — designed, not the browser default.
- Transitions use motion tokens (≤ 220ms for components); respect `prefers-reduced-motion`.
- Hit targets ≥ 44pt / 48dp on touch; ≥ 32px with forgiving padding on desktop.
- Every interactive element: keyboard reachable, correct role/state (`aria-pressed`, `aria-expanded`,
  `aria-invalid`, `disabled`), and a visible label.
