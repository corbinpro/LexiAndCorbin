# Bridal Shower Invitation Site — Design Spec
Date: 2026-05-17

## Overview
Two-page static site hosted on GitHub Pages at https://corbinpro.github.io/LexiAndCorbin/. Displays a bridal shower invitation image with RSVP and registry links.

## Pages

### index.html
- Single HTML file with inline `<style>` block
- Page background: light yellow (`#fef9e7`) to complement the gingham invitation
- Invitation image (`images/80percent.png`) centered, `width: 100%`, `max-width: 420px`
- Below image: two links side by side, centered — **RSVP** and **Registry**
- Link styles: Dancing Script (Google Fonts), `font-size: 1.6rem`, color `#6ab0e0`, no underline, hover underline
- RSVP href: `#placeholder`
- Registry href: `registry.html`

### registry.html
- Single HTML file with inline `<style>` block
- Registry card image (`images/registry_page.png`) centered, same sizing as invitation (`width: 100%`, `max-width: 420px`)
- Image used as a positioned container; two links overlaid inside the white interior area
- Links stacked vertically, centered: **Amazon Registry** and **Target Registry**
- Same font/color as index.html links (Dancing Script, `#6ab0e0`, `font-size: 1.6rem`)
- Amazon href: `https://www.amazon.com/wedding/guest-view/2X91PQO64QI1T`
- Target href: `https://www.target.com/gift-registry/gift/lexi-and-corbin`

## Typography
- Script/cursive: **Dancing Script** (Google Fonts) — matches invitation's handwritten text style
- All link text uses this font

## Colors
- Blue: `#6ab0e0` (matches invitation bow and script text)
- Page background: `#fef9e7` (warm white/light yellow)

## Constraints
- Mobile-first, no JS
- Inline styles only (no separate CSS file)
- No external image dependencies beyond Google Fonts
