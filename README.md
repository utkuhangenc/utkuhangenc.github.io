# Utkuhan Genc — academic website

A personal academic website based on the minimalist Quarto/GitHub Pages style of [lyons66.github.io](https://lyons66.github.io/). It contains real research and publication content from an academic CV and research statement, with a clearly marked placeholder where a headshot belongs.

## What is included

- `index.qmd` — homepage and research biography
- `research.qmd`, `publications.qmd`, `teaching.qmd`, `talks.qmd`, `cv.qmd` — editable pages
- `_quarto.yml` — Quarto configuration, site title, and navigation
- `styles.css` — styling; edit fonts, spacing, colors
- `assets/profile.svg` — temporary **UG** photo placeholder
- `docs/` — **ready-to-publish static website**; this works even if Quarto is not installed
- `.github/workflows/publish.yml` — optional automatic Quarto build and publish once GitHub Pages is set to GitHub Actions

## Option A: publish the prebuilt website with GitHub Pages (beginner-friendly)

1. Unzip the project. If you do not have a GitHub account, create one at https://github.com.
2. Create a **public** repository called `YOURUSERNAME.github.io` (replace `YOURUSERNAME` with your actual GitHub username).
3. Upload the **contents of this project folder**, maintaining its folders. GitHub Desktop (https://desktop.github.com/) makes this easy: clone your new repository, paste the files into its folder, commit, and **Push origin**. Or use the command-line commands below.
4. In the repository, open **Settings → Pages → Build and deployment** and select **Deploy from a branch**, branch **main**, folder **/docs**, then **Save**.
5. Your site will be available at `https://YOURUSERNAME.github.io/` after GitHub Pages deploys it. Check the repository's **Actions** or **Settings → Pages** for publication status.

**Note:** The bundled automatic Quarto workflow is disabled by default (`workflow_dispatch` only), so it will not interfere with the straightforward `/docs` branch deployment above.

### Git command-line upload (alternative to GitHub Desktop)

Create an empty public repository on GitHub first. Then open a terminal *inside the unzipped project folder*:

```bash
git init
git add .
git commit -m "Launch academic website"
git branch -M main
git remote add origin https://github.com/YOURUSERNAME/YOURUSERNAME.github.io.git
git push -u origin main
```

Replace both `YOURUSERNAME` strings. GitHub Desktop does not require these commands.

## Option B: edit pages using Quarto, then republish

1. Install [Quarto](https://quarto.org/docs/get-started/).
2. Open the project folder and edit the relevant `.qmd` pages. These are just text files written in Markdown.
3. Run `quarto preview` to see the changes in your browser.
4. Run `quarto render` to regenerate the `docs/` folder.
5. Commit and push both the changed `.qmd` files and `docs/` output. GitHub Pages will update using the `main /docs` branch setting from Option A.

If you prefer automatic rendering in GitHub rather than installing Quarto locally, change the workflow trigger from `workflow_dispatch` to `push` and set Pages to **GitHub Actions** instead of `/docs` branch. This requires the `pages: write` and `id-token: write` permissions already defined in `.github/workflows/publish.yml`.

## Personalize before you share publicly

- **Photo:** replace `assets/profile.svg` with your portrait. For a JPEG/PNG, update the `image:` field in `index.qmd`; for the prebuilt site, also change the `src` in `docs/index.html` and put the image inside `docs/assets/`, or regenerate `docs/` with Quarto.
- **Biography:** edit `index.qmd`. The public contact email is currently `ugenc@purdue.edu`.
- **CV:** the CV page is intentionally a short public summary. No home address or personal telephone number is published. When you have a public CV PDF, add it and link it from `cv.qmd`.
- **External profiles:** add your verified Google Scholar, LinkedIn, ORCID, or GitHub URLs when ready. Do not add guessed links.
- **Publication status:** check under-review and in-preparation status for updates before publication.

## Notes

This is an independently styled project inspired by the structure of the reference site, not a copy of its proprietary graphics or personal content. The included `docs/` files were generated without Quarto in this environment; their content and styling match the editable Quarto project. A `quarto render` will regenerate `docs/` using the Quarto/Bootstrap page components, preserving the site content and configured styling, but may change small layout details.
