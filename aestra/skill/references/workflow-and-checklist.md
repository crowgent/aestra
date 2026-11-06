# Workflow & Checklist

The end-to-end flow for building or redesigning UI, plus the final QA gate. Follow the CRAFT
method (Context → Rhythm → Architecture → Feel → Test).

---

## Part A — Greenfield (new website / app)

### Phase 1 — Context
1. State the product, audience, primary user task, and success metric in 2–3 lines.
2. Choose platform(s) and stack (see platform-guidelines.md / design-system.md §6).
3. Note constraints: brand assets, deadlines, existing system, localization, legal.
4. If unclear, ask **≤ 3** questions or state assumptions and proceed.

### Phase 2 — Rhythm (tokens)
5. Define color roles, type scale, spacing scale, radius, elevation, motion — light **and** dark.
6. Pick and document the typeface(s); set line-heights and tracking.
7. Write tokens in the chosen stack (CSS vars / TS tokens / ThemeData / Asset catalog / WinUI dict).

### Phase 3 — Architecture
8. Build primitives, then `ui/` components, then `patterns/`, then screens.
9. Keep a clean, orthogonal component API; map variants to tokens.
10. Create a live preview/story for each component in both themes.

### Phase 4 — Direction Lab (explore before committing)
11. Produce **2–3 distinct directions** for the key screen(s) — each a complete, buildable concept
    (vary layout, density, type scale, color temperature, motion feel). One-line rationale each.
12. Present side by side, converge on one, then build it out fully.

### Phase 5 — Feel
13. Add motion using the duration/easing tokens; design every interactive and data state.
14. Add micro-interactions: hover, press, focus, loading, toasts.

### Phase 6 — Test
15. Run the full QA checklist (Part C). Fix everything before declaring done.

---

## Part B — Redesign (existing UI)

1. **Audit (Context)** — inventory screens/components; screenshot the current state. List concrete
   defects: spacing chaos, weak hierarchy, low contrast, dated type, heavy/inconsistent motion,
   broken dark mode, tiny hit targets.
2. **Preserve intent** — keep IA, flows, and copy unless asked. Redesign ≠ re-architect the product.
3. **Baseline metrics** — note current contrast ratios, key sizes, and any system the app uses.
4. **Re-tokenize (Rhythm)** — map existing hard-coded values to the new token set. Most of the
   lift happens here; do this before restyling screens.
5. **Restyle incrementally (Architecture/Feel)** — apply the new system component by component.
   Keep diffs reviewable; show before/after per component.
6. **Verify parity** — every old state and edge case still works; then improve it.
7. **Accessibility uplift** — fix contrast, focus, labels, and hit targets as you go.
8. **Ship & monitor** — watch for regressions; keep the old screens reachable behind a flag if risky.

### Redesign rules
- Never break behavior for the sake of looks.
- Do not silently remove features.
- Keep performance equal or better.
- Change one dimension at a time when possible (tokens first, then layout, then motion).

---

## Part C — Final QA checklist

Tick every box before finishing.

**Foundation**
- [ ] No hard-coded colors/spacing/shadows outside the token layer.
- [ ] One consistent type scale, spacing scale, radius scale, shadow scale.
- [ ] Light **and** dark themes fully designed and tested.
- [ ] Brand primary, semantic (success/warning/danger/info), and neutrals defined as roles.

**Layout & responsive**
- [ ] Correct at 320px, 768px, 1024px, 1440px, 2560px (or mobile/tablet/large for apps).
- [ ] Safe areas / notches / window chrome respected.
- [ ] No horizontal scroll on mobile; no orphaned/misaligned elements.
- [ ] Content reflows sensibly, not just shrinks.

**States**
- [ ] Every interactive element: default, hover, focus-visible, active, disabled, loading.
- [ ] Every data surface: loading/skeleton, empty, error, success, partial/offline.
- [ ] Every input: default, filled, focused, invalid, disabled, helper/error.

**Accessibility**
- [ ] Text ≥ 4.5:1, large text ≥ 3:1, UI/borders ≥ 3:1.
- [ ] Visible focus indicator on all keyboard-reachable controls; logical tab order.
- [ ] Meaning never conveyed by color alone.
- [ ] Touch targets ≥ 44pt / 48dp; desktop controls have generous hit areas.
- [ ] Semantics/roles/labels correct; alt text present.
- [ ] Works with `prefers-reduced-motion`, dark mode, zoom/text-size, high contrast.

**Motion**
- [ ] UI transitions ≤ ~320ms; entrances decelerate, exits accelerate.
- [ ] Only `transform`/`opacity` animated in hot paths; 60fps on low-end devices.
- [ ] Reduced-motion fallback present (fade/instant).
- [ ] Motion never blocks input and is interruptible.
- [ ] No scroll-reveal, stagger, parallax, or looping motion unless it communicates real information.
- [ ] All essential content is visible immediately; no JavaScript/observer-dependent reveal.
- [ ] Hover and press feedback is restrained, fast, and consistent.

**Visual edit**
- [ ] Remove decorative dots, stars, arrows, separators, and section numbers unless meaningful.
- [ ] Remove redundant stats, badges, status labels, and self-referential AI/skill credits.
- [ ] Check the page at first glance: one clear headline, one concise explanation, one obvious action.

**Content**
- [ ] Sentence case, concise, consistent terminology.
- [ ] Buttons say what they do; errors explain the fix.
- [ ] Numbers/dates/currency localized.

**Cross-platform**
- [ ] Platform navigation/gesture conventions respected.
- [ ] Keyboard shortcuts, context menus, and system integrations present on desktop.
- [ ] Visual brand consistent across platforms.

**Ship**
- [ ] Live preview / story for components in both themes.
- [ ] Before/after shown (redesign) or direction rationale documented (greenfield).
- [ ] Performance equal or better than before.
