# Concept wiki - static site (GitHub Pages bundle)

This directory is a **pre-built, self-contained static site**: one HTML page per concept,
a landing `index.html`, and a sibling `assets/` folder of images. There is no build step
and no runtime server. Every page renders fully offline with no external resource loads.

## Local preview

Serve this directory over HTTP and open <http://localhost:8000/>:

```
python -m http.server -d . 8000
```

## Publish to GitHub Pages

This is a **staging build**. To publish it, copy or push the **contents of this
directory** (including `.nojekyll`, `.github/`, and `assets/`) to the **root of a
separate, dedicated deploy repository**. Then enable GitHub Pages on that repo using
**one** of the two modes below - they are **alternatives, not both**:

- **(a) GitHub Actions.** In the deploy repo, set Settings -> Pages -> Source to
  "GitHub Actions". The bundled workflow at `.github/workflows/pages.yml` (now at the
  deploy repo root) uploads this directory and deploys it on every push to the default
  branch.
- **(b) Branch / `/docs` folder.** In the deploy repo, set Settings -> Pages -> Source to
  a branch and folder (the repo root, or a `/docs` subfolder if you place the files
  there). Pages then serves the committed files directly and **ignores** the workflow.

Pick either (a) or (b), not both. `.nojekyll` disables Jekyll processing so directories
beginning with an underscore and the raw HTML are served verbatim.
