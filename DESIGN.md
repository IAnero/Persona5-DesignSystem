# PHANTOM WORKS — Design System

> Persona 5 inspired · Dark-first with full light mode · High contrast · Red/black · Layered paper cutouts
> Framework: Tailwind CSS · Fonts: JetBrains Mono (headings) + Inter (body) · 2026-07-17

---

## Table of Contents

1. [Design DNA](#1-design-dna)
2. [Quick Start](#2-quick-start)
3. [Mode System](#3-mode-system)
4. [Color Palette](#4-color-palette)
5. [Typography](#5-typography)
6. [Spacing & Radius](#6-spacing--radius)
7. [Shadows](#7-shadows)
8. [Signature CSS Utilities](#8-signature-css-utilities)
9. [Component Specifications](#9-component-specifications)
10. [Semantic States](#10-semantic-states)
11. [Motion & Animation](#11-motion--animation)
12. [Anti-Patterns](#12-anti-patterns)
13. [File Map](#13-file-map)
14. [Prototype Instructions](#14-prototype-instructions-for-ai)

---

## 1. Design DNA

| Trait | Value |
|-------|-------|
| **Vibe** | Terminal rebellion — hacker chic meets punk elegance |
| **Colors** | Near-black `#0A0A0A`, Phantom Red `#D40000`, white `#FFFFFF` |
| **Typography** | JetBrains Mono (monospace headings) + Inter (clean body) |
| **Shapes** | Sharp corners (`2-4px` radius), intentional, offset layers |
| **Depth** | Paper cutout red shadows (`0 4px 0 #D40000`) |
| **Labels** | Always UPPERCASE with `0.12em` letter-spacing |
| **Motion** | Fast (`150-300ms`), whip-like easing, staggered entries |

### Design Principles

1. **Dark-First** — Default is near-black (`#0A0A0A`). Light mode is an inverted afterthought for accessibility.
2. **Red is Power** — Phantom Red (`#D40000`) is the ONLY accent. Never dilute with other accent colors.
3. **Paper Cutouts** — UI elements float with a red offset shadow underneath, creating stacked-paper physicality.
4. **Sharp & Intentional** — Border-radius is minimal (`2-4px`). Every curve is earned.
5. **Typography as Attitude** — JetBrains Mono for headings (terminal/technical feel), Inter for body (clean readable).
6. **Mask Motif** — The `.phantom-mask` utility creates layered cutout effect with offset red frame.

---

## 2. Quick Start

```html
<!DOCTYPE html>
<html>
<head>
  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600;700;800&display=swap" rel="stylesheet">

  <!-- Design tokens (auto-handles light/dark) -->
  <link rel="stylesheet" href="design-system/references/tokens.css">
</head>
<body>
  <!-- Your UI here — tokens work in both modes automatically -->
</body>
</html>
```

**No JavaScript required.** Dark mode is default. Light mode activates automatically via `@media (prefers-color-scheme: light)`.

---

## 3. Mode System

The design system uses a **single `tokens.css` file** with two themes:

| Aspect | Dark Mode (default) | Light Mode |
|--------|-------------------|------------|
| Theme | `:root` (no media query needed) | `@media (prefers-color-scheme: light)` |
| Page bg | `#0A0A0A` (near-black) | `#F5F5F0` (warm off-white) |
| Card bg | `#121212` | `#FFFFFF` |
| Text | `#FFFFFF` | `#0A0A0A` |
| Primary | `#D40000` | `#B80000` |
| Accent | `#FFFFFF` (white on dark) | `#D40000` (red on light) |
| Shadows | Darker (`rgba(0,0,0,0.4)`) | Lighter (`rgba(0,0,0,0.12)`) |
| Red offset | Always `var(--red-600)` | Same — signature survives light mode |

### Light Mode Details (per mode)

**In light mode:**
- The Phantom Red accent flips from `#D40000` to `#B80000` (darker for contrast on white)
- The `--color-accent` becomes red (since white-on-white is invisible)
- Card backgrounds become `#FFFFFF` with `#DDD` borders
- Text becomes near-black `#0A0A0A` on `#F5F5F0` background
- Red offset shadows persist — they're the brand signature
- Every component specification in this document applies to both modes via CSS custom properties

---

## 4. Color Palette

### Phantom Red Ramp

```
#7A0000  #9C0000  #B80000  #D40000  #E60000  #FF1A1A  #FF5555  #FF8888  #FFCCCC
```

### Core Tokens

| Token | Dark | Light | Usage |
|-------|------|-------|-------|
| `--color-primary` | `#D40000` | `#B80000` | Buttons, links, active states, borders |
| `--color-on-primary` | `#FFFFFF` | `#FFFFFF` | Text on primary backgrounds |
| `--color-secondary` | `#1A1A1A` | `#E8E8E8` | Secondary surfaces |
| `--color-accent` | `#FFFFFF` | `#D40000` | Highlights, secondary emphasis |
| `--surface-page` | `#0A0A0A` | `#F5F5F0` | Page background |
| `--surface-card` | `#121212` | `#FFFFFF` | Cards, containers |
| `--surface-elevated` | `#1A1A1A` | `#FFFFFF` | Modals, dropdowns, popovers |
| `--surface-sunken` | `#050505` | `#EAEAE5` | Deepest backgrounds, table headers |
| `--surface-overlay` | `rgba(0,0,0,0.8)` | `rgba(0,0,0,0.6)` | Modal scrim, overlay |
| `--text-primary` | `#FFFFFF` | `#0A0A0A` | Headings, body text |
| `--text-secondary` | `#D4D4D4` | `#6B6B6B` | Subdued text, descriptions |
| `--text-tertiary` | `#6B6B6B` | `#A1A1A1` | Labels, metadata |
| `--text-disabled` | `#3D3D3D` | `#8A8A8A` | Disabled text |
| `--text-inverse` | `#0A0A0A` | `#FFFFFF` | Text on light backgrounds in dark mode |
| `--text-on-action` | `#FFFFFF` | `#FFFFFF` | Text on action buttons |
| `--text-link` | `#FF1A1A` | `#D40000` | Link text |
| `--border-default` | `#2A2A2A` | `#DDD` | Dividers, input borders |
| `--border-strong` | `#3D3D3D` | `#BBB` | Stronger borders |
| `--border-focus` | `#E60000` | `#E60000` | Focus ring color |
| `--border-inverse` | `rgba(0,0,0,0.3)` | `rgba(255,255,255,0.3)` | Border on dark backgrounds |

### Action Tokens

| Token | Dark | Light |
|-------|------|-------|
| `--action-primary` | `#D40000` | `#B80000` |
| `--action-primary-hover` | `#E60000` | `#D40000` |
| `--action-primary-disabled` | `#7A0000` | `#FF8888` |
| `--action-secondary` | `#2A2A2A` | `#E8E8E8` |
| `--action-secondary-hover` | `#3D3D3D` | `#DDD` |

---

## 5. Typography

| Level | Size | Weight | Line-Height | Letter-Spacing | Font | Usage |
|-------|------|--------|-------------|----------------|------|-------|
| Display | 48px | 700 | 1.0 | -0.02em | JetBrains Mono | Hero titles, main headers |
| H1 | 36px | 700 | 1.1 | -0.01em | JetBrains Mono | Section headers |
| H2 | 28px | 700 | 1.15 | -0.01em | JetBrains Mono | Card titles |
| H3 | 22px | 700 | 1.2 | normal | JetBrains Mono | Sub-section titles |
| Body | 15px | 400 | 1.6 | normal | Inter | Paragraphs, descriptions |
| Small | 13px | 400 | 1.5 | normal | Inter | Secondary info, metadata |
| Caption | 11px | 600 | 1.35 | 0.08em | Inter, UPPERCASE | Labels, timestamps |
| Label | 11px | 700 | 1.2 | 0.12em | Inter, UPPERCASE | Button text, nav items |

**Font Family CSS:**
```css
--font-display: 'JetBrains Mono', 'Fira Code', monospace;
--font-body: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
--font-mono: 'JetBrains Mono', 'Fira Code', monospace;
```

---

## 6. Spacing & Radius

### Spacing Scale
```
4px   8px   12px   16px   24px   32px   48px   64px   96px   128px
```

### Radius
```
sm: 2px    md: 4px    lg: 8px    xl: 12px    full: 9999px
```

---

## 7. Shadows

Shadows are the signature Persona 5 paper-stack effect — a colored bottom offset:

```css
--shadow-sm: 0 2px 0 var(--red-600);                                  /* 2px red */
--shadow-md: 0 4px 0 var(--red-600), 0 6px 12px rgba(0,0,0,0.4);      /* 4px red */
--shadow-lg: 0 8px 0 var(--red-600), 0 12px 24px rgba(0,0,0,0.5);     /* 8px red */
--shadow-xl: 0 12px 0 var(--red-600), 0 20px 40px rgba(0,0,0,0.6);    /* 12px red */
```

In light mode, the black shadow fades (`rgba(0,0,0,0.12)` to `0.2`) but the red offset stays.

---

## 8. Signature CSS Utilities

These three utilities are defined in `tokens.css` and create the Persona 5 visual language:

### `.phantom-mask` — Layered Paper Cutout

Creates a card that appears to float with an offset red frame behind it. This is the P5 menu effect.

```html
<div class="phantom-mask" style="padding:24px;text-align:center;">
  <h2 style="font-family:var(--font-display);color:var(--color-primary);">MASK EFFECT</h2>
  <p style="color:var(--text-secondary);">Content floats above a red offset frame.</p>
</div>
```

**Renders as:** The card has a `2px solid red` border, with a red rectangle offset 6px behind it, creating a layered paper cutout. In light mode, the red offset persists (same `--red-600`).

### `.phantom-stripe` — Diagonal Red Corner

Adds a subtle diagonal red stripe in the top-right corner. Use on hero sections, cards, or any container that needs attitude.

```html
<section class="phantom-stripe" style="padding:24px;border:1px solid var(--border-default);">
  <h2>Content with attitude</h2>
</section>
```

### `.phantom-divider` — Thick Red Rule

A 4px thick red horizontal rule for section separation.

```html
<hr class="phantom-divider">
```

---

## 9. Component Specifications

All components use CSS custom properties. **Never use raw hex values.**

### 9.1 Navbar

```
┌─────────────────────────────────────────────────────────┐
│  PHANTOM    [ EVENTS ] [ SPEAKERS ] [ LOG IN ] [▶ REGISTER ]
│  ▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀  (2px solid red bottom border)
└─────────────────────────────────────────────────────────┘
```

| Property | Token | Value |
|----------|-------|-------|
| Background | `var(--surface-card)` | Dark card surface |
| Bottom border | `2px solid var(--color-primary)` | Signature red line |
| Brand text | `var(--font-display)`, `var(--color-primary)` | JetBrains Mono, 18px, red |
| Nav links | `var(--font-body)`, `var(--text-secondary)` | Inter, Label size, uppercase |
| Active link | `var(--color-primary)` | Red text |
| CTA button | `var(--action-primary)` bg, `var(--text-on-action)` | Red button with shadow |
| Shadow | `var(--shadow-md)` | Red offset bottom |

**In light mode:** Background becomes white, text becomes dark, bottom border stays red.

### 9.2 Hero

```
╔══════════════════════════════════════════════════╗
║  JUNE 15–17, 2026 · BERLIN      ← date label    ║
║                                                   ║
║  PHANTOM SUMMIT '26             ← Display title  ║
║                                                   ║
║  The annual gathering for rebels                 ║
║  and visionaries in computer vision.  ← body      ║
║                                                   ║
║  [▶ REGISTER NOW]  [VIEW SCHEDULE]  ← CTAs       ║
╚══════════════════════════════════════════════════╝
```

| Element | Token | Notes |
|---------|-------|-------|
| Background | `var(--surface-sunken)` | Deepest surface level |
| Decorative | `.phantom-stripe` utility | Red diagonal corner |
| Date label | `var(--text-caption)` size, `var(--color-primary)` | Uppercase, red |
| Headline | `var(--text-display)`, `var(--font-display)` | JetBrains Mono 48px 700 |
| Subtitle | `var(--text-body)`, `var(--text-secondary)` | Inter 15px |
| Primary CTA | `var(--action-primary)` bg + `var(--shadow-md)` | Red button with shadow |
| Secondary CTA | transparent bg + `1px solid var(--border-inverse)` | Ghost button |

### 9.3 Card

```
┌──────────────────────┐
│  KEYNOTE              │  ← label (Caption/uppercase)
│                       │
│  Dr. Sarah Chen      │  ← title (H3, JetBrains Mono)
│                       │
│  Description text     │  ← body (Inter, text-secondary)
│  here.                │
│                       │
│  ● Confirmed          │  ← badge
└──────────────────────┘
```

| Property | Token | Notes |
|----------|-------|-------|
| Background | `var(--surface-card)` | Dark surface (white in light) |
| Border | `1px solid var(--border-default)` | Subtle |
| Radius | `var(--radius-md)` | 4px |
| Shadow | `var(--shadow-sm)` | 2px red offset |
| Top accent | `3px solid var(--color-primary)` or `.phantom-mask` | Red top border or full mask |
| Label | `var(--text-label)` size, `var(--color-primary)` | Uppercase, red |
| Title | `var(--text-h3)`, `var(--font-display)` | JetBrains Mono 22px |
| Body | `var(--text-body)`, `var(--text-secondary)` | Inter 15px |

**Variants:** default (border+shadow), elevated (`.phantom-mask`), brand (primary bg, white text)

### 9.4 Button

| Variant | Background | Text | Border | Hover |
|---------|-----------|------|--------|-------|
| **Primary** | `var(--action-primary)` | `var(--text-on-action)` | none | `var(--action-primary-hover)` |
| **Secondary** | `var(--action-secondary)` | `var(--text-primary)` | none | `var(--action-secondary-hover)` |
| **Outline** | transparent | `var(--color-primary)` | `1.5px solid var(--color-primary)` | bg fills on hover |
| **Soft** | `var(--state-success-bg)` | `var(--state-success)` | none | brighter bg |
| **Ghost** | transparent | `var(--color-primary)` | none | underline on hover |
| **Disabled** | `var(--action-primary-disabled)` | `var(--text-disabled)` | none | cursor `not-allowed` |

**Sizes:**

| Size | Padding | Font | Radius |
|------|---------|------|--------|
| XS | `4px 12px` | Label (11px) | sm (2px) |
| SM | `6px 16px` | Label (11px) | sm (2px) |
| MD | `10px 24px` | Label (11px) | md (4px) |
| LG | `14px 32px` | Label (11px) | md (4px) |
| XL | `16px 40px` | Small (13px) | lg (8px) |

All buttons: uppercase text, `0.12em` letter-spacing, `700` weight, `150ms` transitions.

### 9.5 Input

| State | Border | Background | Text | Extra |
|-------|--------|------------|------|-------|
| Default | `var(--border-default)` | `var(--surface-card)` | `var(--text-primary)` | — |
| Focus | `var(--border-focus)` | `var(--surface-card)` | `var(--text-primary)` | ring `color-mix(in srgb, var(--border-focus) 25%, transparent)` |
| Error | `var(--state-danger)` | `var(--state-danger-bg)` | `var(--state-danger)` | + helper text below |
| Disabled | `var(--border-default)` | `var(--surface-sunken)` | `var(--text-disabled)` | cursor `not-allowed` |

- Radius: `var(--radius-md)` (4px)
- Label: 11px, uppercase, `0.12em` letter-spacing

### 9.6 Badge

| Variant | Background | Text |
|---------|-----------|------|
| Success | `var(--state-success-bg)` | `var(--state-success)` |
| Warning | `var(--state-warning-bg)` | `var(--state-warning)` |
| Danger | `var(--state-danger-bg)` | `var(--state-danger)` |
| Info | `var(--state-info-bg)` | `var(--state-info)` |
| Neutral | `var(--surface-elevated)` | `var(--text-secondary)` |

- Radius: `var(--radius-full)`
- Font: 10px, 700 weight, `0.06em` letter-spacing, uppercase

### 9.7 Alert

| Type | Left Border | Background | Icon + Text Color |
|------|------------|------------|-------------------|
| Success | `3px solid var(--state-success)` | `var(--state-success-bg)` | `var(--state-success)` |
| Warning | `3px solid var(--state-warning)` | `var(--state-warning-bg)` | `var(--state-warning)` |
| Danger | `3px solid var(--state-danger)` | `var(--state-danger-bg)` | `var(--state-danger)` |
| Info | `3px solid var(--state-info)` | `var(--state-info-bg)` | `var(--state-info)` |

Layout: icon(20px circle) + bold label + body text. Radius: 4px.

### 9.8 Toggle / Switch

| State | Track | Knob |
|-------|-------|------|
| ON | `var(--color-primary)` | `#FFFFFF`, right position |
| OFF | `var(--border-default)` | `#FFFFFF`, left position |

Dimensions: `40×22px` track, `18px` knob. Radius: `11px` (pill).

### 9.9 Table

| Element | Style |
|---------|-------|
| Header | bg `var(--surface-sunken)`, text `var(--text-secondary)`, 11px uppercase, `0.05em` LS |
| Row | border-bottom `1px solid var(--border-default)` |
| Hover | bg `var(--surface-elevated)` |
| Status | Use badge component |

### 9.10 Stepper

| Step | Circle | Text | Connector |
|------|--------|------|-----------|
| Completed | `var(--color-primary)` bg, checkmark icon | `var(--text-secondary)` | `var(--color-primary)` line |
| Current | `var(--color-primary)` bg, step number (bold) | `var(--text-primary)` bold | `var(--border-default)` line |
| Upcoming | `var(--border-default)` bg | `var(--text-secondary)` | `var(--border-default)` line |

Circle: `24×24px`, Connector: `32×2px`, Font: `10px` 700.

### 9.11 Toast / Snackbar

| Property | Token |
|----------|-------|
| Background | `var(--surface-elevated)` |
| Border | `1px solid var(--border-default)` |
| Shadow | `var(--shadow-lg)` |
| Radius | `var(--radius-md)` |
| Accent dot | `8px`, `var(--color-primary)` or `var(--state-success)` |
| Action | Label font, `var(--color-primary)` color |

### 9.12 All Components

navbar · hero · section · sidebar · footer · tabs · breadcrumb · pagination · stepper ·
card · list · table · media · text · button · input · checkbox · select · search · toggle ·
alert · toast · modal · tooltip · badge · avatar

---

## 10. Semantic States

| Token | Dark | Light | Meaning |
|-------|------|-------|---------|
| `--state-success` | `#22C55E` | `#16A34A` | Green — confirmed, available, completed |
| `--state-success-bg` | `rgba(34,197,94,0.12)` | lighter green bg |
| `--state-warning` | `#F59E0B` | `#D97706` | Amber — caution, limited, attention |
| `--state-warning-bg` | `rgba(245,158,11,0.12)` | lighter amber bg |
| `--state-danger` | `#FF1A1A` | `#DC2626` | Red — error, sold out, destructive |
| `--state-danger-bg` | `rgba(255,26,26,0.12)` | lighter red bg |
| `--state-info` | `#3B82F6` | `#2563EB` | Blue — information, help |
| `--state-info-bg` | `rgba(59,130,246,0.12)` | lighter blue bg |

---

## 11. Motion & Animation

| Aspect | Value |
|--------|-------|
| Micro-interactions | `150-300ms`, ease-out |
| Page transitions | `400-600ms`, power2.inOut with overlay |
| Scroll reveals | Staggered entries, `300-450ms`, stagger `0.06s` |
| Hover states | `150ms` ease, color or opacity shift |
| Reduced motion | Respect `prefers-reduced-motion` — disable all animations |

**GSAP Pattern (Complex Page Transition):**
```js
const state = Flip.getState('.hero-image');
navigate();
Flip.from(state, {
  duration: 0.6,
  ease: 'expo.inOut',
  absolute: true,
  zIndex: 100
});
```

---

## 12. Anti-Patterns

| Don't | Why |
|-------|-----|
| Gradients | P5 is flat, sharp, high-contrast. No gradients anywhere. |
| Purple/pink/neon | Red is the ONLY accent color. Never introduce others. |
| Large border-radius | Keep 2-8px max. Curves must be earned. |
| Emoji as icons | Use Lucide or Heroicons SVG icons only. |
| Center everything | Left-align with asymmetric balance (P5 layout style). |
| Soft/blurry shadows | Hard red offset shadow IS the brand. |
| Raw hex in components | Every color must reference a CSS custom property. |
| Ignore light mode | Both modes must be tested. Red offset survives in both. |

---

## 13. File Map

```
design-system/
├── SKILL.md                        <- Design system overview (this document's short version)
├── DESIGN.md                        <- THIS FILE — full design system documentation
├── design-system.json               <- Machine-readable tokens for AI consumption
├── assets/
│   ├── font-import.html             <- Copy-paste font import HTML
│   └── tailwind.config.js           <- Tailwind v3+ configuration
├── references/
│   ├── tokens.css                   <- CSS custom properties (single file, both modes)
│   ├── tokens.md                    <- Token documentation
│   └── components.md                <- Component specifications
└── pics/                            <- Reference images
```

---

## 14. Prototype Instructions (for AI)

To build a prototype from this design system:

1. **Import `tokens.css`** — this single file provides all colors, spacing, typography, shadows, and utilities for both dark and light modes automatically.
2. **Import fonts** — JetBrains Mono (headings) and Inter (body) from Google Fonts using the snippet in `font-import.html`.
3. **Reference tokens, not hex values** — every color must use `var(--token-name)`. Never hardcode `#D40000` or any other hex value.
4. **Use the label convention** — all button text, nav links, badges, table headers, and form labels must be UPPERCASE with `letter-spacing: 0.08-0.12em`.
5. **Apply the red offset shadow** — every card, button, and elevated element should use `var(--shadow-sm)` or `var(--shadow-md)` to get the signature red bottom edge.
6. **Use `.phantom-mask` for hero elements** — the layered cutout effect is the Persona 5 signature.
7. **Test both themes** — toggle `prefers-color-scheme` in dev tools to verify light mode. The red offset shadows must render in both modes.
8. **Semantic colors are not grays** — `--state-success` is green, `--state-warning` is amber, `--state-danger` is red, `--state-info` is blue. The old AI system used grays for all of these — do not repeat that mistake.
9. **JetBrains Mono for all headings** — display, H1, H2, H3 all use JetBrains Mono 700 weight. Inter for body text only.
10. **No decorative animation** — every animation must convey meaning (hover state, loading, transition). Respect `prefers-reduced-motion`.

---

> *Phantom Works · Persona 5 Inspired Design System · 2026-07-17*
