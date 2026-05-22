# skill-ui-ux-Libera

> A Claude Code skill for UI/UX design intelligence — LIBERA Studio fork of ui-ux-pro-max v2.5.0, updated for 2025 web standards.

**Maintained by [LIBERA Studio](https://github.com/sayitlouderdev) · License: MIT**

---

## What this is

A permanent fork of the [ui-ux-pro-max](https://github.com/yuvalsuede/ai-component-generator) Claude Code skill (v2.5.0 by Next Level Builder), with targeted updates for 2025 browser standards and stack-agnostic usage.

The CSV databases and Python search scripts in this repository are **substantially the work of Next Level Builder** (MIT license). The SKILL.md contains LIBERA Studio modifications. See [NOTICE.md](NOTICE.md) for full attribution.

### Why fork instead of using the original?

The original `ui-ux-pro-max` lives in `~/.claude/plugins/cache/` and gets **overwritten on every plugin update**. This fork lives in a permanent location (`~/.claude/commands/`) that is never touched by plugin updates.

---

## What changed from upstream (v2.5.0)

| Change | Detail |
|--------|--------|
| **AVIF first** | AVIF now has 93%+ browser support in 2025. Updated to recommend AVIF as primary format, WebP as fallback (upstream had it reversed) |
| **Stack-agnostic** | Removed hardcoded "React Native is this project's only tech stack" from Step 1. Now supports all 10 stacks equally |
| **Container Queries** | Added `container-queries` rule — Baseline 2025, all major engines |
| **View Transitions API** | Added `view-transitions` rule — Baseline 2025, all major engines |
| **Viewport height** | Added `viewport-height-safe` — use `min-h-[100dvh]`, never `h-screen` (iOS Safari fix) |
| **Backdrop blur scope** | Added `backdrop-blur-scope` — only on fixed/sticky elements, GPU repaint warning |
| **IntersectionObserver** | Added `intersection-observer` — use instead of `scroll` event listeners |
| **§11 Interaction States** | New section: every component needs loading/empty/error/active states — not just success |
| **§12 Launch Completeness** | New section: meta tags, favicon, legal links, 404, skip-to-content — items AI consistently forgets |
| **Performance 2025 checklist** | Pre-delivery checklist updated with all 2025 additions |

---

## Repository structure

```
skill-ui-ux-Libera/
├── SKILL.md          ← The Claude Code skill — install in ~/.claude/commands/
├── data/             ← CSV databases from ui-ux-pro-max v2.5.0
│   ├── styles.csv        50+ UI styles with AI prompts and CSS keywords
│   ├── colors.csv        161 color palettes by product type
│   ├── typography.csv    57 font pairings with Google Fonts imports
│   ├── products.csv      161 product types with reasoning rules
│   ├── ux-guidelines.csv 99 UX best practices and anti-patterns
│   ├── charts.csv        25 chart types with library recommendations
│   ├── landing.csv       Landing page structures and CTA strategies
│   ├── google-fonts.csv  Individual Google Fonts lookup
│   ├── ui-reasoning.csv  Design system reasoning rules
│   └── stacks/           Stack-specific guidelines (17 stacks)
├── scripts/          ← Python search engine from ui-ux-pro-max v2.5.0
│   ├── search.py         CLI entry point (BM25 + regex hybrid)
│   ├── core.py           Search engine core
│   └── design_system.py  Design system generation
├── LICENSE           ← MIT
├── NOTICE.md         ← Third-party attribution
└── CONTRIBUTING.md   ← How to contribute
```

---

## Install the skill

```bash
# Copy SKILL.md to the permanent commands directory
cp SKILL.md ~/.claude/commands/ui-ux-libera.md
```

Invoke with `/ui-ux-libera` in any Claude Code session. Works globally across all projects.

---

## Use the databases

Requires Python 3 (no external dependencies).

```bash
# Full design system for a project
python3 scripts/search.py "saas minimal dark mode" --design-system -p "Project Name"

# Search specific domain
python3 scripts/search.py "glassmorphism dark" --domain style
python3 scripts/search.py "elegant modern" --domain typography
python3 scripts/search.py "entertainment vibrant" --domain color

# Stack-specific guidelines
python3 scripts/search.py "performance navigation" --stack nextjs
python3 scripts/search.py "accessibility gestures" --stack react-native
```

### Available domains

`product` · `style` · `color` · `typography` · `landing` · `chart` · `ux` · `google-fonts` · `react` · `web` · `prompt`

### Available stacks

`react` · `nextjs` · `vue` · `nuxtjs` · `nuxt-ui` · `astro` · `svelte` · `html-tailwind` · `shadcn` · `react-native` · `flutter` · `swiftui` · `jetpack-compose` · `angular` · `laravel` · `threejs`

---

## Related repositories

| Repository | What it contains |
|------------|-----------------|
| [skill-web-design](https://github.com/sayitlouderdev/skill-web-design) | Design knowledge base: 29 reference docs on brand, color, typography, motion, layout, interaction, and more |

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

---

## License and attribution

This repository is licensed under the **MIT License**. See [LICENSE](LICENSE).

The CSV databases and Python scripts are the work of Next Level Builder (ui-ux-pro-max, MIT). The SKILL.md contains LIBERA Studio modifications built on top of the original. See [NOTICE.md](NOTICE.md) for full attribution.
