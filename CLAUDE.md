# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

This is a static GitHub Pages site (`davidkazuhiro.github.io`) served directly from the repository root via GitHub Pages. There is no build system, package manager, framework, or test suite — the repository consists of raw static files that GitHub Pages serves as-is.

- `index.html` — the site's single page.
- `CNAME` — configures the custom domain (`david.somers-harris.com`) for GitHub Pages.

## Development workflow

There are no build, lint, or test commands — none are configured, and none are needed. Edit HTML/CSS/JS files directly and commit.

To preview changes locally, open `index.html` directly in a browser, or serve the directory with any static file server (e.g. `python3 -m http.server`) and visit `http://localhost:8000`.

Changes take effect on the live site automatically once pushed to the default branch, via GitHub Pages' built-in deployment — there is no separate deploy step or CI pipeline in this repository.

## Conventions

- Keep the site as plain static files (HTML/CSS/JS) unless the user explicitly asks to introduce a framework or build tooling.
- If the custom domain changes, update `CNAME` (single line, no protocol, e.g. `example.com`).
