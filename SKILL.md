---
name: ui-ux-libera
description: "UI/UX design intelligence for web and mobile. LIBERA Studio fork of ui-ux-pro-max v2.5.0 — updated for 2025 standards (AVIF-first, View Transitions API, Container Queries, stack-agnostic workflow). Includes 50+ styles, 161 color palettes, 57 font pairings, 161 product types, 99 UX guidelines, and 25 chart types across 10 stacks."
---

# UI/UX Libera — Design Intelligence
*LIBERA Studio fork of ui-ux-pro-max v2.5.0 — updated May 2026*

Comprehensive design guide for web and mobile applications. Contains 50+ styles, 161 color palettes, 57 font pairings, 161 product types with reasoning rules, 99 UX guidelines, and 25 chart types across 10 technology stacks. Searchable database with priority-based recommendations.

## When to Apply

This Skill should be used when the task involves **UI structure, visual design decisions, interaction patterns, or user experience quality control**.

### Must Use

- Designing new pages (Landing Page, Dashboard, Admin, SaaS, Mobile App)
- Creating or refactoring UI components (buttons, modals, forms, tables, charts, etc.)
- Choosing color schemes, typography systems, spacing standards, or layout systems
- Reviewing UI code for user experience, accessibility, or visual consistency
- Implementing navigation structures, animations, or responsive behavior
- Making product-level design decisions (style, information hierarchy, brand expression)
- Improving perceived quality, clarity, or usability of interfaces

### Skip

- Pure backend logic development
- Only involving API or database design
- Performance optimization unrelated to the interface
- Infrastructure or DevOps work
- Non-visual scripts or automation tasks

**Decision criteria**: If the task will change how a feature **looks, feels, moves, or is interacted with**, use this skill.

## Rule Categories by Priority

| Priority | Category | Impact | Key Checks (Must Have) | Anti-Patterns (Avoid) |
|----------|----------|--------|------------------------|------------------------|
| 1 | Accessibility | CRITICAL | Contrast 4.5:1, Alt text, Keyboard nav, Aria-labels | Removing focus rings, Icon-only buttons without labels |
| 2 | Touch & Interaction | CRITICAL | Min size 44×44px, 8px+ spacing, Loading feedback | Reliance on hover only, Instant state changes (0ms) |
| 3 | Performance | HIGH | AVIF/WebP, Lazy loading, Reserve space (CLS < 0.1) | Layout thrashing, Cumulative Layout Shift |
| 4 | Style Selection | HIGH | Match product type, Consistency, SVG icons (no emoji) | Mixing flat & skeuomorphic randomly, Emoji as icons |
| 5 | Layout & Responsive | HIGH | Mobile-first breakpoints, Viewport meta, No horizontal scroll | Horizontal scroll, Fixed px container widths, Disable zoom |
| 6 | Typography & Color | MEDIUM | Base 16px, Line-height 1.5, Semantic color tokens | Text < 12px body, Gray-on-gray, Raw hex in components |
| 7 | Animation | MEDIUM | Duration 150–300ms, Motion conveys meaning, Spatial continuity | Decorative-only animation, Animating width/height, No reduced-motion |
| 8 | Forms & Feedback | MEDIUM | Visible labels, Error near field, Helper text, Progressive disclosure | Placeholder-only label, Errors only at top, Overwhelm upfront |
| 9 | Navigation Patterns | HIGH | Predictable back, Bottom nav ≤5, Deep linking | Overloaded nav, Broken back behavior, No deep links |
| 10 | Charts & Data | LOW | Legends, Tooltips, Accessible colors | Relying on color alone to convey meaning |
| 11 | Interaction States | HIGH | Loading, Empty, Error, Active feedback for every component | Only implementing the success state |
| 12 | Launch Completeness | MEDIUM | Meta tags, Favicon, Legal links, 404, Skip-to-content | Shipping without these basics |

## Quick Reference

### 1. Accessibility (CRITICAL)

- `color-contrast` - Minimum 4.5:1 ratio for normal text (large text 3:1); WCAG 2.2 AA
- `focus-states` - Visible focus rings on interactive elements (2–4px; Apple HIG, MD3)
- `alt-text` - Descriptive alt text for meaningful images
- `aria-labels` - aria-label for icon-only buttons; accessibilityLabel in native
- `keyboard-nav` - Tab order matches visual order; full keyboard support
- `form-labels` - Use label with for attribute
- `skip-links` - Skip to main content for keyboard users
- `heading-hierarchy` - Sequential h1→h6, no level skip
- `color-not-only` - Don't convey info by color alone (add icon/text)
- `dynamic-type` - Support system text scaling; avoid truncation as text grows
- `reduced-motion` - Respect prefers-reduced-motion; reduce/disable animations when requested
- `voiceover-sr` - Meaningful accessibilityLabel/accessibilityHint; logical reading order
- `escape-routes` - Provide cancel/back in modals and multi-step flows
- `keyboard-shortcuts` - Preserve system and a11y shortcuts; offer keyboard alternatives for drag-and-drop

### 2. Touch & Interaction (CRITICAL)

- `touch-target-size` - Min 44×44pt (Apple) / 48×48dp (Material Design 3); extend hit area beyond visual bounds if needed
- `touch-spacing` - Minimum 8px/8dp gap between touch targets
- `hover-vs-tap` - Use click/tap for primary interactions; don't rely on hover alone
- `loading-buttons` - Disable button during async operations; show spinner or progress
- `error-feedback` - Clear error messages near problem
- `cursor-pointer` - Add cursor-pointer to clickable elements (Web)
- `gesture-conflicts` - Avoid horizontal swipe on main content; prefer vertical scroll
- `tap-delay` - Use touch-action: manipulation to reduce 300ms delay (Web)
- `standard-gestures` - Use platform standard gestures consistently; don't redefine
- `system-gestures` - Don't block system gestures (Control Center, back swipe, etc.)
- `press-feedback` - Visual feedback on press (ripple/highlight; MD3 state layers)
- `haptic-feedback` - Use haptic for confirmations and important actions; avoid overuse
- `gesture-alternative` - Don't rely on gesture-only interactions; always provide visible controls
- `safe-area-awareness` - Keep primary touch targets away from notch, Dynamic Island, gesture bar
- `no-precision-required` - Avoid requiring pixel-perfect taps on small icons or thin edges
- `swipe-clarity` - Swipe actions must show clear affordance or hint
- `drag-threshold` - Use a movement threshold before starting drag to avoid accidental drags

### 3. Performance (HIGH)

- `image-optimization` - Use AVIF first (93%+ browser support in 2025), WebP as fallback; responsive images (srcset/sizes), lazy load non-critical assets
- `image-dimension` - Declare width/height or use aspect-ratio to prevent layout shift (CLS)
- `font-loading` - Use font-display: swap/optional to avoid invisible text (FOIT)
- `font-preload` - Preload only critical fonts; avoid overusing preload on every variant
- `critical-css` - Prioritize above-the-fold CSS (inline critical CSS or early-loaded stylesheet)
- `lazy-loading` - Lazy load non-hero components via dynamic import / route-level splitting
- `bundle-splitting` - Split code by route/feature (React Suspense / Next.js dynamic) to reduce initial load
- `third-party-scripts` - Load third-party scripts async/defer; audit and remove unnecessary ones
- `reduce-reflows` - Avoid frequent layout reads/writes; batch DOM reads then writes
- `content-jumping` - Reserve space for async content to avoid layout jumps (CLS < 0.1)
- `lazy-load-below-fold` - Use loading="lazy" for below-the-fold images and heavy media
- `virtualize-lists` - Virtualize lists with 50+ items to improve memory efficiency and scroll performance
- `main-thread-budget` - Keep per-frame work under ~16ms for 60fps; move heavy tasks off main thread
- `progressive-loading` - Use skeleton screens / shimmer instead of long blocking spinners for >1s operations
- `input-latency` - Keep input latency under ~100ms for taps/scrolls
- `tap-feedback-speed` - Provide visual feedback within 100ms of tap
- `debounce-throttle` - Use debounce/throttle for high-frequency events (scroll, resize, input)
- `offline-support` - Provide offline state messaging and basic fallback (PWA / mobile)
- `network-fallback` - Offer degraded modes for slow networks (lower-res images, fewer animations)
- `container-queries` - Use CSS container queries (@container) instead of media queries for component-level responsiveness; Baseline 2025
- `view-transitions` - Use the View Transitions API for page/route transitions; Baseline 2025, supported in all major engines
- `viewport-height-safe` - Use `min-h-[100dvh]` for full-height sections; never `h-screen` — iOS Safari jumps catastrophically when the URL bar hides/shows
- `backdrop-blur-scope` - Apply `backdrop-blur` only to fixed/sticky elements (navbars, overlays); never on scrolling containers — causes continuous GPU repaints on mobile
- `intersection-observer` - For scroll-triggered animations use IntersectionObserver; never `window.addEventListener('scroll')` — causes continuous reflows and kills mobile performance

### 4. Style Selection (HIGH)

- `style-match` - Match style to product type
- `consistency` - Use same style across all pages
- `no-emoji-icons` - Use SVG icons (Heroicons, Lucide), not emojis
- `no-side-stripe-borders` - Never use `border-left` or `border-right` >1px as colored accent on cards, alerts, or list items — use background tints, full borders, or spacing instead
- `color-palette-from-product` - Choose palette from product/industry context
- `effects-match-style` - Shadows, blur, radius aligned with chosen style
- `platform-adaptive` - Respect platform idioms (iOS HIG vs Material Design 3)
- `state-clarity` - Make hover/pressed/disabled states visually distinct while staying on-style
- `elevation-consistent` - Use a consistent elevation/shadow scale for cards, sheets, modals
- `dark-mode-pairing` - Design light/dark variants together
- `icon-style-consistent` - Use one icon set/visual language across the product
- `system-controls` - Prefer native/system controls; only customize when branding requires it
- `blur-purpose` - Use blur to indicate background dismissal (modals, sheets), not as decoration
- `primary-action` - Each screen should have only one primary CTA

### 5. Layout & Responsive (HIGH)

- `viewport-meta` - width=device-width initial-scale=1 (never disable zoom)
- `mobile-first` - Design mobile-first, then scale up to tablet and desktop
- `breakpoint-consistency` - Use systematic breakpoints (e.g. 375 / 768 / 1024 / 1440)
- `readable-font-size` - Minimum 16px body text on mobile (avoids iOS auto-zoom)
- `line-length-control` - Mobile 35–60 chars per line; desktop 60–75 chars
- `horizontal-scroll` - No horizontal scroll on mobile
- `spacing-scale` - Use 4pt/8dp incremental spacing system
- `touch-density` - Keep component spacing comfortable for touch
- `container-width` - Consistent max-width on desktop (max-w-6xl / 7xl)
- `z-index-management` - Define layered z-index scale (e.g. 0 / 10 / 20 / 40 / 100 / 1000)
- `fixed-element-offset` - Fixed navbar/bottom bar must reserve safe padding for underlying content
- `scroll-behavior` - Avoid nested scroll regions that interfere with the main scroll experience
- `viewport-units` - Prefer min-h-dvh over 100vh on mobile
- `orientation-support` - Keep layout readable and operable in landscape mode
- `content-priority` - Show core content first on mobile; fold or hide secondary content
- `visual-hierarchy` - Establish hierarchy via size, spacing, contrast — not color alone
- `grid-over-flex-math` - Use CSS Grid for multi-column layouts; never `calc(33% - 1rem)` flexbox math — unreliable across browsers
- `scroll-smooth` - Add `scroll-behavior: smooth` on `<html>` for anchor link navigation
- `semantic-html` - Use `<nav>`, `<main>`, `<article>`, `<aside>`, `<section>`; avoid div soup — improves accessibility and SEO

### 6. Typography & Color (MEDIUM)

- `line-height` - Use 1.5-1.75 for body text
- `line-length` - Limit to 65-75 characters per line
- `font-pairing` - Match heading/body font personalities
- `font-scale` - Consistent type scale (e.g. 12 14 16 18 24 32)
- `contrast-readability` - Darker text on light backgrounds (e.g. slate-900 on white)
- `text-styles-system` - Use platform type system: iOS 11 Dynamic Type / Material 3 type roles
- `weight-hierarchy` - Bold headings (600–700), Regular body (400), Medium labels (500)
- `color-semantic` - Define semantic color tokens (primary, secondary, error, surface, on-surface) not raw hex
- `color-dark-mode` - Dark mode uses desaturated / lighter tonal variants, not inverted colors
- `color-accessible-pairs` - Foreground/background pairs must meet 4.5:1 (AA) or 7:1 (AAA); verify with tools
- `color-not-decorative-only` - Functional color (error red, success green) must include icon/text
- `truncation-strategy` - Prefer wrapping over truncation; when truncating use ellipsis and tooltip
- `letter-spacing` - Respect default letter-spacing per platform; avoid tight tracking on body text
- `number-tabular` - Apply `font-variant-numeric: tabular-nums` to all price, metric, and data columns to prevent layout shift on number updates
- `whitespace-balance` - Use whitespace intentionally to group related items; avoid visual clutter
- `text-wrap-headings` - Use `text-wrap: balance` on headings and `text-wrap: pretty` on body to prevent orphaned words
- `no-pure-black` - Avoid `#000000` for text; use off-black (`#111111` / `#0a0a0a`) — pure black on white creates harsh contrast that strains reading

### 7. Animation (MEDIUM)

- `duration-timing` - Use 150–300ms for micro-interactions; complex transitions ≤400ms; avoid >500ms
- `transform-performance` - Use transform/opacity only; avoid animating width/height/top/left
- `loading-states` - Show skeleton or progress indicator when loading exceeds 300ms
- `excessive-motion` - Animate 1-2 key elements per view max
- `easing` - Use ease-out for entering, ease-in for exiting; avoid linear for UI transitions
- `motion-meaning` - Every animation must express a cause-effect relationship, not just be decorative
- `state-transition` - State changes should animate smoothly, not snap
- `continuity` - Page/screen transitions should maintain spatial continuity
- `parallax-subtle` - Use parallax sparingly; must respect reduced-motion
- `spring-physics` - Prefer spring/physics-based curves over linear for natural feel
- `exit-faster-than-enter` - Exit animations shorter than enter (~60–70% of enter duration)
- `stagger-sequence` - Stagger list/grid item entrance by 30–50ms per item
- `shared-element-transition` - Use shared element / hero transitions for visual continuity
- `interruptible` - Animations must be interruptible; user tap/gesture cancels in-progress animation
- `no-blocking-animation` - Never block user input during an animation
- `scale-feedback` - Subtle scale (0.95–1.05) on press for tappable cards/buttons
- `motion-consistency` - Unify duration/easing tokens globally
- `modal-motion` - Modals/sheets should animate from their trigger source for spatial context
- `navigation-direction` - Forward navigation animates left/up; backward animates right/down
- `motion-state-isolation` - For magnetic hover or infinite loops with Motion/Framer Motion: use `useMotionValue` + `useTransform` outside render cycle; never `useState` — prevents performance collapse on mobile

### 8. Forms & Feedback (MEDIUM)

- `input-labels` - Visible label per input (not placeholder-only)
- `error-placement` - Show error below the related field
- `submit-feedback` - Loading then success/error state on submit
- `required-indicators` - Mark required fields (e.g. asterisk)
- `empty-states` - Helpful message and action when no content
- `toast-dismiss` - Auto-dismiss toasts in 3-5s
- `confirmation-dialogs` - Confirm before destructive actions
- `input-helper-text` - Provide persistent helper text below complex inputs
- `disabled-states` - Disabled elements use reduced opacity (0.38–0.5) + cursor change
- `progressive-disclosure` - Reveal complex options progressively; don't overwhelm users upfront
- `inline-validation` - Validate on blur (not keystroke); show error only after user finishes input
- `input-type-keyboard` - Use semantic input types (email, tel, number) to trigger correct mobile keyboard
- `password-toggle` - Provide show/hide toggle for password fields
- `autofill-support` - Use autocomplete / textContentType attributes
- `undo-support` - Allow undo for destructive or bulk actions
- `success-feedback` - Confirm completed actions with brief visual feedback
- `error-recovery` - Error messages must include a clear recovery path (retry, edit, help link)
- `multi-step-progress` - Multi-step flows show step indicator or progress bar; allow back navigation
- `form-autosave` - Long forms should auto-save drafts to prevent data loss
- `error-clarity` - Error messages must state cause + how to fix (not just "Invalid input")
- `field-grouping` - Group related fields logically
- `focus-management` - After submit error, auto-focus the first invalid field (WCAG)
- `error-summary` - For multiple errors, show summary at top with anchor links to each field
- `modal-last-resort` - Modals interrupt flow and block content; exhaust inline editing, slide-overs, or expandable sections first — modals are for high-stakes confirmation only
- `no-window-alert` - Never use `window.alert()` or `window.confirm()` — use custom inline messages and confirmation UI

### 9. Navigation Patterns (HIGH)

- `bottom-nav-limit` - Bottom navigation max 5 items; use labels with icons (Material Design 3)
- `drawer-usage` - Use drawer/sidebar for secondary navigation, not primary actions
- `back-behavior` - Back navigation must be predictable and consistent; preserve scroll/state
- `deep-linking` - All key screens must be reachable via deep link / URL
- `tab-bar-ios` - iOS: use bottom Tab Bar for top-level navigation (Apple HIG)
- `top-app-bar-android` - Android: use Top App Bar with navigation icon (Material Design 3)
- `nav-label-icon` - Navigation items must have both icon and text label
- `nav-state-active` - Current location must be visually highlighted in navigation
- `nav-hierarchy` - Primary nav (tabs/bottom bar) vs secondary nav (drawer/settings) must be clearly separated
- `modal-escape` - Modals and sheets must offer a clear close/dismiss affordance
- `search-accessible` - Search must be easily reachable; provide recent/suggested queries
- `breadcrumb-web` - Web: use breadcrumbs for 3+ level deep hierarchies
- `state-preservation` - Navigating back must restore previous scroll position, filter state, and input
- `gesture-nav-support` - Support system gesture navigation (iOS swipe-back, Android predictive back)
- `tab-badge` - Use badges on nav items sparingly; clear after user visits
- `adaptive-navigation` - Large screens (≥1024px) prefer sidebar; small screens use bottom/top nav
- `back-stack-integrity` - Never silently reset the navigation stack
- `navigation-consistency` - Navigation placement must stay the same across all pages

### 10. Charts & Data (LOW)

- `chart-type` - Match chart type to data type (trend → line, comparison → bar, proportion → pie/donut)
- `color-guidance` - Use accessible color palettes; avoid red/green only pairs for colorblind users
- `data-table` - Provide table alternative for accessibility
- `pattern-texture` - Supplement color with patterns or shapes so data is distinguishable without color
- `legend-visible` - Always show legend; position near the chart
- `tooltip-on-interact` - Provide tooltips/data labels on hover (Web) or tap (mobile)
- `axis-labels` - Label axes with units and readable scale
- `responsive-chart` - Charts must reflow or simplify on small screens
- `empty-data-state` - Show meaningful empty state when no data exists
- `loading-chart` - Use skeleton or shimmer placeholder while chart data loads
- `animation-optional` - Chart entrance animations must respect prefers-reduced-motion
- `large-dataset` - For 1000+ data points, aggregate or sample; provide drill-down for detail
- `number-formatting` - Use locale-aware formatting for numbers, dates, currencies
- `no-pie-overuse` - Avoid pie/donut for >5 categories; switch to bar chart for clarity
- `sortable-table` - Data tables must support sorting with aria-sort indicating current sort state

### 11. Interaction States (HIGH)

Every interactive component needs all states implemented — AI default is to only build the "success" state.

- `loading-state` - Skeleton loaders matching exact layout shape for async content; no generic circular spinners for content areas
- `empty-state` - Designed "getting started" view when no data exists — not blank space; include a clear action
- `error-state` - Clear inline error messages with recovery path; never `window.alert()`
- `active-feedback` - Tactile press feedback: `scale(0.98)` or `translateY(1px)` on `:active` to simulate physical click
- `hover-state` - Every interactive element has a hover state (background shift, scale, or color change)
- `focus-visible` - `:focus-visible` for keyboard users; never remove outline without replacing it
- `disabled-visual` - Disabled elements look unclickable; reduced opacity + `cursor: not-allowed` + no interaction
- `dependency-check` - Before importing any animation or UI library, verify it exists in `package.json` — never assume availability

### 12. Launch Completeness (MEDIUM)

Items AI consistently forgets before shipping.

- `meta-tags` - Include `<title>`, `<meta name="description">`, `og:title`, `og:description`, `og:image`, `twitter:card` on every page
- `favicon` - Always include a branded favicon; no browser default
- `legal-footer` - Privacy policy + terms of service links in footer where legally required
- `custom-404` - Custom branded 404 page with navigation back; never expose server default
- `skip-to-content` - Hidden skip-link at page top for keyboard users: `<a href="#main" class="sr-only focus:not-sr-only">`
- `cookie-consent` - Compliant consent banner where required by jurisdiction (EU, UK, CA)
- `no-dead-links` - No buttons or links pointing to `#` without a real destination or disabled state
- `form-validation` - Client-side validation for email format, required fields, and length limits
- `back-navigation` - Every page has a way back; no dead ends in user flows

---

## How to Use

### Step 1: Analyze Requirements

Extract key information from the user request:
- **Product type**: Entertainment (social, video, music, gaming), Tool (scanner, editor, converter), Productivity (task manager, notes, calendar), or hybrid
- **Target audience**: Consumer or professional; consider age group and usage context
- **Style keywords**: playful, vibrant, minimal, dark mode, content-first, immersive, etc.
- **Stack**: Choose from React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui, or HTML/CSS

### Step 2: Generate Design System

Clone [skill-ui-ux-Libera](https://github.com/sayitlouderdev/skill-ui-ux-Libera) and run:

```bash
python3 scripts/search.py "<product_type> <industry> <keywords>" --design-system [-p "Project Name"]
```

If scripts are not available, apply the Quick Reference checklist above manually starting from Priority 1.

### Step 3: Domain Deep-Dives (as needed)

| Need | Domain |
|------|--------|
| Product type patterns | `product` |
| Style options | `style` |
| Color palettes | `color` |
| Font pairings | `typography` |
| Chart recommendations | `chart` |
| UX best practices | `ux` |

### Step 4: Stack Guidelines

Apply stack-specific best practices for your chosen framework. All 10 stacks supported: React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui, HTML/CSS.

---

## Pre-Delivery Checklist

### Visual Quality
- [ ] No emojis used as icons (use SVG instead)
- [ ] All icons come from a consistent icon family and style
- [ ] Semantic theme tokens are used consistently (no hardcoded hex in components)

### Interaction
- [ ] All tappable elements provide clear pressed feedback
- [ ] Touch targets meet minimum size (≥44×44pt iOS, ≥48×48dp Android)
- [ ] Micro-interaction timing stays in the 150–300ms range
- [ ] Disabled states are visually clear and non-interactive
- [ ] Screen reader focus order matches visual order

### Light/Dark Mode
- [ ] Primary text contrast ≥4.5:1 in both light and dark mode
- [ ] Secondary text contrast ≥3:1 in both modes
- [ ] Both themes tested before delivery

### Layout
- [ ] Safe areas respected for headers, tab bars, and bottom CTA bars
- [ ] Scroll content not hidden behind fixed/sticky bars
- [ ] Verified on small phone, large phone, and tablet (portrait + landscape)
- [ ] 4/8dp spacing rhythm maintained

### Accessibility
- [ ] All meaningful images/icons have accessibility labels
- [ ] Form fields have labels, hints, and clear error messages
- [ ] Color is not the only indicator
- [ ] Reduced motion and dynamic text size supported
- [ ] Accessibility traits/roles/states announced correctly

### Performance (2025)
- [ ] Images use AVIF format (WebP as fallback)
- [ ] Container queries used where component-level responsiveness is needed
- [ ] View Transitions API considered for page/route transitions
- [ ] CLS < 0.1 verified
- [ ] Full-height sections use `min-h-[100dvh]`, not `h-screen`
- [ ] `backdrop-blur` applied only to fixed/sticky elements
- [ ] Scroll animations use IntersectionObserver, not scroll event listener

### Interaction States
- [ ] Loading state implemented (skeleton, not spinner)
- [ ] Empty state designed and implemented
- [ ] Error state with recovery path
- [ ] Active/pressed feedback on all interactive elements
- [ ] All library imports verified in package.json

### Launch Completeness
- [ ] Meta tags present: title, description, og:image, twitter:card
- [ ] Branded favicon present
- [ ] Legal links in footer (privacy policy, terms)
- [ ] Custom 404 page
- [ ] Skip-to-content link present
- [ ] No dead links (`href="#"` without disabled state)
- [ ] Client-side form validation

---

## Common Sticking Points

| Problem | What to Do |
|---------|------------|
| Can't decide on style/color | Re-run design system query with different keywords |
| Dark mode contrast issues | Quick Reference §6: `color-dark-mode` + `color-accessible-pairs` |
| Animations feel unnatural | Quick Reference §7: `spring-physics` + `easing` + `exit-faster-than-enter` |
| Form UX is poor | Quick Reference §8: `inline-validation` + `error-clarity` + `focus-management` |
| Navigation feels confusing | Quick Reference §9: `nav-hierarchy` + `bottom-nav-limit` + `back-behavior` |
| Layout breaks on small screens | Quick Reference §5: `mobile-first` + `breakpoint-consistency` |
| Performance / jank | Quick Reference §3: `virtualize-lists` + `main-thread-budget` + `container-queries` |
| Images slow to load | Use AVIF first, WebP fallback; `lazy-load-below-fold` + `image-dimension` |
| iOS Safari layout jump | Replace `h-screen` with `min-h-[100dvh]` on full-height sections |
| Blur causes mobile lag | `backdrop-blur` only on fixed/sticky elements — never on scrolling containers |
| Scroll animations cause jank | Use IntersectionObserver; never `window.addEventListener('scroll')` |
| Component missing states | §11: implement loading + empty + error + active feedback for every component |
| Missing before launch | §12 checklist: meta tags, favicon, legal links, 404, skip-to-content |

---

*Fork di ui-ux-pro-max v2.5.0 — LIBERA Studio, maggio 2026. Non sovrascrivere con aggiornamenti del plugin originale.*
