# UI/UX Libera

LIBERA Studio fork of [ui-ux-pro-max](https://github.com/yuvalsuede/ai-component-generator) v2.5.0 — updated for 2025 standards.

## What's here

| Path | Content |
|------|---------|
| `SKILL.md` | The Claude Code skill — install in `~/.claude/commands/ui-ux-libera.md` |
| `data/*.csv` | Design databases: 50+ styles, 161 color palettes, 57 font pairings, 161 product types, 99 UX guidelines, 25 chart types |
| `data/stacks/` | Stack-specific guidelines: React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, and more |
| `scripts/` | Python search engine (BM25 + regex) for querying the databases |

## Install the skill

```bash
cp SKILL.md ~/.claude/commands/ui-ux-libera.md
```

Invoke with `/ui-ux-libera` in any Claude Code session.

## Use the databases

```bash
python3 scripts/search.py "saas minimal dark mode" --design-system
python3 scripts/search.py "glassmorphism" --domain style
python3 scripts/search.py "elegant modern" --domain typography
python3 scripts/search.py "dashboard" --stack nextjs
```

## Changes from upstream

- AVIF first (93%+ browser support 2025), WebP as fallback
- Stack-agnostic (removed React Native hardcode)
- Added `container-queries` — Baseline 2025
- Added `view-transitions` — Baseline 2025
- Added §11 Interaction States
- Added §12 Launch Completeness
- Pre-delivery checklist updated with Performance 2025 section
