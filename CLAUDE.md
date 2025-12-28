# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static website for Stromy company built with **Hugo** using the `hugo-universal-theme`. Hugo is a static site generator that uses Go templates and markdown content to generate HTML.

## Development Commands

### Development Server
```sh
hugo server -D
```
- Starts local development server with live reload
- `-D` flag includes draft content
- Default URL: http://localhost:1313

### Production Build
```sh
hugo
```
- Generates static site files in `public/` directory
- Use `hugo --minify` for production deployment

## Architecture & Content Management

### Data-Driven Components

The hugo-universal-theme uses a **data-driven architecture** for homepage sections. Unlike typical Hugo sites where content lives in markdown files, key homepage components are defined as YAML files in the `data/` directory:

- **`data/carousel/`**: Homepage carousel slides (each `.yaml` file = one slide)
  - Fields: `weight`, `title`, `description` (HTML allowed), `image`, `href`

- **`data/features/`**: Feature boxes with icons (each `.yaml` file = one feature)
  - Fields: `weight`, `name`, `icon` (FontAwesome CSS class), `url`, `description`

- **`data/testimonials/`**: Customer testimonials (each `.yaml` file = one testimonial)
  - Fields: `text`, `name`, `position`, `avatar`

- **`data/clients/`**: Client/partner logos (each `.yaml` file = one client)
  - Fields: `name`, `image`, `url`

The `weight` field controls display order across all these components.

### Configuration-Based Content

The theme heavily relies on `hugo.toml` configuration rather than traditional content files:

- **Menu system**: Defined in `[[menu.main]]` sections
  - Supports dropdown menus with sections and columns
  - Use `parent` field to create hierarchical menus
  - Special behavior: `url` field on top-level menu with image path creates 2-column image dropdown

- **Homepage sections**: Enabled/disabled via `[params.X]` blocks
  - `params.carouselHomepage`, `params.features`, `params.testimonials`, `params.clients`, `params.recent_posts`, `params.see_more`

- **Footer content**: Configured via `params.about_us`, `params.contact_url`, `params.address`

### Standard Hugo Directories

- **`content/`**: Markdown files for pages and blog posts
  - Blog posts should include `banner = "img/banners/banner-x.jpg"` in frontmatter
  - Contact page must have `id = "contact"` in frontmatter

- **`static/`**: Static assets (images, CSS, fonts)
  - Custom CSS: `static/css/custom.css`
  - Images referenced in data files use paths relative to `static/` (e.g., `img/carousel/slide.png`)

- **`layouts/`**: Template overrides (only override theme templates when necessary)
  - `layouts/partials/custom_headers.html` for custom JS/CSS includes

### Theme Customization Approach

**DO NOT edit files in `themes/hugo-universal-theme/`**. Instead:
- Override layouts by creating same-path files in root `layouts/` directory
- Add custom CSS in `static/css/custom.css`
- Configure via `hugo.toml` parameters
- Theme color: set `style` param to: `default`, `blue`, `green`, `marsala`, `pink`, `red`, `turquoise`, or `violet`

## Key Configuration Patterns

### Theme-Specific Parameters
- `params.disabled_logo`: Set to true to use text logo instead of image
- `params.dropdown_mouse_over`: Change menu from click to hover
- `params.topbar.enable`: Enable top contact bar
- `params.widgets`: Enable/disable sidebar widgets (search, categories, tags)
- `params.enableGoogleMaps`, `params.enableRecaptchaInContactForm`: Feature flags

### Integration Services
- Disqus comments: `services.disqus.shortname`
- Google Analytics: `services.googleAnalytics.id`
- Formspree contact form: `params.email`
- Google Maps: `params.googleMapsApiKey`, `params.latitude`, `params.longitude`

## Important Notes

- This is NOT a Git repository (no version control initialized)
- Theme uses Bootstrap 3.4 CSS framework
- FontAwesome icons available for features
- HTML allowed in: carousel descriptions, footer text, topbar text
- Menu items with `identifier` starting with `section.` become dropdown section headers
- The `post` attribute in menu items controls column placement (1-4) in dropdown menus
