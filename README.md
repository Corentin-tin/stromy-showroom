# Stromy Showroom

Static website for Stromy company, built with Hugo and the
`hugo-universal-theme`.

## Requirements

- Hugo (latest stable recommended)

## Quick start

1) Start the dev server:

```sh
hugo server -D
```

2) Open the local URL printed by Hugo.

3) Build production files:

```sh
hugo
```

Output is written to `public/`.

## Project structure

- `hugo.toml`: site configuration (baseURL, title, theme, params).
- `content/`: pages and posts (create this as you add content).
- `data/`: homepage sections (carousel, features, testimonials, clients).
- `static/`: images and custom CSS (ex: `static/css/custom.css`).
- `themes/hugo-universal-theme/`: theme source (do not edit unless you are
  maintaining the theme).

## Hugo Universal Theme docs

See the [Hugo Universal Theme documentation](themes/hugo-universal-theme/README.md)

## Deploy to GitHub Pages

Recommended: build with GitHub Actions and publish `public/` to `gh-pages`.

1) Set `baseURL` in `hugo.toml`:
   - Project page: `https://<user>.github.io/<repo>/`
   - User page: `https://<user>.github.io/` (repo must be named `<user>.github.io`)

2) Add a workflow like this (save as `.github/workflows/deploy.yml`):

```yaml
name: Deploy Hugo
on:
  push:
    branches: ["main"]
permissions:
  contents: write
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: "0.125.0"
      - run: hugo --minify
      - uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

3) In GitHub repo settings -> Pages, set the source to the `gh-pages` branch.

