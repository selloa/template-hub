---
title: My Hub
version: 0.1.0
date: *
status: draft
description: A simple static hub built from Markdown.
---

# My Hub

*A lightweight home for links, notes, and references.*

Write content in Markdown under `content/`, run `python build.py`, and publish the generated HTML to GitHub Pages.

---

## Explore

- **[Topics](topics/index.html)** — example second page with sidebar sections and link styles

---

## Customize this hub

1. Edit the `SITE` block at the top of `build.py` (name, author, site id).
2. Edit this file and `content/topics.md` (or rename/replace them).
3. Add pages by extending `PAGES` and `NAV_ITEMS` in `build.py`.
4. Run `python build.py`, then commit both `.md` sources and generated `.html`.

See `README.md` for the full checklist.

---

## Page build notes

Internal notes for the author — stripped from the published page at build time.
Use this section for drafts, TODOs, or reminders about the build workflow.
