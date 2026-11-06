# Design System Architecture

How to structure tokens, components, theming, and code so the UI stays coherent and scales.
This is the backbone of the skill — get it right and polished UI becomes the default.

## 1. Token layers (primitive → semantic → component)

Use a three-tier token model. Never reference primitives directly from components.

```
primitive  →  raw values, no meaning      (blue-500: #3B82F6, space-4: 16px)
semantic   →  roles, themed             (color-action: {light: blue-600, dark: blue-500})
component  →  per-component overrides   (button-bg: color-action, button-radius: radius-md)
```

**Rules**
- Components consume **semantic** (or component) tokens only.
- Theming (light/dark/brand) happens at the **semantic** layer.
- Changing a brand color must require editing primitives, never components.

Token categories: **color, space, radius, typography (family/size/weight/leading/tracking),
shadow/elevation, border, motion (duration/easing), opacity, z-index**.

## 2. Naming conventions

- kebab-case, category-prefixed: `color-bg-surface`, `space-4`, `radius-lg`, `text-body-md`,
  `shadow-md`, `duration-fast`, `ease-standard`.
- Use **roles** not appearances: `color-danger` (good) vs `color-red` (bad at semantic layer).
- Consistent scale suffixes: `-xs -sm -md -lg -xl` or numeric `-1..-9`. Pick one and stay.

## 3. Theming (light / dark / brand)

- Author both themes from day one; do not bolt dark mode on later.
- Implementation by stack:
  - **Web**: CSS custom properties on `:root` and `[data-theme="dark"]`; Tailwind maps them via
    `theme.extend.colors`. Optionally OKLCH for perceptual ramps.
  - **React Native**: a `ThemeProvider` context exposing tokens; support `useColorScheme`.
  - **Flutter**: `ThemeData` + `ColorScheme.fromSeed` (M3) with `ThemeExtension` for custom tokens.
  - **SwiftUI**: `Color`s in an Asset Catalog with light/dark variants + `Environment(\.colorScheme)`.
  - **Windows/WinUI**: `ResourceDictionary` with `ThemeDictionaries` (`Light`/`Dark`/`HighContrast`)
    following Fluent token names (`SystemControlBackgroundBaseLow`, custom brand overrides).
- Support **system / light / dark** preference and let users override.
- Also plan **high-contrast** / increased-contrast modes; never rely on subtle shadows there.

## 4. Component API conventions

- **Props over variants explosion.** Model state/variant/size via a small, orthogonal API:
  `variant`, `size`, `tone`, `disabled`, `loading`, `fullWidth`.
- Use **slots/composition** for extensibility (leading/trailing icons, children), not dozens of
  booleans.
- Forward refs, spread rest props, and merge `className`/style so consumers can extend.
- Keep variants **mapped to tokens** (a `variant` selects tokens, it does not hard-code colors).
- Provide sensible defaults so components are useful with zero props.
- Control vs. presentational: keep data-fetching out of pure UI components.
- Document each component with: purpose, props, states, a11y notes, and do/don't examples.

## 5. Layered folder architecture

```
design/
├── tokens/            # primitives + semantic tokens (source of truth)
│   ├── color.ts        (or colors.css / Color.xcassets / colors.dart)
│   ├── space.ts
│   ├── typography.ts
│   ├── radius.ts
│   ├── shadow.ts
│   └── motion.ts
├── theme/             # theme providers, light/dark mapping
└── primitives/        # Box, Stack, Text, Icon …

components/
├── ui/                # unstyled/utility primitives (Button, Input, Card, Dialog…)
├── patterns/          # composed blocks (SearchBar, DataTable, Navbar…)
└── <feature>/         # feature-specific components
```

- `ui/` = generic, reusable, token-driven, no business logic.
- `patterns/` = composed from `ui/`, still reusable.
- feature folders = product-specific, import from `ui/` and `patterns/`.
- One component = one folder (component + styles + tests + stories + index).

## 6. Recommended stacks per platform

| Platform | UI | Styling | Motion |
|----------|----|---------|--------|
| Web | React / Next.js | Tailwind CSS v4 + CSS variables | Motion (framer-motion) |
| Web (no framework) | HTML | CSS custom properties + minimal utility CSS | CSS transitions / Web Animations API |
| Mobile (cross) | React Native / Expo | tokens + StyleSheet / NativeWind | Reanimated + Gesture Handler |
| Mobile iOS | SwiftUI | Asset catalog + `ThemeData` | SwiftUI animations |
| Mobile Android | Jetpack Compose | Material 3 tokens | Compose animation APIs |
| Desktop (cross) | Tauri / Electron | same web stack | same web stack |
| Desktop macOS | SwiftUI | Asset catalog | SwiftUI animations |
| Desktop Windows | WinUI 3 / Fluent | ThemeDictionaries + Fluent tokens | WinUI animations |

Prefer **copy-in component kits over heavy UI dependencies** when you need full control of the
visual language (the shadcn / motion-primitives approach: you own the source).

## 7. Governance

- Tokens are the **single source of truth**; contracts for theme changes.
- Version components; deprecate rather than silently change.
- Every component needs a **storybook/preview** or live example in both themes.
- Add a lint rule / test that fails on hard-coded colors and spacing outside the token layer.
- Treat accessibility (contrast, focus, roles) as part of the component definition, with tests.

## 8. Anti-patterns to reject

- Raw hex/px values sprinkled in components.
- A `variant` for every visual possibility instead of orthogonal props.
- Dark mode as "invert the colors".
- One giant global stylesheet with no tokens.
- Copying a screenshot pixel-for-pixel without extracting the underlying system.
- Adding a component library whose look you then fight with overrides.
