# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

This is a personal profile site (`davidkazuhiro.github.io`) built with Jekyll and served via GitHub Pages, which builds it automatically on every push — no CI pipeline or separate deploy step. Content is authored in Markdown and rendered through Jekyll (GitHub Pages' native static site generator), not hand-written HTML.

- `index.md` — the site's content (bio + social links), as Markdown with YAML front matter (`title`, `tagline`, `location`).
- `_config.yml` — Jekyll site config. Sets `theme: null` deliberately — the site uses a fully custom layout/CSS, not a gem-based theme (the `github-pages` gem defaults to `jekyll-theme-primer` if this isn't set, which pulls in a stylesheet that fails to compile locally). `README.md`, `CLAUDE.md`, and Ruby tooling files are excluded from the build via `exclude:`.
- `_layouts/default.html` — the single layout. Renders `page.title`/`page.tagline`/`page.location` as a header, then `{{ content }}` (the rendered Markdown body).
- `assets/css/style.css` — all styling: CSS custom properties for a light/dark palette (`prefers-color-scheme`), one indigo accent color, Shippori Mincho for the name and Noto Sans JP for body text.
- `CNAME` — configures the custom domain (`david.somers-harris.com`).
- `Gemfile` — pins the `github-pages` gem so local builds use the same Jekyll/plugin versions as GitHub Pages' production build.

To add a link/button styled consistently with the existing ones, use kramdown's inline attribute list syntax on a normal Markdown link: `[Label](url){:.link-btn target="_blank" rel="noopener"}` — this keeps content in Markdown rather than dropping into raw HTML.

## Development workflow

Requires Ruby + Bundler. This repo pins Ruby via `.ruby-version`-less rbenv setup — if `jekyll`/`bundle exec jekyll` reports "command not found" after `bundle install`, check `rbenv version` isn't pointing at a Ruby without the gems installed (`rbenv local <version>` to pin one, then `rbenv rehash`).

```sh
bundle install                 # first time / after Gemfile changes
bundle exec jekyll serve       # local preview at http://localhost:4000, rebuilds on change
bundle exec jekyll build       # one-off build into _site/
```

There are no lint or test commands configured.

Changes take effect on the live site automatically once pushed to the default branch — GitHub Pages runs its own Jekyll build server-side.

## Conventions

- Keep content changes in Markdown (`index.md` and any future pages) rather than editing generated HTML or reaching for raw `<div>`/`<a>` blocks when a styled Markdown link will do.
- Theme/design changes belong in `_layouts/default.html` and `assets/css/style.css`. Don't introduce a JS framework or client-side build step unless explicitly asked — this is meant to stay a plain Jekyll site.
- Single accent color (indigo) design language against a neutral light/dark background — keep new UI elements consistent with that rather than introducing new colors.
- If the custom domain changes, update `CNAME` (single line, no protocol, e.g. `example.com`).
