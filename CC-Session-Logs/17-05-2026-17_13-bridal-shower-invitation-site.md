# Session Log: 17-05-2026 17:13 - bridal-shower-invitation-site

## Quick Reference (for AI scanning)
**Confidence keywords:** bridal-shower, invitation, HTML, CSS, mobile-first, GitHub-Pages, Canva, PNG-buttons, aspect-ratio, ghost-pulse-animation, media-query, preload, RSVP, registry, Lexi-and-Corbin
**Projects:** LexiAndCorbin (https://corbinpro.github.io/LexiAndCorbin/)
**Outcome:** Built and deployed a two-page mobile-first invitation site with proportionally-scaling card, overlaid PNG buttons, ghost pulse animation, and Google Forms RSVP.

## Decisions Made
- **Option A (single HTML file w/ inline styles)** chosen over separate CSS files — user preference for simplicity.
- **Replaced text links with Canva PNG button images** to preserve exact Canva font fidelity instead of approximating with Google Fonts (Dancing Script was dropped).
- **`aspect-ratio: 1429 / 2000` + `width: min(...)`** chosen over `height: 100vh` alone — guarantees the card fits both viewport dimensions with 8px padding and keeps absolute link positioning percentages accurate.
- **Button scaling: vh-based with mobile media query override** chosen over pure percentage-of-card — percentage approach over-scaled on desktop. Final: desktop `6vh`/`8vh`, mobile (≤600px) `3.5vh`/`4.5vh`.
- **Ghost pulse animation injected via inline JS** (per user request) — script appends a `<style>` with `@keyframes ghost-pulse` and adds `.pulse` class to all button anchors.
- **`docs/` and `CLAUDE.md` gitignored** at user request to keep planning artifacts out of the repo.

## Key Learnings
- The brainstorming/writing-plans/executing-plans skill triplet is heavyweight for a 2-file static site but the user followed it through.
- For absolutely-positioned overlays on an image, pinning the container to the image's exact aspect ratio (via `aspect-ratio` + `min()` width) makes percentage positioning rock solid across viewports.
- `new Image().src = '...'` is a one-liner browser preload pattern; chained in a `.forEach` to preload multiple assets on the index page.
- GitHub Pages will silently break if image assets aren't tracked by git — `git ls-files images/` confirmed `80percent.png` and `registry_page.png` were never added.

## Solutions & Fixes
- **Site broken after push:** `images/80percent.png` and `images/registry_page.png` weren't tracked. Fix: `git add images/80percent.png images/registry_page.png && git commit && git push`.
- **Image cropped on mobile:** changed card sizing from `height: 100vh` to `width: min(calc(100vw - 16px), calc((100vh - 16px) * 1429 / 2000))` with `aspect-ratio: 1429 / 2000` and added 8px body padding.
- **Buttons too big on mobile:** reverted to `vh` sizing for desktop, added `@media (max-width: 600px)` to halve them on mobile.
- **Rounded corners + pulse:** `border-radius: 12px` on both `<a>` and `<img>`; inline JS injects `@keyframes ghost-pulse { 0% box-shadow 0 0 0 0 rgba(106,176,224,0.7); 70% 0 0 0 10px rgba(...0); }` and adds `.pulse` class.

## Files Modified
- `index.html`: Main invitation page. Displays `images/80percent.png`, two PNG button links (RSVP → Google Forms, Registry → registry.html) overlaid at `bottom: 14%` of card. Inline `<script>` preloads registry assets and injects pulse animation.
- `registry.html`: Registry page. Displays `images/registry_page.png`, two PNG button links (Amazon, Target registries) stacked at `top: 40%`. Same pulse animation injected inline.
- `.gitignore`: Ignores `docs/`, `CLAUDE.md`, `**/CLAUDE.md`.
- `docs/superpowers/specs/2026-05-17-bridal-shower-invitation-design.md`: Design spec (now gitignored).
- `docs/superpowers/plans/2026-05-17-bridal-shower-site.md`: Implementation plan (now gitignored).
- `images/`: Added `80percent.png`, `registry_page.png`, `RSVPbutton.png`, `registryButton.png`, `amazonRegistryButton.png`, `targetRegistryButton.png`, `invitation.png` (moved from repo root).

## Quick Resume Context
Two-page static site at https://corbinpro.github.io/LexiAndCorbin/ — invitation page with RSVP (Google Form: https://forms.gle/5W6Cj3sw5gh5LLfb6) and Registry link; registry page with Amazon + Target registry buttons. All four buttons are Canva PNG exports overlaid on background invitation/registry images. Card uses `aspect-ratio: 1429/2000` with `width: min()` to fit any viewport with 8px padding. Open questions: RSVP link doesn't yet use `target="_blank"`; mobile button sizing currently at 3.5vh/4.5vh and may still need tweaks.
