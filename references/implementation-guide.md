# Implementation Guide

Complete reference for stack-specific guidance, search syntax, example workflows, and professional UI rules. Use this file when implementing code or when you need platform-specific adaptations.

---

## Search Syntax Reference

### Domain Search

Use this pattern to retrieve design data:

```
Search [domain] for: [keywords]
Return top [N] results with all fields
```

**Available domains:**

| Domain | CSV File | Search Columns | Use For |
|--------|----------|---------------|---------|
| `style` | styles.csv | Style Category, Keywords, Best For, Type, AI Prompt Keywords | UI styles, effects, CSS keywords |
| `color` | colors.csv | Product Type, Notes | Color palettes by industry |
| `typography` | typography.csv | Font Pairing Name, Category, Mood, Best For, Heading Font, Body Font | Font pairings with Google Fonts URLs |
| `landing` | landing.csv | Pattern Name, Keywords, Conversion Optimization, Section Order | Page structure, CTA placement |
| `product` | products.csv | Product Type, Keywords, Primary Style, Key Considerations | Product type recommendations |
| `ux` | ux-guidelines.csv | Category, Issue, Description, Platform | Best practices, anti-patterns |
| `chart` | charts.csv | Data Type, Keywords, Best Chart Type, When to Use | Chart type recommendations |
| `google-fonts` | google-fonts.csv | Family, Category, Stroke, Classifications, Keywords | Individual Google Fonts lookup |
| `react` | react-performance.csv | Category, Issue, Keywords, Description | React/Next.js performance |
| `web` | app-interface.csv | Category, Issue, Keywords, Description | Mobile app interface guidelines |
| `icons` | icons.csv | Category, Icon Name, Keywords, Best For | Icon library recommendations |

### Stack Search

```
Search stack [stack-name] for: [keywords]
```

**Available stacks:**

| Stack | Focus |
|-------|-------|
| `react` | Components, hooks, performance |
| `nextjs` | App Router, RSC, caching, images |
| `vue` | Composition API, reactivity, performance |
| `svelte` | Runes, stores, transitions |
| `astro` | Islands, partial hydration, content |
| `swiftui` | Views, modifiers, navigation |
| `react-native` | Components, navigation, lists, safe areas |
| `flutter` | Widgets, state management, platform channels |
| `nuxtjs` | Pages, composables, server API |
| `nuxt-ui` | Components, theming, forms |
| `html-tailwind` | Utility classes, responsive, dark mode |
| `shadcn` | Component primitives, theming, Radix |
| `jetpack-compose` | Composables, state, Material You |
| `angular` | Components, services, RxJS |
| `laravel` | Blade, Livewire, Inertia.js |
| `threejs` | Scenes, materials, lighting, post-processing |

---

## Example Workflows

### Workflow A: New Landing Page

**User:** "Build a landing page for my fintech app"

**Step 1 — Analyze:**
- Product: Fintech / B2B SaaS
- Audience: Enterprise decision-makers
- Style: Trustworthy, clean, data-forward
- Stack: React + Tailwind (assume if not specified)

**Step 2 — Search design direction:**
```
Search product for: fintech saas b2b
Search style for: minimalism clean professional trustworthy
Search color for: fintech professional
Search typography for: professional modern clean
Search landing for: conversion hero testimonial
```

**Step 3 — Synthesize:**
- Pattern: Trust & Authority (Hero → Features → Social Proof → CTA)
- Style: Minimalism & Swiss Style
- Colors: Deep blue primary, white background, green accent for positive
- Typography: Inter heading + Inter body (clean, trustworthy)
- Key effects: Subtle hover transitions, smooth scroll

**Step 4 — Implement with rules:**
- Accessibility: contrast 4.5:1 minimum
- Touch: 44×44pt targets on mobile
- Layout: mobile-first, breakpoints 375/768/1024/1440
- Animation: 200ms transitions, transform/opacity only
- Forms: visible labels, inline validation

### Workflow B: New Dashboard

**User:** "Create an analytics dashboard"

**Step 1 — Analyze:**
- Product: Analytics / BI tool
- Audience: Data analysts, managers
- Style: Data-dense, professional, efficient
- Stack: React + shadcn/ui

**Step 2 — Search:**
```
Search product for: analytics dashboard bi
Search style for: data-dense minimal dashboard
Search color for: analytics professional
Search chart for: trend comparison real-time
```

**Step 3 — Synthesize:**
- Pattern: Data-Dense Dashboard
- Style: Minimalism (data-first)
- Colors: Slate/gray neutrals with single accent
- Charts: Line for trends, bar for comparisons, donut for proportions
- Typography: Monospace for numbers, sans-serif for labels

**Step 4 — Implement:**
- Charts: legends, tooltips, keyboard-navigable
- Layout: 12-column grid, card-based
- Performance: virtualize large tables, lazy load charts
- Accessibility: table alternatives for charts, color not sole indicator

### Workflow C: Dark Mode Implementation

**User:** "Add dark mode to my app"

**Step 1 — Analyze:**
- Existing: Light mode already built
- Need: Dark variant that maintains brand

**Step 2 — Search:**
```
Search style for: dark mode oled
Search color for: dark mode palette
Search ux for: dark mode contrast accessibility
```

**Step 3 — Rules to apply:**
- Design dark mode alongside light — don't just invert
- Use desaturated tonal variants (slate-900, not pure black)
- Test contrast independently: ≥4.5:1 for text
- Modal scrim: 40–60% black in both modes
- Respect `prefers-color-scheme` system preference
- Provide manual toggle

**Step 4 — Implementation:**
- Semantic tokens mapped per theme
- CSS variables or Tailwind `dark:` variants
- Test all components in both modes
- Verify focus states, disabled states, error states in both

### Workflow D: Mobile App UI

**User:** "Build a fitness tracking app UI"

**Step 1 — Analyze:**
- Product: Fitness / Health
- Platform: iOS + Android (React Native)
- Style: Energetic, motivating, clean

**Step 2 — Search:**
```
Search product for: fitness health tracking
Search style for: vibrant minimal energetic
Search color for: fitness energetic health
Search typography for: modern energetic clean
```

**Step 3 — Platform-specific rules:**
- Touch targets: 44×44pt (iOS), 48×48dp (Android)
- Safe areas: respect notch, Dynamic Island, gesture bar
- Navigation: bottom tab bar, max 5 items
- Typography: support Dynamic Type scaling
- Haptic feedback for workout milestones
- Dark mode: OLED-friendly deep blacks

**Step 4 — Implementation:**
- Use platform-native navigation patterns
- Charts: activity rings, bar charts for weekly progress
- Forms: workout logging with quick-add shortcuts
- Accessibility: VoiceOver/TalkBack labels on all controls

---

## Stack-Specific Guidelines

### React / Next.js

**Performance:**
- Route-level code splitting with `next/dynamic` or `React.lazy`
- Image optimization with `next/image`
- Font optimization with `next/font`
- `preconnect` to critical origins in `_document.tsx`

**Accessibility:**
- Radix primitives for keyboard/focus (shadcn/ui)
- `aria-*` props on custom components
- `prefers-reduced-motion` via CSS or Framer Motion

**Styling:**
- Tailwind CSS: utility-first, responsive variants
- CSS variables for theming
- `dark:` variants for dark mode

### Vue / Nuxt.js / Nuxt UI

**Performance:**
- Lazy load routes with `defineAsyncComponent`
- Nuxt Image for optimization
- Client-only components for heavy UI

**Styling:**
- Tailwind via `@nuxtjs/tailwindcss`
- Nuxt UI components with built-in theming
- Color mode module for dark mode

### Svelte / SvelteKit

**Performance:**
- Runes for fine-grained reactivity
- Lazy load with `import()` in `+page.svelte`
- `@sveltejs/enhanced-img` for images

**Styling:**
- Tailwind via `tailwindcss` Vite plugin
- Scoped styles in `<style>` blocks
- CSS variables for theming

### HTML + Tailwind

**Responsive:**
- Mobile-first: base styles for mobile, `sm:`, `md:`, `lg:`, `xl:` for larger
- Container queries for component-level responsiveness

**Dark Mode:**
- `darkMode: 'class'` in config + class toggle
- Or `darkMode: 'media'` for system preference only
- `dark:` prefix variants

**Accessibility:**
- Tailwind `focus:`, `focus-visible:` utilities
- `motion-reduce:` for reduced motion
- `sr-only:` for screen reader text

### React Native

**Layout:**
- `SafeAreaView` for notch/gesture bar
- `FlatList` for performant lists (virtualized)
- Flexbox layout (no CSS Grid)

**Styling:**
- StyleSheet for performance (not inline styles)
- Platform-specific styles with `Platform.OS`
- No CSS — use StyleSheet objects

**Navigation:**
- React Navigation: bottom tabs, stack, drawer
- Bottom tabs: max 5 items with labels
- Preserve state on back navigation

**Accessibility:**
- `accessibilityLabel`, `accessibilityHint`, `accessibilityRole`
- `accessible={true}` on grouped elements
- Test with VoiceOver (iOS) and TalkBack (Android)

### SwiftUI

**Layout:**
- `safeAreaPadding()` for safe areas
- `NavigationStack` for hierarchical navigation
- `TabView` for bottom tabs

**Styling:**
- `.font()` with Dynamic Type sizes
- `.foregroundStyle()` for semantic colors
- `.dynamicTypeSize()` for testing

**Accessibility:**
- `.accessibilityLabel()`, `.accessibilityHint()`
- `.accessibilityAddTraits()` for roles
- Support Dynamic Type automatically with `.font()`

### Flutter

**Layout:**
- `SafeArea` widget for system insets
- `ListView.builder` for virtualized lists
- `MediaQuery` for responsive sizing

**Styling:**
- `ThemeData` for global theming
- `MaterialColor` for color swatches
- `TextTheme` for typography scale

**Accessibility:**
- `Semantics` widget for labels/hints
- `excludeFromSemantics` for decorative
- `MediaQueryData.textScaleFactor` for scaling

### Jetpack Compose

**Layout:**
- `systemBarsPadding()` modifier
- `LazyColumn` / `LazyRow` for virtualized lists
- `Scaffold` for standard app structure

**Styling:**
- `MaterialTheme` for colors, typography, shapes
- `ColorScheme` for light/dark variants
- Custom shapes with `RoundedCornerShape`

**Accessibility:**
- `contentDescription` for semantics
- `semantics` modifier for custom roles
- `LocalTextStyle` for scaling

---

## Professional UI Rules

These rules prevent the most common "unprofessional UI" issues:

### Icons & Visual Elements

| Rule | Do | Don't | Why |
|------|----|-------|-----|
| No emoji icons | Use SVG vector icons (Lucide, Heroicons) | Use 🎨 🚀 ⚙️ for nav/controls | Emojis are font-dependent, inconsistent, unthemeable |
| Vector-only | SVG or platform vector icons | Raster PNGs that blur | Scales cleanly, supports theming |
| Stable press states | Color/opacity/elevation transitions | Layout-shifting transforms | Prevents jitter, preserves perceived quality |
| Correct brand logos | Official assets with clear space | Guessing paths, recoloring unofficially | Legal compliance, brand integrity |
| Consistent sizing | Design tokens: icon-sm=24pt, icon-md=32pt | Mixing 20/24/28pt randomly | Maintains rhythm and hierarchy |
| Stroke consistency | One stroke width per layer | Mixing thick/thin arbitrarily | Reduces perceived polish |
| Filled vs outline | One style per hierarchy level | Mixing at same level | Maintains semantic clarity |
| Touch targets | ≥44×44pt with hitSlop if needed | Small icons without expanded area | Meets accessibility standards |
| Icon alignment | Aligned to text baseline | Misaligned or inconsistent padding | Prevents visual imbalance |
| Icon contrast | WCAG 4.5:1 for small, 3:1 for large | Low-contrast blending into background | Ensures accessibility |

### Interaction (App / Mobile)

| Rule | Do | Don't |
|------|----|-------|
| Tap feedback | Clear pressed feedback within 80–150ms | No visual response |
| Animation timing | 150–300ms micro-interactions | Instant or >500ms |
| Accessibility focus | Focus order matches visual, labels descriptive | Unlabeled controls |
| Disabled state | Semantically disabled, reduced opacity, no tap | Looks tappable but does nothing |
| Touch target | ≥44×44pt (iOS), ≥48×48dp (Android) | Tiny targets without padding |
| Gesture conflicts | One primary gesture per region | Overlapping tap/drag conflicts |
| Native controls | Use Button, Pressable with accessibility roles | Generic containers as controls |

### Light/Dark Mode

| Rule | Do | Don't |
|------|----|-------|
| Surface readability | Cards clearly separated from background | Overly transparent surfaces |
| Text contrast (light) | Body ≥4.5:1 on light surfaces | Low-contrast gray body text |
| Text contrast (dark) | Primary ≥4.5:1, secondary ≥3:1 on dark | Text blending into background |
| Border visibility | Separators visible in both themes | Theme-specific borders disappearing |
| State parity | Pressed/focused/disabled equally distinguishable | States defined for one theme only |
| Token theming | Semantic tokens mapped per theme | Hardcoded per-screen hex values |
| Scrim legibility | Modal scrim 40–60% black | Weak scrim competing with background |

### Layout & Spacing

| Rule | Do | Don't |
|------|----|-------|
| Safe areas | Respect top/bottom for fixed headers/tabs | UI under notch or gesture bar |
| System bar clearance | Spacing for status/nav bars | Tappable content colliding with OS chrome |
| Content width | Predictable width per device class | Arbitrary widths between screens |
| Spacing rhythm | 4/8dp system for padding/gaps | Random increments |
| Text measure | Readable on large devices | Edge-to-edge paragraphs on tablets |
| Section hierarchy | Clear vertical rhythm tiers | Similar levels with inconsistent spacing |
| Adaptive gutters | Increase insets on larger widths | Same narrow gutter everywhere |
| Scroll coexistence | Content insets for fixed bars | Scroll hidden behind sticky elements |

---

## Troubleshooting Common Issues

| Problem | Likely Cause | Solution |
|---------|-----------|----------|
| UI looks "off" but can't tell why | Inconsistent spacing, mixed icon styles, or missing hover states | Audit with Pre-Delivery Checklist |
| Layout shifts on load | Images without dimensions, fonts without display:swap | Add width/height, font-display:swap, skeleton screens |
| Mobile feels cramped | Fixed px widths, no mobile-first approach | Switch to mobile-first, use relative units |
| Animations feel janky | Animating width/height, no transform/opacity | Refactor to transform + opacity only |
| Forms confuse users | Placeholder-only labels, errors at top | Add visible labels, inline validation, error per field |
| Navigation feels lost | Overloaded nav, no state preservation | Limit bottom nav to 5, highlight current, preserve state |
| Charts are unreadable | Too many categories, no legend, color-only meaning | Simplify data, add legend, supplement color with text |
| Dark mode looks wrong | Inverted colors instead of tonal variants | Use desaturated variants, test contrast independently |
| Touch targets missed | Icons at natural size without padding | Expand hit area to 44×44pt minimum |
| Screen reader issues | Missing labels, wrong focus order | Add aria-label/accessibilityLabel, verify tab order |
