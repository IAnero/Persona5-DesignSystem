# Persona5-DesignSystem

Persona 5 inspired design system for websites and event pages.

## Quick links

- [Full Design System (`./DESIGN.md`)](DESIGN.md) — tokens, components, light/dark mode, anti-patterns
- [Preview — Dark & Light Mode (`./ui-kit-preview.html`)](ui-kit-preview.html)
- [Light Mode Preview (`./ui-kit-preview-light.html`)](ui-kit-preview-light.html) — with live toggle
- [CSS Tokens (`./design-system/references/tokens.css`)](design-system/references/tokens.css) — single file, both modes
- [Machine-readable tokens (`./design-system/design-system.json`)](design-system/design-system.json)

## Stack

- **Fonts:** JetBrains Mono (headings) + Inter (body)
- **CSS:** Custom properties via `tokens.css` — no framework required
- **Mode:** Dark-first with `@media (prefers-color-scheme: light)` auto-switch
- **Signature:** Red offset shadows, `.phantom-mask` paper cutout, `.phantom-stripe` diagonal accent
