# Platform Guidelines

Respect each platform's conventions for navigation, controls, and gestures while keeping the brand
consistent. A design that ignores platform norms feels foreign even when it is beautiful.

## Breakpoints (web)

| Name | Min width | Target |
|------|-----------|--------|
| `sm` | 0–639 | phones |
| `md` | 640–1023 | large phones / small tablets |
| `lg` | 1024–1279 | tablets / small laptops |
| `xl` | 1280–1535 | desktops |
| `2xl` | 1536+ | large desktops |

Design at `sm`, `md`, `lg`, `xl` at minimum. Max content width 1200–1440px; side gutters scale with
viewport. Test at 320px and 2560px extremes.

## Web

- Semantic HTML first; landmarks (`header/nav/main/footer`), one `h1` per page.
- Keyboard-first: full tab order, visible focus, Escape closes overlays, focus trapping in modals.
- Hover states are expected; but never rely on hover alone for critical info.
- Scroll behavior smooth but subtle; sticky headers with shadow-on-scroll.
- Loading via skeletons; optimistic UI where safe.
- Support browser zoom to 200% without breakage.

## iOS (HIG)

- Navigation: `NavigationStack`/tab bar at bottom (≤ 5 tabs); back via top-left or edge-swipe.
- Touch targets ≥ 44×44pt; controls use system feel; supports Dynamic Type.
- Prefer bottom sheets and large titles; respect safe areas and notches.
- Use haptics for selection/impact; support Dark Mode and Increase Contrast.
- SF Symbols or a cohesive icon set; avoid arbitrary custom chrome.

## Android (Material 3)

- Navigation: top app bar, navigation bar (bottom, 3–5 items) or navigation rail/drawer for larger.
- Touch targets ≥ 48×48dp; 8dp grid; elevation via tonal surfaces (M3), not just shadows.
- Dynamic color (optional) with brand fallback; support predictive back and edge-to-edge.
- Ripple/state layers for feedback; FAB for the primary action where appropriate.

## macOS (Human Interface Guidelines)

- Window chrome: traffic lights top-left; toolbar with commands; menu bar provides all commands.
- Pointer precision: smaller controls OK (≥ ~24px), but keep forgiving hit areas.
- Native controls (segmented, sidebar, sheets) over web-style chrome when possible.
- Support light/dark, vibrancy/materials, retina, keyboard shortcuts (⌘), and Mac menus.

## Windows (Fluent / WinUI 3)

- Follow Fluent: acrylic/mica materials, subtle depth, rounded corners (8px), clear focus rectangles.
- Title bar integration; command bar / navigation view for app structure.
- Support theme (light/dark/**high contrast**), system accent color, and snap layouts.
- Keyboard + pointer first; controls ≥ 32–40px with generous hit areas. Respect High Contrast mode.

## Desktop apps generally (Tauri / Electron)

- Familiar window/title-bar behavior; native menus where possible.
- Keyboard shortcuts, right-click context menus, drag-and-drop, multi-window support.
- Never let web-only idioms (e.g. scroll trap, no focus) leak into a desktop app.
- Keep install/update surfaces minimal and native-feeling.

## Cross-platform strategy

- **Shared**: tokens, type, color roles, spacing, motion durations/easings, iconography, brand.
- **Adapted**: navigation patterns, control sizes, gestures, materials, key shortcuts.
- Decide early: one responsive codebase (RN/Flutter/Tauri) vs. native per platform. Match the choice
  to the product's fidelity and performance needs — do not force one approach everywhere.

## Density

Offer comfortable vs. compact density for data-heavy desktop/web tools (row heights, paddings
scale down ~20–30%). Keep touch targets intact on touch-capable devices regardless of density.
