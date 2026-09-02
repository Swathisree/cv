# Personal CV website — Swathisree Sreepada

A clean, minimal, single-page CV website ready to host free on **GitHub Pages**.

## What's in this folder

```
cv_website/
├── index.html              ← the English site (self-contained, all CSS inline)
├── fr/index.html           ← the French site, served at /cv/fr/
├── photo.jpg               ← profile photo (shared by both pages)
├── Swathisree_Sreepada_CV_ATS.pdf              ← downloadable CV, English (ATS)
├── Swathisree_Sreepada_CoverLetter_ATS.pdf     ← downloadable cover letter, English (ATS)
├── Swathisree_Sreepada_CV_ATS_FR.pdf           ← downloadable CV, French (ATS)
├── Swathisree_Sreepada_CoverLetter_ATS_FR.pdf  ← downloadable cover letter, French (ATS)
├── .nojekyll               ← tells GitHub Pages to skip Jekyll processing
└── README.md               ← this file
```

## The two language versions

English lives at `/cv/`, French at `/cv/fr/`, and each page has an `EN`/`FR` chip in
the nav bar linking to the other. English stays at the root on purpose — both cover
letters print `swathisree.github.io/cv` as the contact URL, so that address has to keep
resolving.

Each page is **self-contained with its own inline CSS**, deliberately: if a regenerated
`index.html` ever overwrites the English page, the French one keeps working. The trade-off
is that a styling change has to be applied to both files.

The French page's assets are referenced with `../` since it sits one directory down. Its
text comes from `Swathisree_CV_ATS_FR.pdf`, so if you retranslate the CV, update the page
to match.

## Preview it locally first

Open `index.html` in any browser — double-click it, or from a terminal:

```
open index.html
```

## Publish on GitHub Pages (free)

There are two common patterns. Pick one.

### Option A — Personal site at `https://<username>.github.io`

The simplest, gives you a clean top-level URL.

1. On GitHub, create a **new public repository** named exactly `<your-username>.github.io`
   (e.g. if your GitHub username is `swathisree`, name it `swathisree.github.io`).
2. In a terminal, from **inside this `cv_website` folder**, run:

   ```bash
   git init
   git add .
   git commit -m "Initial CV site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
   git push -u origin main
   ```
3. Go to the repo on GitHub → **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to `Deploy from a branch`,
   **Branch** to `main`, folder `/ (root)`, then click **Save**.
5. Wait 1–2 minutes. Your site will be live at
   `https://<your-username>.github.io`.

### Option B — Project site at `https://<username>.github.io/cv`

Use this if you want to keep the personal `github.io` URL for something else.

1. Create a new public repo, e.g. `cv` (any name works).
2. From inside this `cv_website` folder, run:

   ```bash
   git init
   git add .
   git commit -m "Initial CV site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/cv.git
   git push -u origin main
   ```
3. Repo → **Settings → Pages** → Source `main`, folder `/ (root)`, Save.
4. Live at `https://<your-username>.github.io/cv/`.

## Editing the site later

Everything is in `index.html`. To change text, just edit the file. To swap the CV
or cover letter PDF, replace `Swathisree_Sreepada_CV_ATS.pdf` /
`Swathisree_Sreepada_CoverLetter_ATS.pdf` with a new file of the **same name** (or
edit the `href="..."` links in `index.html` — each PDF is linked twice, once in the
nav bar and once in the hero button row). Then:

```bash
git add .
git commit -m "Update"
git push
```

Changes go live in about a minute.

## Custom domain (optional)

If you own a domain like `swathisree.com`:

1. Add a file called `CNAME` (no extension) in this folder with just the domain,
   e.g. `swathisree.com` on a single line.
2. In your domain registrar, add a CNAME record pointing your domain to
   `<your-username>.github.io`.
3. Repo → Settings → Pages → set the custom domain, tick "Enforce HTTPS".

## What's set up correctly already

- **Mobile responsive** — works on phones (nav collapses, photo scales).
- **Sticky nav** for jumping between sections.
- **SEO meta** description in `<head>`.
- **`.nojekyll`** included, so GitHub Pages won't try to run Jekyll on this folder.
- **Print-friendly** — the CSS hides the nav bar and buttons when you print
  the page, so it prints cleanly.
- **Accent color** (`#0d9488`, teal) defined once in a CSS variable — change
  `--accent` in the `<style>` block to re-theme the whole site in one edit.

## Notes

- The site font (Inter + JetBrains Mono) is loaded from Google Fonts. If you
  prefer no external requests, delete the two `<link ...>` tags in `<head>`
  — the site falls back to system fonts.
- No JavaScript frameworks, no build step, no dependencies. It's just HTML +
  CSS in one file.
