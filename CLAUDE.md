# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Academic personal homepage for Rui Zhou, built with Jekyll 3.9.0 and deployed via GitHub Pages. Based on the AcadHomepage template.

## Development Commands

```bash
# Install dependencies
bundle install

# Run local development server with live reload (http://127.0.0.1:4000)
bash run_server.sh
# or directly:
bundle exec jekyll liveserve
```

## Architecture

- **`_config.yml`** — Main site configuration: metadata, author profile, social links, plugins, Google Scholar CDN settings
- **`_pages/about.md`** — All homepage content (biography, news, education, publications, internships) in a single Markdown file with embedded HTML
- **`_layouts/default.html`** — Base HTML layout that assembles includes (head, masthead, sidebar, scripts)
- **`_includes/`** — HTML partials: sidebar, author profile, SEO tags, analytics, MathJax config, Google Scholar stats fetcher
- **`_data/navigation.yml`** — Navigation menu sections
- **`_sass/`** — SCSS stylesheets; `assets/css/main.scss` is the entry point that imports everything
- **`google_scholar_crawler/`** — Python script (`main.py`) using `scholarly` to fetch citation stats; automated daily via GitHub Actions (`.github/workflows/google_scholar_crawler.yaml`), outputs to `google-scholar-stats` branch

## Key Patterns

- **Publications** are defined directly in `_pages/about.md` using `<div class='paper-box'>` HTML blocks with inline citation count spans (`<span class='show_paper_citations' data='PAPER_ID'>`)
- **Google Scholar stats** are fetched client-side from jsdelivr CDN pointing to the `google-scholar-stats` branch
- **Navigation sections** correspond to anchor IDs in `about.md` (e.g., `#-news`, `#-educations`, `#-publications`)
- MathJax v2.7.4 is enabled for mathematical notation
