# Stromy Showroom

Static website for Stromy company, built with Hugo and the
`hugo-saasify-theme`.

## Requirements

- Hugo Extended v0.80.0+ (required for theme)
- Node.js v14.x+
- npm

## Quick start

1) Install dependencies:

```sh
npm install
```

2) Start the dev server:

```sh
npm run start
```

This will compile TailwindCSS in watch mode and start Hugo dev server.

3) Open the local URL (http://localhost:1313)

4) Build production files:

```sh
npm run build
```

Output is written to `public/`.

## Project structure

- `hugo.toml`: site configuration (baseURL, title, theme, params, menus).
- `content/`: pages and blog posts in markdown format.
- `static/`: static assets (images, fonts). CSS is auto-generated to `static/css/style.css`.
- `layouts/`: custom layout overrides (use `layouts/partials/custom-head.html` for custom scripts).
- `tailwind.config.js`: TailwindCSS customization (colors, fonts, etc).
- `themes/hugo-saasify-theme/`: theme source as git submodule (do not edit).

## Theme Features

- Built with TailwindCSS 3.x for modern, responsive design
- 21 shortcodes for rapid component development
- Performance optimized (90+ Lighthouse scores)
- Multilingual support with i18n
- SEO optimized with semantic HTML

## Hugo Saasify Theme docs

See the [Hugo Saasify Theme documentation](themes/hugo-saasify-theme/README.md) or visit https://github.com/chaoming/hugo-saasify-theme

## Deploy to GitHub Pages

This site uses GitHub Actions to build and deploy automatically to GitHub Pages.

The workflow (`.github/workflows/hugo.yaml`) handles:
1. Installing Hugo Extended
2. Installing Node.js dependencies
3. Building TailwindCSS styles
4. Building Hugo site with minification
5. Deploying to GitHub Pages

**Requirements:**
- Set `baseURL` in `hugo.toml` to your GitHub Pages URL
- Ensure theme is added as git submodule: `git submodule add https://github.com/chaoming/hugo-saasify-theme themes/hugo-saasify-theme`
- Push to `main` branch to trigger automatic deployment

In GitHub repo settings → Pages, set the source to "GitHub Actions".

