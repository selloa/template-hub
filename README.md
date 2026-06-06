# template-hub

A reusable static hub template: write Markdown, run a local build, publish HTML to GitHub Pages.

**Workflow:** edit `content/*.md` → run `python build.py` → preview with `serve.bat` or open `index.html`.

## What this is

- **Source of truth:** `content/*.md` with YAML front matter
- **Build:** `build.py` generates static HTML with sidebar nav, Google Translate, link badges, and more
- **Deploy:** commit generated HTML at the repo root for GitHub Pages (no CI required)

Live hubs such as [coder-hub](https://github.com/selloa/coder-hub) and dottt-hub can pick up improvements made here over time.

## Quick start

Requires Python 3:

```powershell
pip install -r requirements.txt
python build.py
```

Double-click **`serve.bat`** to rebuild and open http://localhost:8000/ in your browser.

## First customization checklist

1. **Edit `SITE` in `build.py`** — `site_id`, `site_name`, `default_description`, `author_name`, `author_url`, `translate_languages`
2. **Edit `content/index.md`** — front matter (`title`, `description`, etc.) and home page body
3. **Rename or replace `content/topics.md`** — or add new pages (see below)
4. **Replace `assets/favicon.svg`** — optional branding
5. **Run `python build.py`** — then commit both `.md` sources and generated `.html`

## Repository layout

| Path | Purpose |
|------|---------|
| `content/*.md` | Source of truth — edit these |
| `build.py` | Build engine + `SITE` config and page manifest |
| `index.html`, `topics/`, etc. | Generated site (commit for GitHub Pages) |
| `assets/site.css` | Page styling |
| `serve.bat` | Build + local preview |

## Adding a page

1. Create `content/newpage.md` with YAML front matter and content.
2. Add an entry to `PAGES` in `build.py`:

   ```python
   ("content/newpage.md", "newpage/index.html", "newpage"),
   ```

3. Add a matching entry to `NAV_ITEMS`:

   ```python
   ("newpage", "New Page", "newpage/index.html"),
   ```

4. Run `python build.py`.

For a **single-page hub**, use one entry in `PAGES` and leave `NAV_ITEMS` empty (remove the `build_topnav` call from the template if you prefer no top nav — or keep one item).

## Markdown features

| Feature | Usage |
|---------|--------|
| Auto build date | `date: *` (or `auto`, `today`) in front matter |
| Bare URL pairs | Title on one line, URL on the next (no blank line between) |
| Owner / fork badges | `<owner>` or `<fork>` on its own line |
| Internal author notes | `## Page build notes` section — stripped at build time |
| Task lists | `- [ ]` and `- [x]` (via pymdownx.tasklist) |

External `http(s)` links open in a new tab. YouTube, Vimeo, and other video hosts get a `link-video` class (play icon on hover).

## GitHub Pages

1. Push the repo with generated HTML at the root.
2. In repo **Settings → Pages**, set source to the default branch, folder **/ (root)**.
3. Optional: enable **Template repository** in **Settings** so others can click "Use this template".

Relative links work for both user sites (`yourname.github.io`) and project sites (`yourname.github.io/my-hub/`).

Regenerate locally with `python build.py` before pushing — same workflow as a hand-maintained static site.

## Build locally (reference)

```powershell
pip install -r requirements.txt
python build.py
```

Or use **`build.bat`** (build only) or **`serve.bat`** (build + preview).

## License

MIT — see [LICENSE](LICENSE).
