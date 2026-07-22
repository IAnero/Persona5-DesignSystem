# M4Event Design System

> Brutalist · Dark-first · Red/black · High contrast · Zero radius · Monospace
> Archivo Black (display) + JetBrains Mono (body) · Flat surfaces · No curves · No shadows
> Compiled from actual CSS tokens · 2026-07-22

---

## 1. Design DNA

| Trait | Value |
|-------|-------|
| **Vibe** | Brutalist terminal — raw, monospaced, high-impact |
| **Colors** | Near-black `#0B0B0B`, Signal Red `#E61919`, off-white `#ECECEA` |
| **Typography** | Archivo Black (display headings) + JetBrains Mono (body) + IBM Plex Mono (mono fallback) |
| **Shapes** | Zero border-radius everywhere — sharp, intentional, uncompromising |
| **Depth** | Flat — no shadows, no paper cutouts, no offset effects |
| **Labels** | Always UPPERCASE with `0.12em` letter-spacing |
| **Motion** | Fast (`150-300ms`), simple easing |
| **Icons** | Inline SVG only — never emoji, never icon fonts |

### Core Principles

1. **Dark-First** — Default is near-black (`#0B0B0B`). No light mode.
2. **Red is Power** — Signal Red (`#E61919`) is the ONLY accent. Never dilute with other accent colors.
3. **Brutalist Flat** — Zero radius. Zero shadows. No curves, no gradients, no glassmorphism.
4. **Monospace Everything** — Body text is JetBrains Mono. Headings are Archivo Black. No sans-serif body.
5. **Typography as Attitude** — Archivo Black for massive display impact, JetBrains Mono for readable body.
6. **All Caps Labels** — Every label, button, badge, and nav item is UPPERCASE with tracking.

---

## 2. CSS Tokens (Copy-Paste Ready)

### 2.1 Core Tokens — `:root`

```css
:root {
  /* === Colors === */
  --color-primary: #E61919;
  --color-primary-hover: #FF2A2A;
  --color-on-primary: #0B0B0B;

  /* === Surfaces === */
  --surface-page: #0B0B0B;
  --surface-card: #131312;
  --surface-elevated: #1A1A19;
  --surface-sunken: #050505;

  /* === Text === */
  --text-primary: #ECECEA;
  --text-secondary: #9F9F9C;
  --text-tertiary: #6A6A67;
  --text-disabled: #3A3A36;

  /* === Borders === */
  --border-default: #2A2A27;
  --border-strong: #3A3A36;
  --border-focus: #E61919;

  /* === Actions === */
  --action-primary: #E61919;
  --action-primary-hover: #FF2A2A;
  --action-secondary: #1A1A19;
  --action-secondary-hover: #2A2A27;

  /* === Semantic States === */
  --state-success: #4AF626;
  --state-success-bg: rgba(74,246,38,0.12);
  --state-warning: #E0A819;
  --state-warning-bg: rgba(224,168,25,0.12);
  --state-danger: #E61919;
  --state-danger-bg: rgba(230,25,25,0.12);
  --state-info: #4AF626;
  --state-info-bg: rgba(74,246,38,0.12);

  /* === Typography === */
  --font-display: 'Archivo Black', 'Inter', sans-serif;
  --font-body: 'JetBrains Mono', 'IBM Plex Mono', ui-monospace, monospace;
  --font-mono: 'JetBrains Mono', 'IBM Plex Mono', ui-monospace, monospace;
  --font-sans: 'JetBrains Mono', 'IBM Plex Mono', ui-monospace, monospace;

  /* === Radius (always zero — brutalist) === */
  --radius-sm: 0;
  --radius-md: 0;
  --radius-lg: 0;
  --radius-full: 0;

  /* === Layout === */
  --container: 1120px;
  --gutter: 32px;
  --status-bar-height: 54px;
  --home-indicator-height: 34px;
}
```

### 2.2 Base Reset + Body

```css
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { -webkit-text-size-adjust: 100%; }
body {
  background: var(--surface-page);
  color: var(--text-primary);
  font-family: var(--font-body);
  font-size: 15px;
  line-height: 1.6;
  -webkit-font-smoothing: antialiased;
  overflow-x: hidden;
}
img, svg { display: block; max-width: 100%; }
a { color: inherit; text-decoration: none; }
button { font: inherit; cursor: pointer; border: none; background: none; }
h1, h2, h3, h4 { font-family: var(--font-display); text-wrap: balance; }
```

---

## 3. Typography

| Level | Size | Weight | Line-Height | Letter-Spacing | Font | Usage |
|-------|------|--------|-------------|----------------|------|-------|
| Display | `36px` mobile / `48px` desktop | 700 (Archivo Black) | 1.0 | -0.02em | Archivo Black | Hero titles |
| H1 | `28px` mobile / `36px` desktop | 700 | 1.1 | -0.01em | Archivo Black | Section headers |
| H2 | `22px` | 700 | 1.15 | normal | Archivo Black | Card titles |
| H3 | `17px` | 700 | 1.2 | normal | Archivo Black | Sub-section titles |
| Body | `15px` | 400 | 1.6 | normal | JetBrains Mono | Paragraphs |
| Small | `13px` | 400 | 1.5 | normal | JetBrains Mono | Secondary info |
| Caption | `11px` | 600 | 1.35 | `0.08em` | JetBrains Mono, UPPERCASE | Labels, timestamps |
| Label | `11px` | 700 | 1.2 | `0.12em` | JetBrains Mono, UPPERCASE | Button text, nav items |

---

## 4. Spacing

### Mobile (iPhone 15 Pro — 390px frame)

| Context | Value |
|---------|-------|
| Screen content padding | `0 24px 24px` |
| Card padding | `20px` |
| Card-to-card gap | `16px` |
| Section margin-bottom | `28px` |
| Sub-section margin-bottom | `20px` |
| Inline element gaps | `8px` |
| Input padding | `16px` |
| Row/item padding | `16px` |
| Bottom nav height | `80px` (incl. home indicator) |

### Hard Rules

- No border-radius — zero everywhere (`--radius-*: 0`)
- No `box-shadow` — flat surfaces only
- No `margin-top` on first child — use margin-bottom on the element above

---

## 5. Components

### 5.1 Buttons

| Variant | Background | Text | Border | Hover |
|---------|-----------|------|--------|-------|
| Primary | `var(--action-primary)` | `var(--color-on-primary)` | none | `var(--action-primary-hover)` |
| Secondary | transparent | `var(--text-primary)` | `1px solid var(--border-strong)` | bg fills |
| Ghost | transparent | `var(--color-primary)` | none | underline |

**Standard sizing:**
- Default: `14px 24px`, Label (11px), ALL CAPS
- SM: `6px 16px`, Label (11px), ALL CAPS
- LG: `16px 40px`, Small (13px), ALL CAPS

**All buttons:** uppercase text, `0.12em` letter-spacing, `700` weight, `150ms` transitions, `border-radius: 0`.

### 5.2 Cards

| Property | Token |
|----------|-------|
| Background | `var(--surface-card)` |
| Border | `1px solid var(--border-default)` |
| Radius | `0` |
| Shadow | none |
| Padding | `20px` |
| Title | `var(--font-display)`, H3 size, 700 |

### 5.3 Inputs

| State | Border | Background |
|-------|--------|------------|
| Default | `1px solid var(--border-default)` | `var(--surface-card)` |
| Focus | `2px solid var(--border-focus)` | `var(--surface-card)` |
| Error | `2px solid var(--state-danger)` | `var(--state-danger-bg)` |

**No box-shadow on focus** — use `border-width: 2px` only.

### 5.4 Badges & Tags

```css
.badge, .tag {
  border-radius: 0;
  font-family: var(--font-mono);
  padding: 4px 10px;
  font-size: 10px;
  font-weight: 700;
  letter-spacing: 0.06em;
  text-transform: uppercase;
}
```

### 5.5 Toggle / Switch

| State | Track | Knob |
|-------|-------|------|
| ON | `var(--color-primary)` | `#FFFFFF`, right |
| OFF | `var(--border-default)` | `#FFFFFF`, left |

Dimensions: `44x24px` track, `18px` knob. The override CSS (applied in assembled viewer) adds `border-radius: 12px` for pill shape. Base design uses zero radius.

---

## 6. Mobile Screen Architecture

### iPhone 15 Pro Frame

```css
.iphone-frame {
  width: 390px;
  background: var(--surface-page);
  border: 1px solid var(--border-default);
  overflow: hidden;
  position: relative;
}

.status-bar {
  height: 54px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 32px;
  font-family: var(--font-body);
  font-size: 14px;
  font-weight: 600;
  position: relative;
}

.dynamic-island {
  position: absolute;
  top: 11px;
  left: 50%;
  transform: translateX(-50%);
  width: 120px;
  height: 33px;
  background: #000;
  border-radius: 20px;
}

.screen-content {
  min-height: 680px;
  padding: 0 24px 24px;
}

.home-indicator {
  height: 34px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.home-indicator .bar {
  width: 130px;
  height: 5px;
  background: var(--border-strong);
}
```

### Bottom Navigation

```css
.bottom-nav {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 80px;
  background: var(--surface-card);
  border-top: 1px solid var(--border-default);
  display: flex;
  align-items: flex-start;
  padding-top: 10px;
  justify-content: space-around;
  z-index: 50;
}
.bottom-nav .nav-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  color: var(--text-tertiary);
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 0.06em;
  text-transform: uppercase;
}
.bottom-nav .nav-item.active {
  color: var(--color-primary);
}
```

---

## 7. Brutalist Override System

The design uses brutally enforced `!important` overrides to strip all curves:

```css
/* All border-radius zero */
[style*="border-radius"] { border-radius: 0 !important; }

/* Core elements */
.card, .event-card, .stat-box, .meta-item,
.btn-primary, button.btn-primary, a.btn-primary,
.badge, .tag,
input, textarea, select, .input-field, .search-bar input,
.avatar, .notif-dot, .notif-count,
.progress-bar, .progress-fill,
.step-dot, .message-bubble,
.icon-circle, .icon-circle-sm,
.bottom-nav-item, .nav-item,
.toggle, .filter-option,
.phone, .phone-frame, .iphone-frame,
.home-indicator .bar, .home-indicator > div {
  border-radius: 0 !important;
}

/* Shadows stripped */
.card, .event-card, .stat-box, .meta-item {
  box-shadow: none !important;
}
```

---

## 8. Icons — Inline SVG Only

**Rule: No emoji. No icon fonts. Only inline SVG.**

All icons use `currentColor` fill/stroke to inherit parent text color.

### Common Icons

| Icon | Use |
|------|-----|
| Home | Bottom nav |
| Search | Search screens |
| Calendar | Event dates |
| Ticket | Ticketing |
| Camera | Photo wall |
| Bell | Notifications |
| User | Profile |
| Settings | Settings |
| Shield | Security/Privacy |
| Heart | Likes |
| Message | Comments |
| Clock | Upcoming |
| Star | Featured |
| Arrow Left | Back |
| X | Close |
| Check | Checkmark |
| Dollar | Payment/Price |
| Lock | Auth |
| Mail | Email |
| Edit | Edit Profile |
| Share | Share |
| Map Pin | Location |

---

## 9. Anti-Patterns

| Don't | Why |
|-------|-----|
| Gradients | Brutalist is flat, high-contrast. No gradients anywhere. |
| Border-radius > 0 | Zero radius is the brand. |
| Emoji as icons | Use inline SVG only. |
| Soft/blurry shadows | No shadows at all. Flat surfaces. |
| box-shadow on focus | Use `border-width: 2px` only. |
| Inter, sans-serif body | Body must be JetBrains Mono. |
| Paper cutout / offset shadows | Not used. Zero depth. |
| Glassmorphism / backdrop-filter | Never. |
| Light mode | Dark-first only. No light mode. |
| Purple/blue/cyan accents | Red (`#E61919`) is the ONLY accent. |
| Raw hex in components | Every color references a CSS custom property. |

---

## 10. Screen File Map

| File | Screens | Content |
|------|---------|---------|
| `m4event-landing.html` | Landing page | Hero, Features, Steps, CTA |
| `m4event-auth.html` | 10 screens | Splash, Welcome, Login, Register, Forgot Password, Email Verification, Account Created, Loading, Error, Success, Empty |
| `m4event-discovery.html` | 10 screens | Home, Search, Results, Categories, Featured, Nearby, Upcoming, Recommendations, Filters, Empty |
| `m4event-screens-part1.html` | 11 screens | Event Detail, Gallery, Participants, Organizers, Partners, Buy Ticket, Checkout, Payment Confirmation, My Ticket, My Tickets, Ticket Details |
| `m4event-manage.html` | 10 screens | Create Steps 1-5, My Events, Dashboard, Analytics, Revenue, Activity |
| `m4event-social.html` | 7 screens | Photo Wall, Upload, Photo Detail, Likes, Comments, Live Feed, Notifications, Activity Feed |
| `m4event-final.html` | 18 screens | Profile, Edit, Settings, Notifications, Privacy, Security, Help, About, Partner Dashboard, Admin Overview, Users, Events Manage, Reports, Loading, Empty, Success, Error, 404 |

---

## 11. Font Import

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Archivo+Black&family=JetBrains+Mono:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

---

## 12. M4Event Product Context

- **Product:** M4Event — event management mobile app
- **Company:** M4Vision
- **Target audience:** Event organizers, attendees, partners
- **Platform:** Mobile-first (iOS/Android concepts), responsive web viewer
- **Features:** Create events, Ticketing, QR Tickets, Dashboard, Photo Wall, Live Sharing, Likes/Comments, Analytics, Partner Management

---

## 13. Checklist (P0 — must pass on every artifact)

- [ ] All colors use CSS custom properties — no raw hex outside `:root`
- [ ] Display headings use `var(--font-display)` (Archivo Black)
- [ ] Body text uses JetBrains Mono (`var(--font-body)`)
- [ ] All labels are UPPERCASE with `0.12em` letter-spacing
- [ ] No emoji anywhere — only inline SVG icons
- [ ] No gradients anywhere — flat surfaces only
- [ ] No `box-shadow` or `backdrop-filter` (except Dynamic Island hardware)
- [ ] All `border-radius: 0` — no curves
- [ ] Card padding is always `20px`
- [ ] Button padding is always `14px 24px` (default) or `6px 16px` (sm)
- [ ] Screen content padding is always `0 24px 24px`
- [ ] Red (`#E61919`) is the ONLY accent color
- [ ] No invented metrics or filler copy
- [ ] Every interactive element has visible states (hover, active, disabled)
- [ ] No light mode — dark mode only

---

> *M4Event Design System · Actual CSS Tokens · 2026-07-22*
