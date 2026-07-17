# Phantom Works — Component Specifications

> Persona 5 inspired UI components. All colors reference CSS custom properties from `tokens.css`.
> Every component must use tokens — never raw hex values.

---

## Navbar

```
┌──────────────────────────────────────────────────────┐
│  PHANTOM WORKS  [ EVENTS ] [ SPEAKERS ] [ LOG IN ] [▶ REGISTER ]
└──────────────────────────────────────────────────────┘
```

| Property | Token | Notes |
|----------|-------|-------|
| Background | `var(--surface-card)` | Dark card surface |
| Bottom border | `2px solid var(--color-primary)` | Signature red bottom line |
| Brand text | `var(--font-display)`, `var(--color-primary)` | JetBrains Mono, red |
| Nav links | `var(--text-secondary)`, uppercase | 11px, 0.12em LS |
| Active link | `var(--color-primary)` | Red highlight |
| CTA button | bg `var(--color-primary)`, text `var(--color-on-primary)` | Red button |
| Shadow | `var(--shadow-md)` | Red offset bottom |

**States:** transparent, solid (default), blur

---

## Hero

```
╔═══════════════════════════════════════════════════╗
║  JUNE 15–17, 2026 · BERLIN                        ║
║                                                    ║
║  PHANTOM                                         ║
║  SUMMIT  2026                                     ║
║                                                    ║
║  The annual gathering for rebels and              ║
║  visionaries in computer vision.                  ║
║                                                    ║
║  [▶ REGISTER NOW]  [VIEW SCHEDULE]                ║
╚═══════════════════════════════════════════════════╝
```

| Element | Token | Notes |
|---------|-------|-------|
| Background | `var(--surface-sunken)` | Deepest black |
| Decorative | `.phantom-stripe` utility | Red diagonal in corner |
| Date/location label | `var(--text-caption)` size, `var(--text-secondary)` | UPPERCASE, wide LS |
| Headline | `var(--text-display)`, `var(--font-display)` | JetBrains Mono, 48px |
| Subtitle | `var(--text-body)`, `var(--text-secondary)` | 15px, lh 1.6 |
| Primary CTA | `var(--action-primary)` bg + shadow | Red button |
| Secondary CTA | `1px solid var(--border-inverse)` | Ghost button |

---

## Card

```
┌──────────────────────┐
│  KEYNOTE              │  ← label tag, uppercase
│                       │
│  Dr. Sarah Chen      │  ← H3, JetBrains Mono
│                       │
│  "Vision              │
│  Transformers..."     │  ← body text
│                       │
│  ● Confirmed          │  ← status badge
└──────────────────────┘
```

| Property | Token | Notes |
|----------|-------|-------|
| Background | `var(--surface-card)` | Dark surface |
| Border | `1px solid var(--border-default)` | Subtle gray border |
| Radius | `var(--radius-md)` | 4px |
| Shadow | `var(--shadow-sm)` | Red offset (2px) |
| Top accent | `3px solid var(--color-primary)` OR `.phantom-mask` | Red top border or full mask |
| Title | `var(--text-h2)` / `var(--text-h3)`, `var(--font-display)` | JetBrains Mono |
| Body | `var(--text-body)`, `var(--text-secondary)` | Inter |

**Variants:** default, elevated (`.phantom-mask`), brand (primary bg)

---

## Button

| Variant | Background | Text | Border | Hover |
|---------|-----------|------|--------|-------|
| Primary | `var(--action-primary)` | `var(--text-on-action)` | none | `var(--action-primary-hover)` |
| Secondary | `var(--action-secondary)` | `var(--text-primary)` | none | `var(--action-secondary-hover)` |
| Outline | transparent | `var(--color-primary)` | `1.5px solid` | bg fill on hover |
| Ghost | transparent | `var(--color-primary)` | none | underline |
| Disabled | `var(--action-primary-disabled)` | `var(--text-disabled)` | none | cursor not-allowed |

**Sizes:**

| Size | Padding | Font | Radius |
|------|---------|------|--------|
| XS | 4px 12px | Label (11px) | sm (2px) |
| SM | 6px 16px | Label (11px) | sm (2px) |
| MD | 10px 24px | Caption (11px) | md (4px) |
| LG | 14px 32px | Caption (11px) | md (4px) |
| XL | 16px 40px | Small (13px) | lg (8px) |

All buttons: uppercase text, 0.12em letter-spacing, 700 weight, 150ms transitions.

---

## Input

| State | Border | Background | Text | Extra |
|-------|--------|------------|------|-------|
| Default | `var(--border-default)` | `var(--surface-card)` | `var(--text-primary)` | — |
| Focus | `var(--border-focus)` | `var(--surface-card)` | `var(--text-primary)` | ring `var(--border-focus)` 25% opacity |
| Error | `var(--state-danger)` | `var(--state-danger-bg)` | `var(--state-danger)` | + helper text below |
| Disabled | `var(--border-default)` | `var(--surface-sunken)` | `var(--text-disabled)` | cursor not-allowed |

Radius: `var(--radius-md)` (4px). Label: 11px, uppercase, 0.12em LS.

---

## Badge

| Variant | Background | Text |
|---------|-----------|------|
| Success | `var(--state-success-bg)` | `var(--state-success)` |
| Warning | `var(--state-warning-bg)` | `var(--state-warning)` |
| Danger | `var(--state-danger-bg)` | `var(--state-danger)` |
| Info | `var(--state-info-bg)` | `var(--state-info)` |
| Neutral | `var(--surface-elevated)` | `var(--text-secondary)` |

Radius: `var(--radius-full)`. Font: 11px, 600 weight, 0.06em LS.

---

## Alert

| Type | Left Border | Background | Icon Text Color |
|------|------------|------------|-----------------|
| Success | `3px solid var(--state-success)` | `var(--state-success-bg)` | `var(--state-success)` |
| Warning | `3px solid var(--state-warning)` | `var(--state-warning-bg)` | `var(--state-warning)` |
| Danger | `3px solid var(--state-danger)` | `var(--state-danger-bg)` | `var(--state-danger)` |
| Info | `3px solid var(--state-info)` | `var(--state-info-bg)` | `var(--state-info)` |

Layout: icon(20px circle) + bold label + body text.

---

## Toggle / Switch

| State | Track | Knob |
|-------|-------|------|
| ON | `var(--color-primary)` | `#FFFFFF` |
| OFF | `var(--border-default)` | `#FFFFFF` |

Dimensions: 40×22px track, 18px knob. Radius: 11px (pill).

---

## Table

| Element | Style |
|---------|-------|
| Header | bg `var(--surface-sunken)`, text `var(--text-secondary)` 11px uppercase |
| Row | border-bottom `1px solid var(--border-default)` |
| Hover | bg `var(--surface-elevated)` |
| Status badge | Use `<span class="badge-{variant}">` |

---

## Stepper

| Step | Circle | Label | Connector |
|------|--------|-------|-----------|
| Completed | `var(--color-primary)` bg, checkmark icon | `var(--text-secondary)` | `var(--color-primary)` line |
| Current | `var(--color-primary)` bg, step number | `var(--text-primary)` bold | `var(--border-default)` line |
| Upcoming | `var(--border-default)` bg | `var(--text-secondary)` | `var(--border-default)` line |

---

## All Components

navbar · hero · section · sidebar · footer · tabs · breadcrumb · pagination · stepper ·
card · list · table · media · text · button · input · checkbox · select · search · toggle ·
alert · toast · modal · tooltip · badge · avatar
