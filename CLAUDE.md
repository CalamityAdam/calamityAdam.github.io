# calamityAdam.github.io

Personal site, hosted on GitHub Pages, served at **adumb.dev** (custom domain via Cloudflare DNS — see README.md for the registrar/DNS setup).

## Stack

Plain static HTML/CSS/JS. **No build step.** GitHub Pages serves the repo as-is.

Jekyll runs by default on Pages but only processes files with YAML front-matter — every HTML file in this repo is plain HTML, so Jekyll passes it through unchanged. Don't add front-matter unless you mean to opt into Liquid templating.

## Deploy

Push to `master`. That's it. Pages rebuilds in ~30–60s. Cloudflare may also cache — hard refresh if changes don't appear.

```sh
git -C /Users/adam.sisk/dev/repos/adamsisk/calamityAdam.github.io push
```

## Layout

| Path | Purpose |
|------|---------|
| `index.html` | Landing page — name, headshot, nav links |
| `style.css` | Landing styles only (Montserrat, pastel/teal/blue palette via CSS custom properties) |
| `index.js` | Landing JS (currently minimal) |
| `questions/` | Standalone conversation visualizer (self-contained HTML with embedded styles) |
| `reports/` | Standalone analysis reports — **unlinked from the main nav, accessed by direct URL** |
| `artifacts/` | Standalone engineering walkthroughs / blog posts — same convention as `reports/` (unlisted, direct URL) |
| `assets/` | Resume PDF, headshot |
| `favicon.svg` | Site icon — referenced as `../favicon.svg` from subpages |
| `CNAME` | `adumb.dev` — required by GitHub Pages for the custom domain |

## Conventions

### Subpages are self-contained
The `questions/`, `reports/`, and `artifacts/` pages each embed their own `<style>` block instead of importing `style.css`. They reuse the site's color palette (declared inline) and Montserrat font, but otherwise stand alone. This keeps the landing's CSS small and lets each subpage iterate without risk of breaking the homepage.

### Reports / Artifacts are "unlisted, not private"
Neither `reports/` nor `artifacts/` is linked from `index.html`. Anyone with the URL can read them, and a search crawler that finds the URL may index them. Treat this as obscurity, not access control — never put anything Ramsey-internal, PII, or otherwise sensitive in here.

**`reports/` vs `artifacts/`:**
- `reports/` — analysis dashboards, data write-ups, ad-hoc investigations with charts and numbers. Quieter audience, often technical-internal in tone.
- `artifacts/` — blog-post-flavored engineering walkthroughs. Long-form, narrative, intended for sharing. Each post is a self-contained HTML with hero, modules, OG meta tags, JSON-LD `BlogPosting`, canonical URL, footnotes, and an author footer. Treat as if going on the public web (because it is).

To add a report or artifact:
1. Drop the self-contained HTML into `reports/` or `artifacts/` with a URL-friendly slug (`kebab-case.html`)
2. Add a card to the corresponding `index.html` — copy an existing `<li class="report-card">` / `<li class="artifact-card">` and update title/date/description
3. For artifacts: also add OG/Twitter meta + JSON-LD with absolute `https://adumb.dev/...` URLs, and an OG image (1200×630, can be SVG)
4. Commit and push

### Homepage nav is flex chips
`style.css` lays out the homepage nav as a flex-wrap row of pill-shaped `.chip` links — adding or removing a chip needs no layout changes, they wrap on their own.

## Git

- Default branch is **`master`**, not `main`.
- Don't commit anything Ramsey-related (work, internal data, screenshots from work tools).
