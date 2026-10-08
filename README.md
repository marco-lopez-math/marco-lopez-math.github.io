# marco-lopez-math.github.io

This repository is a Jekyll-based GitHub Pages site.

## Changes in this repaired version

- MathJax 3 is loaded from jsDelivr with `defer`, so the document is parsed before MathJax typesets it.
- Both `\(...\)` / `$...$` and `\[...\]` / `$$...$$` delimiters are configured.
- Site links and the stylesheet use Jekyll's `relative_url` filter.
- Added the missing `about.md` page so the existing About navigation link has a target.
- Made the CV iframe responsive.
- Added mobile styling and horizontal overflow handling for wide display mathematics.
- Removed generated `_site/` and `.jekyll-cache/` content from the source package.
- Removed local Zotero filesystem paths from `publications.bib`.
- Added a GitHub Pages Actions workflow under `.github/workflows/pages.yml`.

## GitHub Pages

For this `*.github.io` user site, the repository root is the Pages source.

In GitHub, open **Settings → Pages → Build and deployment → Source** and select
**GitHub Actions**. Then push the repository to `main`.

GitHub's current Pages documentation recommends the Actions workflow used here and
documents `actions/checkout@v6`, `actions/configure-pages@v5`,
`actions/jekyll-build-pages@v1`, `actions/upload-pages-artifact@v4`, and
`actions/deploy-pages@v4`.

## MathJax

The important part is in `_layouts/default.html`. The configuration is deliberately
placed before the loader:

```html
<script>
  window.MathJax = {
    tex: {
      inlineMath: [['\\(', '\\)'], ['$', '$']],
      displayMath: [['\\[', '\\]'], ['$$', '$$']]
    }
  };
</script>
<script defer src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
```

After deployment, test the Publications page using the two titles that contain
mathematics. If the expressions render as formatted mathematics rather than raw
LaTeX, the MathJax problem is resolved.
