# Representation Forcing — Project Page

Static project page for *Representation Forcing for Bottleneck-Free Unified Multimodal Models*.

Built on the [Nerfies](https://nerfies.github.io/) template (Bulma + AOS), keeping a consistent
look with the project pages for [Loong](https://yuqingwang1029.github.io/Loong-video/),
[PAR](https://yuqingwang1029.github.io/PAR-project/), and
[TokenBridge](https://yuqingwang1029.github.io/TokenBridge/).

## Structure

```
RF-gh-pages/
├── index.html
├── README.md
└── static/
    ├── css/      # Bulma, fontawesome, custom index.css
    ├── js/       # Bulma carousel/slider, index.js
    └── images/   # PUT YOUR FIGURES HERE (see below)
```

## Required images

The page references the following files in `static/images/`. The paper ships them as PDFs
(under `../figs/`), so you'll need to export web-friendly versions:

| Page slot | Expected filename | Source PDF | Recommended format |
|---|---|---|---|
| Architectural comparison | `teaser.png` | `figs/teaser.pdf` | PNG @ ~2400px wide, or SVG |
| Demo gallery (1024 results) | `demo.png` | `figs/demo.pdf` | PNG @ ~2400px wide |
| Training pipeline | `method.png` | `figs/method.pdf` | PNG @ ~2400px wide, or SVG |
| Qualitative comparison | `compare.png` | `figs/compare.pdf` | PNG @ ~2400px wide |

### Quick conversion (macOS / Linux with `pdftoppm` and `pdf2svg`)

```bash
cd ../figs
for f in teaser demo method compare; do
  pdftoppm -r 300 -png "$f.pdf" "../RF-gh-pages/static/images/$f"
  # pdftoppm appends "-1" for single-page PDFs; rename:
  mv "../RF-gh-pages/static/images/$f-1.png" "../RF-gh-pages/static/images/$f.png" 2>/dev/null || true
done
```

Or, if you prefer SVG for line-art figures (teaser, method):

```bash
pdf2svg ../figs/teaser.pdf ../RF-gh-pages/static/images/teaser.svg
pdf2svg ../figs/method.pdf ../RF-gh-pages/static/images/method.svg
```

If you switch to SVG, change the `src="./static/images/teaser.png"` references in `index.html`
to `.svg`.

## Things to fill in before publishing

In `index.html`, search for `href="#"` placeholders and replace with real URLs:

- arXiv link (line in the hero `link-block` section)
- Paper PDF link
- GitHub code link
- BibTeX entry: replace `arXiv:XXXX.XXXXX` and confirm year (`2026`) and the
  `wang2026representation` cite key.

Also confirm in the "More Research" navbar dropdown that the link to the
TokenBridge page is correct (`https://yuqingwang1029.github.io/TokenBridge/`).
If your TokenBridge page lives at a different URL, update accordingly.

## Local preview

```bash
cd RF-gh-pages
python3 -m http.server 8000
# open http://localhost:8000
```

## Deployment

The page is fully static. Push the contents of `RF-gh-pages/` to a `gh-pages` branch
(or a repo with GitHub Pages enabled), e.g.:

```bash
# inside a new repo
git checkout --orphan gh-pages
git add .
git commit -m "init project page"
git push origin gh-pages
```

Then enable Pages in the GitHub repo settings (Source: `gh-pages` branch, root).

## Notes on style choices vs. TokenBridge page

- Added a **TL;DR callout** at the top of the hero for fast skim-reading.
- Added **Open Graph meta tags** so the page renders nicely when shared on Twitter/X.
- Added a dedicated **"Our Line of Work"** section linking back to Loong / PAR / TokenBridge
  (in addition to the navbar dropdown).
- Kept the same color palette (`#0074D9` blue), Bulma layout, AOS scroll animations.
