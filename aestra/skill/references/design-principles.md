# Design Principles

The fundamentals every screen must satisfy. These are the rules that make UI look "clean and
polished" instead of amateur. Apply them everywhere, on every platform.

## 1. Visual hierarchy

- Every screen has **one primary action**. The eye should land there first.
- Establish hierarchy with, in order of strength: **size → weight → color/contrast → position →
  whitespace**. Do not rely on size alone.
- Limit type sizes per screen to ~4–5 steps. More than that reads as noise.
- Use a clear reading order (F-pattern for text-heavy, Z-pattern for marketing pages).
- De-emphasize with the *muted* text color and smaller weight, not by inventing new grays.

## 2. Spacing & rhythm

- Use a **single spacing scale** with a base unit (4px or 8px). Every margin/padding/gap is a
  multiple of it. Never hand-pick "13px".
- Suggested scale: `2, 4, 8, 12, 16, 24, 32, 48, 64, 96`.
- **Proximity = meaning.** Related items sit closer than unrelated ones. Group with space before
  reaching for borders or cards.
- Keep consistent page gutters and a max content width (e.g. 1200–1440px) with generous margins.
- Vertical rhythm: consistent section padding (e.g. desktop 96px, mobile 48–64px).

## 3. Typography

- Pick **one primary family** (plus one optional mono for code/data). Do not mix many fonts.
- Suggested modern default: a variable geometric/grotesk sans (e.g. Geist, Inter, Satoshi) with
  `-apple-system, "Segoe UI"` fallbacks. Avoid system-default-only.
- Define a **type scale** (e.g. `12, 14, 16, 20, 24, 32, 40, 56, 72`) with paired line-heights.
- Rules of thumb: body 16px/1.5, small 14px/1.45, caption 12px/1.4; headings line-height 1.1–1.3.
- Use `letter-spacing`: slightly negative for large display text (−1 to −2%), 0 or positive for
  small caps/labels.
- Constrain line length to **45–75 characters** for readability.
- Use `text-wrap: balance` on headings and `pretty` on body where supported.

## 4. Color

- Build a **semantic** color system, not a palette of pretties:
  `background, surface, surface-elevated, border, text-primary, text-secondary, text-muted,
  primary, primary-hover, accent, success, warning, danger, info, focus-ring`.
- Each role needs values for **light and dark** themes.
- Generate a primary ramp (50→900). Use 500–600 for the base, 600–700 for hover, 700–800 active.
- Neutrals should be slightly tinted toward the brand hue (2–6% saturation) for cohesion.
- **Contrast:** body text ≥ 4.5:1, large text ≥ 3:1, UI borders/icons ≥ 3:1, focus rings ≥ 3:1
  against adjacent colors.
- Never use pure `#000`/`#fff` as the primary text/background; use near-black (#0B0B0F) and
  off-white (#FAFAFA) to reduce harshness.
- Reserve saturated color for emphasis and status; most surfaces stay neutral.

## 5. Shape, depth & elevation

- Pick a **radius scale** (`sm 6, md 10, lg 14, xl 20, full`) and apply consistently per component
  class. Nested elements use a slightly smaller radius than their container.
- Use depth sparingly. Prefer **borders + subtle shadow** over heavy drop shadows.
- Shadow scale should be layered and soft (low opacity, large blur) for modern, non-2000s look.
- Glass/blur effects only when they serve a purpose (overlays, nav); keep text on solid surfaces
  readable.

## 6. Layout & responsiveness

- Design **mobile-first** for mobile apps; use a 12-col grid (web) or 4-col (mobile) with consistent
  gutters.
- Define breakpoints (see platform-guidelines.md) and design the **in-between** states, not just
  "mobile/desktop".
- Content should reflow, not just shrink. Use fluid type/space sparingly (`clamp()`).
- Respect safe areas/notches on mobile and system title bars on desktop.
- Align everything to the grid; optical alignment beats mathematical when they conflict.

## 7. Component states (design all of them)

For every interactive element: **default, hover, focus-visible, active/pressed, disabled, loading**.
For every data surface: **loading (skeleton), empty, error, success, partial/offline**.
For every input: **default, filled, focused, invalid, disabled, helper/error text**.

- Use **skeletons** that match the final layout, not spinners, for content areas.
- Empty states need: an illustration/icon, a short headline, and a clear action.
- Errors explain *what happened* and *how to fix it*, in plain language, near the problem.

## 8. Accessibility (built-in)

- Semantic HTML/native elements first; ARIA only to fill gaps.
- Visible focus indicator on everything keyboard-reachable; logical tab order.
- Never encode meaning by color alone (add icon/label/text).
- Respect system settings: text size, reduced motion, high contrast, dark mode.
- Alt text, labels, and roles for all media and controls.
- Support keyboard, pointer, touch, and screen-reader flows.

## 9. Content & microcopy

- Sentence case for UI text; concise, active, human. No jargon.
- Buttons describe the action ("Save changes", not "Submit").
- Consistent terminology across the whole product.
- Numbers, dates, and currency localized and formatted per locale.

## 10. The "polish" test

A screen is polished when:
- Nothing is misaligned; spacing follows the scale everywhere.
- Hierarchy is obvious at a glance and after grayscale (test contrast without color).
- All states look considered; no raw default browser styles leak through.
- Motion feels fast, physical, and never blocks the user.
- It looks correct at every supported size and in both themes.
