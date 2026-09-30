# Instructions for AI agents (Jules)

This repository is a MkDocs documentation site deployed to GitHub Pages.

## What you may change

- **Only Markdown files under `docs/`** (`docs/**/*.md`). Add, edit, rename or delete pages there.
- Do **not** change anything else: `mkdocs.yml`, `requirements.txt`, `README.md`, `AGENTS.md`, `LICENSE`, or anything under `.github/`. Do not add images or other non-Markdown files.

Pull requests that stay within `docs/**/*.md` and build cleanly are merged and deployed automatically. A pull request that touches any other file is **not** merged automatically; it waits for a human to review it.

## Navigation

There is no `nav:` in `mkdocs.yml`. The site menu is built from the `docs/` folder structure:

- `docs/index.md` is the home page.
- Group related pages in subfolders (e.g. `docs/architecture/overview.md`); each folder becomes a section.
- Use relative links between pages (e.g. `[Overview](architecture/overview.md)`), and keep them valid when you move or rename a page.

## Before opening a pull request

Make sure the site builds with no warnings:

```bash
pip install -r requirements.txt
mkdocs build --strict
```

A build that fails (for example, because of broken internal links) will not be merged.
