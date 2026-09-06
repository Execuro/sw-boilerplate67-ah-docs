---
title: "sw-boilerplate67-ah — project wiki"
tags: [readme, meta]
---

# sw-boilerplate67-ah — project wiki

**→ Start reading at [index.md](index.md).** This page explains what the wiki is and how it is
published; the documentation itself starts at the index.

This is the living documentation for one Shopware 6 project. It is structured and atomic so that
coding agents (MCP/LLM tooling) can consume it page by page, and written so that the whole team —
PMs, architects, developers, QA — can read the same pages without a translation layer.

## What is inside

| Folder | What lives there |
|---|---|
| [`domains/`](domains/index.md) | Feature documentation, one page per surface (`administration/`, `storefront/`) |
| [`domains/platform/`](domains/platform/index.md) | Cross-cutting infrastructure: extensions, configuration, logging, debugging, environments |
| [`baseline/`](baseline/tech-stack.md) | The project's tech stack and its glossary |
| [`adr/`](adr/index.md) | Accepted architecture and process decisions |
| [`CONVENTIONS.md`](CONVENTIONS.md) | The rules every page follows |

Pages are kept in sync by the `sw-document-feature` skill after each feature verification
(`sw-verify-feature`).

## Publishing with GitHub Pages

The wiki uses the [Primer](https://github.com/pages-themes/primer) theme — one of the themes
GitHub Pages supports natively, so no build setup or Actions workflow is needed. Which of the two
setups applies depends on where this folder lives:

**A. Published as its own repository** (this folder is the repository root — the simplest case):

1. Push the folder to its own GitHub repository.
2. Settings → Pages → Build and deployment: Source **Deploy from a branch**, branch `master`, folder **/ (root)**.
3. `_config.yml` here is the site config, so the Primer theme applies automatically.

**B. Published from the parent project repository** (`docs/project-wiki/` inside a larger repo):

GitHub Pages only reads `_config.yml` from the Pages source root (`/` or `/docs`), never from a
nested folder — so a branch deploy from `/docs` renders these pages **unthemed**. To keep the
theme, either move the wiki to its own repository (setup A), or switch Source to **GitHub Actions**
and point a Jekyll build at this folder (`actions/jekyll-build-pages` with `source: docs/project-wiki`).

## Previewing locally

```sh
gem install bundler jekyll
cd docs/project-wiki
bundle exec jekyll serve      # or: jekyll serve
# open http://127.0.0.1:4000
```

Minimal `Gemfile` — `github-pages` pins the exact versions GitHub Pages runs, so a local preview
matches the published site:

```ruby
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
```

---

*Generated 2026-09-06 · verified against Shopware 6.7.13 · the rules for pages live in
[CONVENTIONS.md](CONVENTIONS.md).*
