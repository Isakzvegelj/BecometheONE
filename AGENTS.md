# AGENTS.md — Guidance for AI Agents

## Project Overview

Single-page marketing site for "BEcomeTheONE" — an AI-native agentic hub positioning. The page sells a high-ticket transformation service (€1M+ engagements) to companies wanting to become category leaders.

## Key Files

| File | Purpose | Lines |
|---|---|---|
| `index.html` | Everything: HTML skeleton, all CSS (~280 lines of inline `<style>`), all JS (~110 lines of inline `<script>`) | 680 |
| `i18n.js` | 31-language translation dictionary, exported as `window.I18N` | 580 |
| `eagle.png` | PNG image asset (eagle in flight) | — |

## Architecture Notes

- **Single-file HTML** — ALL CSS is inline in `<style>` inside `<head>`. ALL JS is inline in `<script>` at the bottom of `<body>` (except `i18n.js` which is loaded as an external deferred script).
- **No build system** — no bundler, no transpiler, no package.json. The site works by opening `index.html` directly.
- **i18n** — Elements are translated via `data-i18n` attributes. The `setLang()` function in the inline script reads `window.I18N[code]` and sets `el.innerHTML = dict[key]`.
- **Language detection** — Defaults to English, checks `localStorage.getItem('btolang')`, falls back to `en`.
- **Scroll animations** — Elements with class `reveal` are animated in via IntersectionObserver. Delays are set by classes `d1`–`d5`.
- **Contact form** — Uses a simulated async send (1.2s delay). No backend endpoint is configured.
- **Deployment** — GitHub Pages. Push to `main`.

## Coding Conventions

- **CSS** — All in `:root` variables in `<style>`. Uses `--cyan`, `--gold`, `--ink`, `--paper` as the primary palette. Mobile breakpoint at 850px, secondary at 720px/600px.
- **JS** — `const`/`let`, no framework. DOM queries via `getElementById`/`querySelector`. Event listeners in inline script.
- **HTML** — Semantic elements (`<header>`, `<section>`, `<footer>`, `<nav>`, `<main>`). BEM-like class naming. Aria attributes on interactive elements.
- **No comments in code** — Do not add explanatory comments. The code should be self-documenting.

## Constraints

1. **Must remain a single-file HTML** — No splitting CSS or JS into separate files (except `i18n.js` and `eagle.png` which are already external).
2. **No build step** — No npm, no bundler, no transpiler. Must work when opened directly in a browser.
3. **No external runtime deps** — Google Fonts (Fraunces + Inter) are the only external resources. No other CDN scripts, no analytics, no third-party widgets.
4. **Must preserve i18n** — All 31 languages must continue to work. The `data-i18n` attribute pattern must be preserved.
5. **Must preserve accessibility** — Skip link, aria attributes, semantic HTML, focus management must remain intact.
6. **No backend** — The contact form is a simulated frontend-only interaction. Keep it that way unless explicitly asked to add a backend.

## Suggested Improvement Areas

- Performance (image optimization, lazy loading, CSS minification)
- SEO (structured data, meta tags, sitemap)
- Accessibility audit (color contrast, keyboard navigation, screen reader testing)
- UX polish (form validation, loading states, error handling)
- Content updates (copy, pricing, testimonials)
- Add a proper favicon file
- og-image.png asset for social sharing