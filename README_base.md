# jorisberns.com

Personal academic website of Joris Berns, built with [Quarto](https://quarto.org) and deployed automatically to GitHub Pages via GitHub Actions.

## One-time setup

1. **Install Quarto locally (Windows):** download the `.msi` installer from <https://quarto.org/docs/get-started/>. No R/Python setup is required to render this site.
2. **Create the repository:** create a GitHub repo (e.g. `jorisberns.com`), then from this folder:
   ```powershell
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/jlmberns/jorisberns.com.git
   git push -u origin main
   ```
3. **Enable Pages:** on GitHub → repo → *Settings* → *Pages* → set **Source** to **GitHub Actions**. The included workflow (`.github/workflows/publish.yml`) renders and deploys on every push to `main`.
4. **Custom domain:** in the same Pages settings, enter `jorisberns.com` as the custom domain and enable *Enforce HTTPS*. At your DNS provider, point the apex domain to GitHub Pages with four `A` records (`185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`) and add a `CNAME` record for `www` pointing to `jlmberns.github.io`. The `CNAME` file in this repo keeps the domain binding across deployments.
5. **Retire the old sites:** delete or archive the old Netlify project (`jorisberns.netlify.app`) — it still describes you as a 2021 job-market candidate and competes in search results — and archive the old `jlmberns.github.io` repo once the domain has switched over.

## Fill in before first deployment (TODOs)

- `index.qmd`: replace `YOUR_SCHOLAR_ID` (Google Scholar) and `YOUR-ORCID-ID` (ORCID) in the identity bar, or delete those two links.
- `data/resources.yml`: the two entries are placeholders — point them at real repositories or remove them.
- Verify the two DOI links in `data/publications.yml` resolve to your proceedings.

## Routine updates (the whole point)

| To add… | Edit… |
|---|---|
| A news item | `data/news.yml` (copy a block, edit two lines) |
| A publication | `data/publications.yml` |
| A talk | `data/talks.yml` |
| A code release | `data/resources.yml` |
| A blog post | new folder in `blog/posts/<slug>/index.qmd` |
| A new CV | overwrite `assets/Berns_CV.pdf` |

Then `git add -A && git commit -m "update" && git push` — the site rebuilds itself in ~1 minute. Sorting (newest first) is automatic; you never touch HTML.

To preview locally before pushing: `quarto preview` in the project root.

## Structure

```
_quarto.yml          site config, navigation, theme
styles.scss          all design tokens and styling
index.qmd            About / landing page
research.qmd         projects + publications (from data/)
teaching.qmd         courses + supervision
talks.qmd            talks (from data/) + service + grants
resources.qmd        code & packages (from data/)
blog/                listing + posts
cv.qmd               embedded + downloadable PDF
data/*.yml           the files you actually edit
templates/*.ejs      how data files render (rarely touched)
```
