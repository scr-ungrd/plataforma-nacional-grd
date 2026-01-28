# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the website for the **Amsterdam Complexity School on Climate Change (ACSCC)**, a Jekyll-based static site using the Hydejack v8.4.0 remote theme. It is hosted on GitHub Pages with a custom domain (`acscc.nl`).

## Build & Development Commands

```bash
bundle install              # Install Ruby dependencies
bundle exec jekyll serve    # Run local dev server at http://localhost:4000
bundle exec jekyll build    # Build static site to _site/
```

Requires Ruby and Bundler (`gem install bundler`).

## Deployment

Push to `master` branch triggers GitHub Pages auto-deployment. The `CNAME` file maps to `acscc.nl`.

## Architecture

### Theme & Layout

The site uses `qwtel/hydejack@v8.4.0` as a remote theme (configured in `_config.yml`). Page layouts, JS, and base CSS come from the remote theme. Local overrides go in:

- `_includes/my-head.html` and `_includes/my-body.html` — inject custom HTML into head/body
- `_sass/my-inline.scss` and `_sass/my-style.scss` — custom CSS overrides
- `_includes/carousel.html` — custom pure-CSS image carousel component

### Content Pages

All top-level `.md` files are individual pages (program, speakers, venue, accommodation, application, committees, support, past_editions, gallery, about). Each uses YAML front matter for Jekyll processing. Navigation order is defined in `_config.yml` under `menu:`.

### Data-Driven Content

Files in `_data/` drive dynamic content:
- `authors.yml` — site author metadata (shown in sidebar)
- `carousel.yml` — image paths for the homepage carousel
- `social.yml` — social media links
- `strings.yml` — localization strings

### Assets Organization

Images are organized by year under `assets/` (e.g., `assets/2024/`, `assets/2025/`). Speaker photos, venue images, and sponsor logos are stored here.

### Key Configuration

`_config.yml` controls:
- Site metadata (title, URL, tagline with event dates)
- Navigation menu items and order
- Accent color (`rgb(118,194,138)`) and sidebar image
- Google Analytics (`UA-142483981-1`)
- Dark mode (dynamic, sunrise/sunset based)
- Google Fonts (Noto Sans body, Roboto Slab headings)
- Kramdown with MathJax for math rendering
- HTML compression in production

### Carousel

The carousel (`_includes/carousel.html`) is a pure-CSS implementation using radio buttons. It reads images from `_data/carousel.yml` and supports up to 14 slides (letters a-n). Include it with `{% include carousel.html height="40" unit="%" %}`.
