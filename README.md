---
title: "sw-boilerplate67-ah — project wiki"
tags: [readme, meta]
---

# sw-boilerplate67-ah — project wiki

This documentation was produced by the **Shopware Ecosystem AI SDK**. It is structured, atomic documentation written to be consumed by coding agents (MCP/LLM tooling) and, at the same time, to serve as the project's living documentation for the whole team — PMs, architects, developers, QA.

## What is inside

- `domains/<domain>/` → one feature page per surface (`administration/`, `storefront/`); `adr/` holds decision records; `domains/platform/` covers cross-cutting infrastructure (extensions, configuration, logging, debugging, environments).
- Entry point is [index.md](index.md); the rules every page follows are in [CONVENTIONS.md](CONVENTIONS.md).
- Kept in sync by the `sw-document-feature` skill after each feature verification (`sw-verify-feature`).

## Publish with GitHub Pages (quick setup)

1. Push the repository to GitHub.
2. Settings → Pages → Build and deployment: Source **Deploy from a branch**, branch `main` (or `master`), folder **/docs**.
3. Pages serves `docs/`, so the wiki lands at `https://<org>.github.io/<repo>/project-wiki/`.

Note: the built-in Jekyll build reads `_config.yml` only from the Pages source root (`docs/`), so the `_config.yml` inside `project-wiki/` is not picked up. Two practical options:

- (a) accept the default rendering — pages carry no theme-specific front matter, so they render fine;
- (b) switch Source to **GitHub Actions** and use a Pages workflow (`actions/jekyll-build-pages` with `source: docs/project-wiki`, or a custom `jekyll build --source docs/project-wiki`) so the wiki's own `_config.yml` applies.

## Publish with Jekyll (more features)

```sh
gem install bundler jekyll
cd docs/project-wiki
jekyll serve            # or: bundle exec jekyll serve (with the Gemfile below)
# open http://127.0.0.1:4000
```

`_config.yml` in this folder is the place for theme and plugins (e.g. `just-the-docs` for search and navigation). Pages avoid theme-specific front matter, so any theme works. Minimal `Gemfile`:

```ruby
source "https://rubygems.org"
gem "jekyll"
gem "just-the-docs"   # optional theme; set `theme: just-the-docs` in _config.yml
```

---

Generated 2026-09-06 · verified against Shopware 6.7.13 · Source of truth for rules: CONVENTIONS.md
