# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Dutch Trading Boys** is a single-page marketing website for a Forex & Crypto trading community. The entire application lives in a single `index.html` file — no build tools, no package manager, no framework. Deploy by serving `index.html` directly on any static host.

## Development

Since there is no build system, open `index.html` directly in a browser or use any static file server:

```bash
python3 -m http.server 8080
# or
npx serve .
```

There are no lint, test, or build commands.

## Architecture

Everything is inline in `index.html`:

- **CSS** (~1,500 lines, inline `<style>`) — CSS custom properties for theming (gold `#D4AF37` on black), responsive breakpoints at 560px / 860px / 980px.
- **JavaScript** (vanilla, no frameworks) — multiple independent canvas-based animations and UI modules, each self-contained inside `index.html`.
- **Fonts** — Cormorant Garamond (display), Inter (body), JetBrains Mono (code), loaded from Google Fonts.

### Page Sections (by anchor)

| Anchor | Content |
|--------|---------|
| `#home` | Hero with 3D depth canvas background |
| `#about` / `#features` | Community features, 4-column card grid |
| `#bot` | DTB Cash Bot showcase with radial gauge canvas |
| `#pakketten` | Pricing packages (Bot / Academy / Coaching) |
| `#resultaten` | Animated stat counters (scroll-triggered) |
| `#testimonials` | Auto-advancing carousel, 6 slides |
| `#booking` | Calendly embed (`https://calendly.com/dutchtradingboys/30min`) |
| `#faq` | Accordion FAQ |

### Canvas Animations

Five separate `<canvas>` elements drive the visual effects:
1. **Starfield** — ambient particle background
2. **3D depth grid** — hero section perspective grid
3. **Network nodes** — about section
4. **Bot gauge** — radial dial with ticks for the DTB Cash Bot
5. **Final CTA canvas** — contact section ambient effect

All animations use `requestAnimationFrame` and respect `prefers-reduced-motion`.

### Pricing Placeholders

The pricing section contains placeholder values (`€XX`, `€XXX`). Update these directly in `index.html` when real prices are set.
