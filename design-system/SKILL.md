# PHANTOM WORKS — Design System

> Persona 5 inspired. Dark-first. High contrast. Red/black. Layered cutouts.
> Framework: Tailwind CSS · Theme: Dark-first with inverted light mode · 2026-07-17

## Design DNA

| Trait | Value |
|-------|-------|
| Vibe | Terminal rebellion — hacker chic meets punk elegance |
| Colors | Near-black, phantom red (#D40000), white |
| Typography | JetBrains Mono (monospace headings) + Inter (clean body) |
| Shapes | Sharp corners, intentional radii, offset layers |
| Depth | Paper cutout red shadows (0 4px 0 #D40000) |
| Labels | Always UPPERCASE with 0.12em letter-spacing |
| Motion | Fast (150-300ms), whip-like easing, staggered entries |

## Quick Start

```html
<link rel="stylesheet" href="design-system/references/tokens.css">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600;700;800&display=swap" rel="stylesheet">
```

No JavaScript required. Dark mode is default. Light mode activates via `prefers-color-scheme: light`.

## Core Tokens

| Token | Dark | Light |
|-------|------|-------|
| `--color-primary` | `#D40000` | `#B80000` |
| `--surface-page` | `#0A0A0A` | `#F5F5F0` |
| `--surface-card` | `#121212` | `#FFFFFF` |
| `--text-primary` | `#FFFFFF` | `#0A0A0A` |
| `--border-default` | `#2A2A2A` | `#DDD` |
| `--shadow-md` | `0 4px 0 #D40000, 0 6px 12px rgba(0,0,0,0.4)` | same |

## Signature CSS Utilities

```html
<!-- Paper cutout effect (P5 mask / layered card) -->
<div class="phantom-mask">
  Content appears to float with a red frame behind it.
</div>

<!-- Diagonal red corner accent -->
<div class="phantom-stripe">
  A subtle red diagonal stripe in the top-right corner.
</div>

<!-- Thick red horizontal divider -->
<hr class="phantom-divider">
```

## Semantic States

```
SUCCESS  → #22C55E  (green)
WARNING  → #F59E0B  (amber)
DANGER   → #FF1A1A  (red)
INFO     → #3B82F6  (blue)
```

## Typography Scale

```
DISPLAY  48px  JetBrains Mono (700)  ls:-0.02em  — Main hero titles
H1       36px  JetBrains Mono (700)  ls:-0.01em  — Section headers
H2       28px  JetBrains Mono (700)  ls:-0.01em  — Card titles
H3       22px  JetBrains Mono (700)              — Sub-section titles
BODY     15px  Inter                lh:1.6       — Paragraphs
SMALL    13px  Inter                             — Secondary info
CAPTION  11px  Inter 600            ls:0.08em    — Labels, timestamps
LABEL    11px  Inter 700            ls:0.12em    — UPPERCASE button text
```

## Files

| File | Purpose |
|------|---------|
| `references/tokens.css` | CSS custom properties, light+dark, utilities |
| `references/tokens.md` | Token documentation |
| `references/components.md` | Component specs |
| `assets/tailwind.config.js` | Tailwind v3+ config |
| `assets/font-import.html` | Google Fonts links |
| `design-system.json` | Machine-readable tokens |

## Persona 5 Anti-Patterns (Don't)

- Don't use gradients (P5 is flat, sharp, high-contrast)
- Don't use purple/pink/neon (P5 uses ONLY red as accent)
- Don't use large border-radius (keep it 2-8px max)
- Don't use emoji as icons (use Lucide or Heroicons)
- Don't center everything (P5 often left-aligns with asymmetric balance)
- Don't soften shadows (the hard red offset shadow IS the brand)
