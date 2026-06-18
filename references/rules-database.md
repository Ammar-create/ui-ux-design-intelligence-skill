# Rules Database

Complete reference for all 10 UI/UX rule categories. Use this file when you need deep detail on any category, or when conducting a full UX review.

---

## Category 1: Accessibility (CRITICAL)

### Contrast
- **Minimum 4.5:1** ratio for normal text (WCAG AA)
- **3:1** for large text (18pt+ or 14pt bold)
- Use tools to verify; don't eyeball it
- Test both light and dark modes independently

### Focus States
- Visible focus rings on ALL interactive elements
- Ring width: 2–4px
- Color must contrast with background
- Never remove focus rings with `outline: none` without replacement

### Alt Text
- Descriptive alt text for meaningful images
- Decorative images: `alt=""` or `role="presentation"`
- Charts need text summary in addition to visual

### ARIA Labels
- `aria-label` for icon-only buttons
- `aria-expanded` for dropdowns/accordions
- `aria-live="polite"` for toast announcements
- `role="alert"` for form errors

### Keyboard Navigation
- Tab order matches visual order
- Full keyboard support for all interactive elements
- Skip links for keyboard users
- Logical heading hierarchy (h1→h6, no skips)

### Screen Readers
- Meaningful `accessibilityLabel` / `accessibilityHint` (mobile)
- Logical reading order for VoiceOver / TalkBack
- Form errors announced via `aria-live`

### Text Scaling
- Support system text scaling (iOS Dynamic Type, Android font scaling)
- Avoid truncation as text grows — allow wrapping
- Test at largest text size before delivery

### Reduced Motion
- Respect `prefers-reduced-motion`
- Reduce or disable animations when requested
- Provide instant state changes as fallback

### Color-Independent Meaning
- Never convey information by color alone
- Add icons, text labels, or patterns alongside color
- Error states: red + icon + text
- Success states: green + icon + text

---

## Category 2: Touch & Interaction (CRITICAL)

### Touch Target Size
- **iOS:** minimum 44×44pt
- **Android/Material:** minimum 48×48dp
- Extend hit area beyond visual bounds if icon is smaller
- Use `hitSlop` (React Native) or padding to expand

### Touch Spacing
- Minimum 8px/8dp gap between touch targets
- Prevents accidental taps on adjacent elements

### Hover vs Tap
- Web: use `cursor-pointer` on all clickable elements
- Don't rely on hover for primary interactions
- Mobile: hover doesn't exist — design for tap/press

### Loading Feedback
- Disable button during async operations
- Show spinner or progress indicator
- Skeleton screens for content loading >300ms
- Never leave user guessing if action registered

### Error Feedback
- Clear error messages near the problem field
- Recovery path included (retry, edit, help link)
- Timeout errors: show clear feedback with retry option

### Gesture Guidelines
- Use platform standard gestures consistently
- Don't redefine swipe-back, pinch-zoom, etc.
- Don't block system gestures (Control Center, back swipe)
- Provide visible controls as alternative to gestures
- Use movement threshold before starting drag

### Press Feedback
- Visual feedback within 80–150ms of tap
- Ripple (Material), opacity change, or scale feedback
- Haptic for confirmations and important actions (mobile)
- Restore state on release

---

## Category 3: Performance (HIGH)

### Image Optimization
- Use WebP/AVIF formats
- Responsive images with `srcset` and `sizes`
- Lazy load non-critical images: `loading="lazy"`
- Declare `width/height` or `aspect-ratio` to prevent CLS

### Font Loading
- `font-display: swap` or `optional` to avoid FOIT
- Preload only critical fonts
- Reserve space to reduce layout shift

### Code Splitting
- Route-level splitting (React Suspense, Next.js dynamic)
- Lazy load non-hero components
- Keep initial bundle minimal

### Third-Party Scripts
- Load async/defer
- Audit and remove unnecessary scripts
- Use `preconnect` for critical origins

### Layout Stability
- Reserve space for async content (CLS < 0.1)
- Batch DOM reads then writes
- Avoid frequent layout reads/writes (layout thrashing)
- Use skeleton screens instead of content jumping

### List Performance
- Virtualize lists with 50+ items
- Keep per-frame work under ~16ms for 60fps
- Move heavy tasks off main thread

### Input Responsiveness
- Keep input latency under ~100ms
- Visual feedback within 100ms of tap
- Debounce/throttle high-frequency events (scroll, resize, input)

### Progressive Loading
- Skeleton screens for >1s operations
- Degraded modes for slow networks (lower-res images, fewer animations)
- Offline state messaging and fallback

---

## Category 4: Style Selection (HIGH)

### Style Matching
- Match visual style to product type and audience
- SaaS → Minimalism, Clean, Professional
- Gaming → Cyberpunk, Vibrant, 3D
- Wellness → Soft UI, Organic, Calming
- Fintech → Trustworthy, Clean, Data-dense
- Creative → Brutalism, Memphis, Bold

### Consistency
- Use the SAME style across all pages/screens
- One icon family throughout (stroke width, corner radius unified)
- One elevation/shadow scale for cards, modals, sheets
- Filled vs outline: one style per hierarchy level

### Icons
- **NEVER use emojis as structural icons**
- Use SVG vector icons (Heroicons, Lucide, Phosphor, Feather)
- Scale cleanly and support theming
- Raster PNGs blur/pixelate — avoid

### Effects Alignment
- Shadows, blur, radius aligned with chosen style:
  - Glassmorphism → backdrop blur, semi-transparent
  - Neumorphism → soft shadows, subtle depth
  - Brutalism → hard shadows, bold borders, no radius
  - Minimalism → no shadows, flat, generous whitespace

### Platform Adaptation
- iOS: bottom tab bar, swipe-back, spring animations, HIG
- Android: top app bar, Material Design, ripple feedback
- Web: responsive, hover states, focus rings
- Respect platform idioms for navigation, controls, typography, motion

### State Clarity
- Hover/pressed/disabled states visually distinct
- Use Material state layers or equivalent
- Disabled: reduced opacity (0.38–0.5) + cursor change

### Elevation System
- Consistent shadow scale:
  - `--shadow-sm`: 0 1px 2px rgba(0,0,0,0.05)
  - `--shadow-md`: 0 4px 6px rgba(0,0,0,0.1)
  - `--shadow-lg`: 0 10px 15px rgba(0,0,0,0.1)
  - `--shadow-xl`: 0 20px 25px rgba(0,0,0,0.15)

### Dark Mode Pairing
- Design light and dark variants together
- Dark mode: desaturated/lighter tonal variants, NOT inverted colors
- Test contrast independently per theme
- Modal scrim: 40–60% black in both modes

---

## Category 5: Layout & Responsive (HIGH)

### Viewport
- `<meta name="viewport" content="width=device-width, initial-scale=1">`
- Never disable user zoom
- Use `min-h-dvh` instead of `100vh` on mobile

### Mobile-First
- Design for 375px first
- Then scale up: tablet (768px), desktop (1024px), large (1440px)
- Content priority: show core content first on mobile

### Breakpoints
- Use systematic breakpoints consistently
- Example: 375 / 768 / 1024 / 1440
- Same breakpoints across the entire product

### Typography Measure
- Mobile: 35–60 characters per line
- Desktop: 60–75 characters per line
- Edge-to-edge paragraphs hurt readability on large screens

### Spacing System
- 4pt/8pt incremental system
- Define tiers: 16 / 24 / 32 / 48 / 64
- Use whitespace intentionally to group and separate

### Touch Density
- Comfortable spacing for touch — not cramped
- Not so spread that it causes mis-taps
- Component padding accounts for touch targets

### Container Width
- Consistent max-width on desktop: `max-w-6xl` or `max-w-7xl`
- Increase horizontal insets on larger widths
- Adaptive gutters by breakpoint

### Z-Index Management
- Define layered scale: 0 / 10 / 20 / 40 / 100 / 1000
- Don't use arbitrary values like `z-[99999]`

### Fixed Elements
- Fixed navbar/bottom bar must reserve safe padding
- Scroll content not hidden behind fixed bars
- Content insets for lists behind sticky headers

### Scroll Behavior
- Avoid nested scroll regions interfering with main scroll
- Horizontal scroll only for carousels — never for main content
- `scroll-behavior: smooth` for anchor links

### Orientation
- Layout readable and operable in landscape
- Test both portrait and landscape
- Don't force orientation unless absolutely necessary

### Visual Hierarchy
- Establish via size, spacing, contrast — not color alone
- Primary action most prominent per screen
- Secondary actions visually subordinate

---

## Category 6: Typography & Color (MEDIUM)

### Typography Scale
- Consistent type scale across product
- Example: 12 / 14 / 16 / 18 / 24 / 32 / 48
- Use platform type systems:
  - iOS: Dynamic Type styles (largeTitle, title1, body, caption)
  - Material: type roles (display, headline, title, body, label)

### Line Height
- Body text: 1.5–1.75
- Headings: 1.2–1.3
- Tight tracking on body text is hard to read

### Font Weight Hierarchy
- Bold headings: 600–700
- Regular body: 400
- Medium labels: 500
- Use weight to reinforce hierarchy, not just size

### Font Pairing
- Match heading and body font personalities
- One pairing per product; don't mix arbitrarily
- Sans-serif headings + serif body = editorial
- Sans-serif headings + sans-serif body = modern/clean

### Color Tokens
- Define semantic tokens, not raw hex in components:
  - `--color-primary`, `--color-secondary`, `--color-error`
  - `--color-surface`, `--color-on-surface`
  - `--color-muted`, `--color-border`, `--color-ring`
- Map tokens per theme (light/dark)

### Accessible Color Pairs
- Foreground/background: ≥4.5:1 for AA, ≥7:1 for AAA
- Use tools to verify; don't guess
- Functional colors (error red, success green) need icon/text backup

### Dark Mode Colors
- Desaturated tonal variants, not inverted
- `slate-900` background with `slate-100` text, not pure black/white
- Test independently from light mode

### Truncation
- Prefer wrapping over truncation
- When truncating: ellipsis + tooltip/expand for full text
- Tabular/monospaced figures for data columns to prevent layout shift

### Whitespace
- Use intentionally to group related items
- Separate sections clearly
- Avoid visual clutter

---

## Category 7: Animation (MEDIUM)

### Duration Guidelines
- Micro-interactions: 150–300ms
- Complex transitions: ≤400ms
- Never >500ms for UI feedback
- Exit animations: ~60–70% of enter duration

### Performance-First
- Use `transform` and `opacity` ONLY
- **Never animate width/height/top/left** — causes layout reflow
- Use `will-change` sparingly, only on elements about to animate

### Easing
- Enter: `ease-out` (decelerate)
- Exit: `ease-in` (accelerate)
- Avoid `linear` for UI transitions
- Spring/physics-based curves for natural feel (iOS)

### Meaningful Motion
- Every animation must express cause-effect
- Not decorative — conveys spatial relationships
- Direction indicates hierarchy: from below = deeper, upward = back

### State Transitions
- Hover / active / expanded / collapsed / modal: animate smoothly
- No instant snaps
- Crossfade for content replacement in same container

### Continuity
- Page transitions maintain spatial continuity
- Shared element / hero transitions between screens
- Navigation direction consistent: forward = left/up, back = right/down

### Reduced Motion
- Respect `prefers-reduced-motion`
- Provide instant state changes as fallback
- Parallax: use sparingly, respect reduced motion

### Stagger
- List/grid item entrance: 30–50ms per item
- Avoid all-at-once or too-slow reveals

### Interruptibility
- Animations must be interruptible
- User tap/gesture cancels in-progress animation immediately
- Never block user input during animation

### Modal Motion
- Modals/sheets animate from trigger source
- Scale + fade or slide-in for spatial context
- Backdrop blur to indicate background dismissal

### Scale Feedback
- Subtle scale (0.95–1.05) on press for tappable items
- Restore on release
- Don't shift layout bounds

---

## Category 8: Forms & Feedback (MEDIUM)

### Input Labels
- Visible label per input (not placeholder-only)
- Use `<label for="id">` association
- Helper text below complex inputs, not just placeholder

### Error Placement
- Show error directly below related field
- For multiple errors: summary at top + anchor links to each field
- Error messages: state cause + how to fix (not "Invalid input")

### Validation Timing
- Validate on blur, not keystroke
- Show error only after user finishes input
- Inline validation prevents submission surprises

### Submit Feedback
- Loading state during async submit
- Success: brief visual feedback (checkmark, toast, color flash)
- Error: clear message with recovery path
- Disable submit button during processing

### Required Fields
- Mark with asterisk or "Required" label
- Don't overuse required — only when truly necessary

### Empty States
- Helpful message + action when no content
- Not blank space or generic "No data"
- Guide user toward next step

### Toast Notifications
- Auto-dismiss in 3–5 seconds
- Use `aria-live="polite"` for screen readers
- Don't steal focus
- Stacking: max 3 visible, newest on top

### Confirmation Dialogs
- Confirm before destructive actions (delete, discard)
- Destructive action visually separated (red color)
- Allow undo when possible ("Undo delete" toast)

### Progressive Disclosure
- Reveal complex options progressively
- Don't overwhelm users upfront
- Multi-step flows: show step indicator + allow back

### Input Types
- Use semantic types: `email`, `tel`, `number`, `password`
- Triggers correct mobile keyboard
- `autocomplete` attributes for autofill support

### Password Fields
- Show/hide toggle
- Don't auto-capitalize or auto-correct

### Form Auto-Save
- Long forms should auto-save drafts
- Prevent data loss on accidental dismissal
- Confirm before dismissing modal with unsaved changes

### Focus Management
- After submit error, auto-focus first invalid field
- After route change, move focus to main content
- Maintain logical tab order

---

## Category 9: Navigation Patterns (HIGH)

### Bottom Navigation (Mobile)
- Maximum 5 items
- Labels with icons (not icon-only)
- Current location visually highlighted
- For top-level screens only — never nest sub-navigation

### Top Navigation
- iOS: bottom tab bar for top-level
- Android: top app bar with navigation icon
- Web: breadcrumbs for 3+ level hierarchies

### Back Behavior
- Predictable and consistent
- Preserve scroll position and state
- Support system gestures (swipe-back, predictive back)
- Never silently reset navigation stack

### Deep Linking
- All key screens reachable via URL/link
- Required for sharing and notifications
- Maintain back-path integrity

### Navigation State
- Current location highlighted (color, weight, indicator)
- Primary vs secondary nav clearly separated
- Core navigation reachable from deep pages

### Modals vs Navigation
- Modals for secondary tasks, not primary flows
- Break primary flows into pages, not modals
- Clear close/dismiss affordance
- Swipe-down to dismiss on mobile

### Overflow
- When actions exceed space, use overflow/more menu
- Don't cram elements

### Search
- Easily reachable (top bar or dedicated tab)
- Provide recent/suggested queries
- Keyboard accessible

### Badges
- Use sparingly for unread/pending
- Clear after user visits
- Don't overuse — badge fatigue

### Adaptive Navigation
- Large screens (≥1024px): sidebar preferred
- Small screens: bottom/top nav
- Consistent placement across all pages

---

## Category 10: Charts & Data Visualization (LOW)

### Chart Type Selection
- Trend over time → Line chart
- Comparison → Bar/column chart
- Proportion → Pie/donut (max 5 categories)
- Distribution → Histogram
- Correlation → Scatter plot
- Funnel → Funnel chart
- Geographic → Heat map / choropleth

### Accessibility
- Provide data table alternative
- Screen reader summary of key insight
- Interactive elements keyboard-navigable
- Don't rely on color alone — add patterns/textures

### Color Guidance
- Accessible palettes; avoid red/green only for colorblind
- Data lines/bars vs background ≥3:1
- Data text labels ≥4.5:1

### Legends & Labels
- Always show legend near chart
- Label axes with units and readable scale
- Direct labeling for small datasets
- Auto-skip crowded axis ticks on small screens

### Tooltips
- Show exact values on hover (web) or tap (mobile)
- Keyboard-reachable, not hover-only
- Don't obscure the data point

### Responsive Charts
- Reflow or simplify on small screens
- Horizontal bar instead of vertical on narrow screens
- Fewer ticks, fewer data points visible

### Loading & Empty States
- Skeleton or shimmer while loading
- Meaningful empty state ("No data yet" + guidance)
- Error state: message + retry action

### Data Density
- Limit information density per chart
- Split into multiple charts if needed
- For 1000+ points: aggregate, sample, or provide drill-down

### Number Formatting
- Locale-aware formatting for numbers, dates, currencies
- Tabular figures for alignment
- Consistent precision

### Interactivity
- Legend clickable to toggle series
- Drill-down with clear back-path and breadcrumb
- Time series: allow granularity switching (day/week/month)
- Export option for data-heavy products (CSV/image)
