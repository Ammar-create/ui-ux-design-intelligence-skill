---
name: ui-ux-design-intelligence
description: "AI-powered UI/UX design intelligence for web, mobile, and desktop applications. Use this skill whenever the user requests UI design, frontend styling, component creation, color palette selection, typography pairing, layout decisions, accessibility improvements, animation guidance, responsive design, dark mode implementation, form UX, navigation patterns, chart/data visualization design, or reviewing/fixing UI code quality. Covers 67+ UI styles, 161 color palettes, 57 font pairings, 161 product types, 99 UX guidelines, and 25 chart types across 15+ tech stacks (React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui, HTML/CSS, Angular, Laravel, Astro, Three.js). Triggers on: build/design/create/implement a page, component, dashboard, landing page, mobile app, form, modal, button, card, table, chart, navbar, sidebar, color scheme, typography system, spacing system, layout grid, animation, interaction states, hover/focus states, responsive breakpoints, accessibility review, dark mode, design system, style guide, or any request about how something should look, feel, move, or be interacted with."
---

# UI/UX Design Intelligence

Comprehensive design intelligence for building professional, accessible, and beautiful interfaces across web and mobile.

## When to Apply

**Must Use:**
- Designing new pages (landing page, dashboard, admin panel, SaaS, mobile app, e-commerce)
- Creating or refactoring UI components (buttons, modals, forms, tables, charts, cards, navbars, sidebars)
- Choosing color schemes, typography systems, spacing standards, or layout grids
- Reviewing UI code for UX, accessibility, or visual consistency
- Implementing navigation, animations, responsive behavior, dark mode, or interaction states
- Making product-level design decisions (style, hierarchy, brand expression)
- Improving perceived quality, clarity, or usability

**Skip:**
- Pure backend logic, API/database design only
- Infrastructure/DevOps, non-visual scripts

---

## Design Workflow

Follow this 4-step workflow for every UI/UX task:

### Step 1: Analyze Requirements

Extract from the user's request:
- **Product type:** SaaS, e-commerce, healthcare, fintech, portfolio, social, gaming, etc.
- **Target audience:** Consumer, enterprise, age group, usage context
- **Style keywords:** minimal, vibrant, dark mode, playful, premium, content-first
- **Tech stack:** React, Next.js, Vue, Svelte, Tailwind, SwiftUI, React Native, Flutter, etc.
- **Screen types:** Desktop primary, mobile-first, tablet, multi-platform

### Step 2: Generate Design Direction

Run domain searches to build a complete design direction:

1. **Product match** — identify the industry pattern
2. **Style selection** — match visual style to product personality
3. **Color palette** — choose industry-appropriate colors
4. **Typography pairing** — match font personality to mood
5. **Landing structure** — determine page section flow and CTA strategy

Use this prompt pattern to retrieve data:

```
Search for design recommendations matching: [product] + [industry] + [tone keywords]
Domains: product, style, color, typography, landing
Return: top matches with reasoning for each choice
```

### Step 3: Apply Priority Rules

Use the priority table below to determine which rule category deserves the most attention:

| Priority | Category | Impact | Domains | Key Checks (Must Have) | Anti-Patterns (Avoid) |
|----------|----------|--------|---------|------------------------|------------------------|
| 1 | Accessibility | CRITICAL | `ux` | Contrast 4.5:1, Alt text, Keyboard nav, ARIA labels | Removing focus rings, icon-only buttons without labels |
| 2 | Touch & Interaction | CRITICAL | `ux` | Min 44×44pt target, 8px spacing, Loading feedback | Reliance on hover only, instant 0ms state changes |
| 3 | Performance | HIGH | `ux` | WebP/AVIF, lazy loading, reserve space (CLS < 0.1) | Layout thrashing, cumulative layout shift |
| 4 | Style Selection | HIGH | `style`, `product` | Match product type, consistency, SVG icons | Mixing flat & skeuomorphic randomly, emoji as icons |
| 5 | Layout & Responsive | HIGH | `ux` | Mobile-first breakpoints, viewport meta, no horizontal scroll | Fixed px widths, disabling zoom |
| 6 | Typography & Color | MEDIUM | `typography`, `color` | Base 16px, line-height 1.5, semantic tokens | Text < 12px body, gray-on-gray, raw hex in components |
| 7 | Animation | MEDIUM | `ux` | Duration 150–300ms, motion conveys meaning | Decorative-only animation, animating width/height |
| 8 | Forms & Feedback | MEDIUM | `ux` | Visible labels, error near field, progressive disclosure | Placeholder-only labels, errors only at top |
| 9 | Navigation | HIGH | `ux` | Predictable back, bottom nav ≤5, deep linking | Overloaded nav, broken back behavior |
| 10 | Charts & Data | LOW | `chart` | Legends, tooltips, accessible colors | Color-only meaning, no screen reader fallback |

**Rule:** Always satisfy higher-priority categories before refining lower-priority ones.

### Step 4: Implement & Validate

Before delivering any UI code, run through the Pre-Delivery Checklist.

---

## Quick Rule Index

Read `references/rules-database.md` for the full rule database with all 10 categories. Below are the most frequently applied rules:

### Accessibility (Critical — Always)
- Contrast: minimum 4.5:1 normal text, 3:1 large text
- Focus rings: visible on all interactive elements (2–4px)
- Alt text: descriptive for meaningful images
- `aria-label` for icon-only buttons
- Keyboard nav: tab order matches visual order
- `prefers-reduced-motion`: respected
- Color is never the sole indicator — add icon or text
- Support system text scaling; avoid truncation as text grows

### Touch & Interaction (Critical — Always)
- Touch target minimum: 44×44pt (iOS) / 48×48dp (Android/Material)
- Gap between targets: minimum 8px
- Don't rely on hover for primary interactions
- Disable button + show spinner during async operations
- `cursor-pointer` on all clickable web elements
- Visual feedback on press within 80–150ms
- Haptic feedback for confirmations (mobile)

### Performance (High)
- Images: WebP/AVIF, responsive `srcset`, lazy loading
- Declare `width/height` or `aspect-ratio` to prevent CLS
- `font-display: swap` to avoid FOIT
- Lazy load non-hero components
- Virtualize lists with 50+ items
- Debounce/throttle scroll, resize, input events

### Style Selection (High)
- Match style to product type and audience
- Use the SAME style across all pages
- **NEVER use emojis as icons** — use SVG (Heroicons, Lucide)
- Shadows, blur, radius aligned with chosen style
- Respect platform idioms (iOS HIG vs Material Design)
- One primary CTA per screen

### Layout & Responsive (High)
- Viewport meta: `width=device-width, initial-scale=1`
- Mobile-first: design for 375px, then scale up
- Breakpoints: systematic (e.g., 375 / 768 / 1024 / 1440)
- Body text minimum 16px on mobile (prevents iOS auto-zoom)
- Line length: mobile 35–60 chars; desktop 60–75 chars
- No horizontal scroll on mobile
- Use 4pt/8pt spacing system consistently
- `min-h-dvh` instead of `100vh` on mobile

### Typography & Color (Medium)
- Line-height: 1.5–1.75 for body text
- Consistent type scale (e.g., 12 14 16 18 24 32)
- Use semantic color tokens, not raw hex in components
- Dark mode: desaturated tonal variants, not inverted colors
- Tabular/monospaced figures for data columns

### Animation (Medium)
- Duration: 150–300ms for micro-interactions; ≤400ms for complex
- Use `transform` and `opacity` only; **never animate width/height/top/left**
- Skeleton screens for loading >300ms
- Ease-out for entering, ease-in for exiting
- Every animation must express cause-effect, not just decorate
- Exit animations shorter than enter (~60–70%)
- Stagger list entrances by 30–50ms per item
- Animations must be interruptible; never block input

### Forms & Feedback (Medium)
- Visible label per input (not placeholder-only)
- Error message directly below the related field
- Inline validation on blur, not keystroke
- Semantic input types (`email`, `tel`, `number`) for correct mobile keyboards
- Show/hide toggle for password fields
- Multi-step flows: show progress indicator + allow back
- Auto-save drafts for long forms
- Error messages must state cause + how to fix

### Navigation (High)
- Bottom navigation: maximum 5 items, labels with icons
- Back navigation: predictable, preserves scroll/state
- All key screens reachable via deep link/URL
- Current location visually highlighted in nav
- Support system gestures (iOS swipe-back, Android predictive back)
- Core navigation reachable from deep pages
- Don't mix Tab + Sidebar + Bottom Nav at same hierarchy level

### Charts & Data (Low)
- Match chart type to data: trend→line, comparison→bar, proportion→pie
- Always show legend near the chart
- Provide table alternative for accessibility
- Supplement color with patterns/textures for colorblind users
- Label axes with units and readable scale
- Reflow/simplify charts on small screens

---

## Pre-Delivery Checklist

### Visual Quality
- [ ] No emojis as icons (use SVG: Heroicons / Lucide / Phosphor)
- [ ] All icons from consistent family (stroke width, style unified)
- [ ] Pressed states don't shift layout bounds
- [ ] Semantic theme tokens used (no ad-hoc hardcoded colors)

### Interaction
- [ ] All tappable elements have pressed feedback
- [ ] Touch targets ≥44×44pt (iOS) or ≥48×48dp (Android)
- [ ] Micro-interaction timing 150–300ms with native easing
- [ ] Disabled states are visually clear and non-interactive
- [ ] Screen reader focus order matches visual order
- [ ] Gestures avoid nested/conflicting interactions

### Light/Dark Mode
- [ ] Primary text contrast ≥4.5:1 in both themes
- [ ] Secondary text contrast ≥3:1 in both themes
- [ ] Dividers and interaction states distinguishable in both modes
- [ ] Modal scrim opacity 40–60% black
- [ ] Both themes tested before delivery

### Layout
- [ ] Safe areas respected for headers, tab bars, bottom CTAs
- [ ] Scroll content not hidden behind fixed/sticky bars
- [ ] Verified on small phone, large phone, tablet (portrait + landscape)
- [ ] 4/8pt spacing rhythm maintained globally
- [ ] Long-form text measure readable on larger devices

### Accessibility
- [ ] All meaningful images/icons have accessibility labels
- [ ] Form fields have labels, hints, and clear error messages
- [ ] Color is not the only indicator
- [ ] `prefers-reduced-motion` and dynamic text size supported
- [ ] Accessibility traits/roles/states announced correctly

---

## Reference Files

This skill bundles three reference files. Load the relevant one based on the task:

| File | When to Read |
|------|-------------|
| `references/rules-database.md` | Need detailed rules for any of the 10 categories, or when doing a full UX review |
| `references/implementation-guide.md` | Need stack-specific guidance, search syntax, example workflows, or professional UI rules |

---

## Stack Adapters

Adapt rules to the target stack. Key differences:

**React / Next.js / Vue / Svelte:**
- Use Tailwind tokens for spacing/colors
- `font-display: swap` in `_document.tsx` or `app/layout`
- Route-level code splitting with dynamic imports
- Preconnect to font/CDN origins

**Mobile (React Native / Flutter / SwiftUI / Jetpack Compose):**
- Touch targets: 44×44pt (iOS) / 48×48dp (Android)
- Safe areas via `SafeAreaView` / `.safeAreaPadding()` / `systemBarsPadding()`
- Dynamic Type / accessibility scaling support
- Platform gesture navigation (swipe-back, predictive back)
- Haptic feedback for confirmations

**HTML + Tailwind:**
- Responsive via Tailwind breakpoints (`sm:`, `md:`, `lg:`, `xl:`)
- Prefers-reduced-motion: `motion-reduce:` variants
- Dark mode: `dark:` variants or `class` strategy

**shadcn/ui:**
- Use built-in component tokens for theme consistency
- Override via CSS variables in `globals.css`
- Radix primitives provide keyboard/focus/accessibility
