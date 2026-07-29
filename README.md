# BEcomeTheONE

AI-native agentic hub landing page — a single-page marketing site for companies that want to become AI-native category leaders.

## Tech Stack

- **Vanilla HTML/CSS/JS** — no build step, no framework, no runtime dependencies
- **Google Fonts** — Fraunces (headings) + Inter (body) loaded from CDN
- **i18n** — 31-language translation dictionary loaded via external script (`i18n.js`)

## File Structure

```
BEcomeTheONE/
├── index.html      # Main page: HTML structure + all inline CSS + inline JS
├── i18n.js         # Translation dictionary (31 languages, window.I18N)
├── eagle.png       # Eagle image asset displayed in the "world" section
├── README.md       # This file
├── AGENTS.md       # Guidance for AI agents working on this project
└── .gitignore
```

## How to Run

Open `index.html` directly in a browser, or serve locally:

```bash
python3 -m http.server 8000
# or
npx serve .
```

## Deployment

Deployed via GitHub Pages from `https://github.com/Isakzvegelj/BecometheONE`.
Push to `main` to deploy.

## i18n

Translations are stored in `i18n.js` as `window.I18N` — a dictionary keyed by language code (ISO 639-1). The page loads `i18n.js` via a `<script defer>` tag. Elements with `data-i18n` attributes are populated by the `setLang()` function.

Language selection is persisted in `localStorage` under the key `btolang`.