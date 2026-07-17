# Phantom Works — Design Token Reference

> Persona 5 inspired design system. Dark-first, high contrast, red/black, layered cutouts.
> See `tokens.css` for the complete CSS custom property set with both modes.

---

## Quick Reference

| Token | Dark Mode | Light Mode | Usage |
|-------|-----------|------------|-------|
| `--color-primary` | `#D40000` | `#B80000` | Buttons, links, active states, borders |
| `--color-on-primary` | `#FFFFFF` | `#FFFFFF` | Text on primary backgrounds |
| `--color-accent` | `#FFFFFF` | `#D40000` | Secondary emphasis, highlights |
| `--surface-page` | `#0A0A0A` | `#F5F5F0` | Page background |
| `--surface-card` | `#121212` | `#FFFFFF` | Cards, containers |
| `--surface-elevated` | `#1A1A1A` | `#FFFFFF` | Modals, dropdowns, popovers |
| `--text-primary` | `#FFFFFF` | `#0A0A0A` | Headings, body text |
| `--text-secondary` | `#D4D4D4` | `#6B6B6B` | Subdued text, descriptions |
| `--border-default` | `#2A2A2A` | `#DDD` | Dividers, input borders |
| `--shadow-md` | `0 4px 0 #D40000, ...` | same | Red-bottom-shadow (P5 signature) |

---

## Design Principles

1. **Dark-First** — The default experience is near-black (`#0A0A0A`). Light mode is an inverted afterthought for accessibility.
2. **Red is Power** — Phantom Red (`#D40000`) is the only accent. It marks every interactive element, active state, and section divider. Never dilute it with other accent colors.
3. **Paper Cutouts** — UI elements float with a red offset shadow underneath (`0 4px 0 var(--color-primary)`), creating a stacked-paper physicality.
4. **Sharp & Intentional** — Border-radius is minimal (2-4px). Corners are crisp. Every element earns its curve.
5. **Typography as Attitude** — Headings use JetBrains Mono (monospace, terminal-like, technical). Body uses Inter (clean, readable). All labels are UPPERCASE with wide letter-spacing.
6. **Mask Motif** — The `.phantom-mask` utility creates the signature P5 layered cutout effect: a card with an offset red frame behind it.



---

## Complete Color Palette

### Phantom Red Ramp
```
#7A0000  #9C0000  #B80000  #D40000  #E60000  #FF1A1A  #FF5555  #FF8888  #FFCCCC
```

### Semantic States
| Token | Dark | Light | Meaning |
|-------|------|-------|---------|
| `--state-success` | `#22C55E` | `#16A34A` | Green — confirmed, available |
| `--state-warning` | `#F59E0B` | `#D97706` | Amber — caution, limited |
| `--state-danger` | `#FF1A1A` | `#DC2626` | Red — error, sold out, destructive |
| `--state-info` | `#3B82F6` | `#2563EB` | Blue — information |

---

## Typography

| Level | Size | Weight | Letter-Spacing | Font | P5 Reference |
|-------|------|--------|----------------|------|-------------|
| Display | 48px | 700 | -0.02em | JetBrains Mono | Main menu titles |
| H1 | 36px | 700 | -0.01em | JetBrains Mono | Section headers |
| H2 | 28px | 700 | -0.01em | JetBrains Mono | Card titles |
| H3 | 22px | 700 | normal | JetBrains Mono | Sub-section titles |
| Body | 15px | 400 | normal | Inter | Paragraphs, descriptions |
| Small | 13px | 400 | normal | Inter | Secondary info |
| Caption | 11px | 600 | 0.08em | Inter | Labels, timestamps |
| Label | 11px | 700 | 0.12em | Inter UPPERCASE | Button text, nav items |

---

## Shadows (P5 Signature)

```css
/* Each shadow includes a colored bottom edge (paper stack effect) */
--shadow-sm: 0 2px 0 var(--red-600);
--shadow-md: 0 4px 0 var(--red-600), 0 6px 12px rgba(0,0,0,0.4);
--shadow-lg: 0 8px 0 var(--red-600), 0 12px 24px rgba(0,0,0,0.5);
--shadow-xl: 0 12px 0 var(--red-600), 0 20px 40px rgba(0,0,0,0.6);
```

---

## Spacing Scale

```
4   8   12   16   24   32   48   64   96   128
```

---

## Radius

```
sm: 2px    md: 4px    lg: 8px    xl: 12px    full: 9999px
```

---

## CSS Utilities

| Class | Effect |
|-------|--------|
| `.phantom-mask` | Card with offset red frame behind it (P5 layered cutout) |
| `.phantom-stripe` | Diagonal red corner accent bar |
| `.phantom-divider` | 4px thick red horizontal rule |
