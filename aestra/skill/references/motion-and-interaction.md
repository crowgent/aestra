# Motion & Interaction

Motion is part of the design system, not a finishing trick. Use it to show **where things came
from, what changed, and what is now possible**. If an animation does not clarify one of those, cut it.
The default is **no motion** until a real interaction benefits from feedback.

## 0. Motion taste: quiet by default

- Do not add scroll-reveal, staggered entrance, parallax, floating, cursor-follow, or looping
  animations to a portfolio, marketing page, or product screen just to make it feel polished.
- Content is visible immediately. Never make essential content depend on JavaScript or an observer.
- Prefer a small color/border change on hover and a 1px press response on activation.
- Animate only the property that communicates the change; avoid choreographed page entrances.
- A static page with excellent typography, spacing, and contrast is more polished than a page with
  unnecessary motion.
- Ask: “What information does this motion communicate?” If the answer is “it looks cool,” remove it.

## 1. Motion tokens (define these once)

```
duration-instant  80ms    # micro feedback (hover color, press)
duration-fast     150ms   # small UI transitions (tooltips, toggles, fades)
duration-normal   220ms   # default (dropdowns, modals, route bits)
duration-slow     320ms   # large surfaces, page/section transitions
duration-slower   500ms   # rare, deliberate (onboarding, hero reveals)

ease-standard     cubic-bezier(0.2, 0, 0, 1)     # most UI
ease-decelerate   cubic-bezier(0.0, 0, 0.2, 1)   # entrances
ease-accelerate   cubic-bezier(0.4, 0, 1, 1)     # exits
ease-spring       { stiffness: 300, damping: 30 }# playful, physical
```

Rules: entrances use decelerate, exits use accelerate. Keep UI transitions ≤ 320ms. Bigger distance
= slightly longer duration, not a different curve.

## 2. When to animate (and what)

| Interaction | Motion | Token |
|-------------|--------|-------|
| Hover / focus | color/opacity change | `instant`–`fast` |
| Press | translateY(1px) or subtle color shift | `instant` |
| Toggle / switch | knob slide + track color | `fast` |
| Tooltip / popover | fade + 4–8px rise, origin-aware | `fast`–`normal` |
| Dropdown / menu | fade + scale from trigger (0.96→1) | `normal` |
| Modal / dialog | backdrop fade + panel scale/rise | `normal` |
| Drawer / sheet | slide from edge | `normal`–`slow` |
| Page / route | shared-element or subtle crossfade | `normal`–`slow` |
| List / grid enter | Usually none; stagger only when items genuinely arrive dynamically | `normal` |
| Accordion | height + content fade | `normal` |
| Toast | slide + fade, auto-dismiss | `fast` |

## 3. Gestures (mobile & touch)

- **Drag-to-dismiss** sheets/rows with velocity thresholds, not just distance.
- **Swipe actions** reveal with resistance past the threshold, then snap.
- Provide **haptics** for confirm/impact/selection where the platform allows.
- Keep gestures **reversible/bidirectional** and never the only way to do something.
- Follow platform expectations: iOS edge-swipe back, Android predictive back.

## 4. Layout animation

- Animate **layout changes** (list reorder, expand/collapse, shared elements) so the user keeps
  spatial context.
- Prefer transforming **`transform` and `opacity`** only — never animate `width/height/top/left`
  in hot paths (causes layout thrash). Use FLIP / layout-animation primitives.
- Animate `box-shadow`, `filter`, `background-color` cautiously and only on small surfaces.

## 5. Health rules

- **Interruptible**: motion must yield instantly to new input.
- **Fast**: if the user notices the delay, it is too slow.
- **Purposeful**: no ambient/looping animation in working areas.
- **Sparse**: a screen should not animate every element on load or scroll.
- **Consistent**: same trigger → same motion, everywhere.
- **Origin-aware**: overlays animate from their trigger, not the screen center.

## 6. Reduced motion (mandatory)

- Honor `prefers-reduced-motion: reduce` on web; `AccessibilityInfo.isReduceMotionEnabled` on RN;
  platform settings on iOS/Android/Windows/macOS.
- Remove non-essential motion; use an instant state change or simple opacity fade (≤ 100ms) only
  where a transition is needed to understand the state change.
- Never remove the ability to perceive state change — keep a minimal fade.

## 7. Performance budget

- Target 60fps; animations must stay off the main thread where possible (compositor-only props).
- Avoid animating during data loading; keep skeletons static or gently pulsing (not flashing).
- Lazy-mount heavy animated subtrees; unmount on exit before the next commit.
- Test on low-end devices and with "reduce motion" on.

## 8. Accessibility

- Motion must never be the only signal of state (pair with color/icon/text).
- Respect reduced-motion (above) and avoid flashes > 3 per second (seizure risk).
- Ensure animated content reaches its final visual state even if animation fails.

## 9. Implementation notes

- **Web**: Motion (framer-motion) for layout/gesture/variants; CSS transitions for simple states;
  Web Animations API for imperative cases. Use `LazyMotion`/tree-shaking to keep bundles small.
- **React Native**: Reanimated (worklets) + Gesture Handler for 60fps gestures.
- **Flutter**: implicit animations first (`AnimatedContainer`, `AnimatedSwitcher`),
  `Hero` for shared elements, `AnimationController` for choreography.
- **SwiftUI**: `.animation`, `withAnimation`, `matchedGeometryEffect`, `.transition`.
- **WinUI**: `ThemeTransition`/implicit animations; respect system animation settings.
- Build a small **motion component kit** in your own system (fade-in, stagger, morph, sheet, toast)
  so teams reuse it instead of hand-rolling animations per screen.
