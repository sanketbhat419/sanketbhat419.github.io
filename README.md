# sanketbhat419.github.io

Personal research page — a single static `index.html` with CSS inlined and no
build step. Served by GitHub Pages at <https://sanketbhat419.github.io>.

Publications, patents, and talks are already populated from the CV. Three things
remain.

---

## 1. Remaining TODOs

Both are marked `TODO` in `index.html`:

1. **Photo** — save a square crop (~600×600) as `photo.jpg` next to
   `index.html`. Until then the avatar shows as an empty circle.
2. **Bio** — replace the `SHORT BIO GOES HERE` paragraph with 2–3 sentences in
   your own voice.
3. **CV** *(optional)* — save as `cv.pdf` next to `index.html`, or delete the
   `CV` link from the `.links` nav.

Check nothing was missed:

```bash
grep -n 'TODO\|SHORT BIO' index.html
```

### Optional: attach paper PDFs

Drop files into `papers/` and add a link inside that paper's `pub-links`:

```html
<a href="papers/Bhat2016Production.pdf">PDF</a>
```

> Only post PDFs you have the right to share. Taylor & Francis (IIE
> Transactions, IJPR) and Elsevier (JMS) generally permit the *accepted
> manuscript* after an embargo, not the typeset version. When in doubt, the DOI
> link alone is always safe.

### Adding a future publication

Copy this block into the relevant `<ol class="pubs">`. Numbering is automatic.

```html
<li class="pub">
  <span class="pub-title">PAPER TITLE</span>
  <span class="pub-authors">A. Author, <b>S. Bhat</b>, C. Author</span>
  <span class="pub-venue">VENUE, Vol. 00(0), 000–000, YEAR</span>
  <span class="pub-links">
    <a href="https://doi.org/DOI">DOI</a>
  </span>
</li>
```

### Publication entry snippet

Copy this per paper. Delete the `pub-links` or `pub-note` lines if unused.

```html
<li class="pub">
  <span class="pub-title">PAPER TITLE</span>
  <span class="pub-authors">AUTHOR, <b>YOUR NAME</b>, AUTHOR</span>
  <span class="pub-venue">JOURNAL NAME, Vol. 00(0), 000–000, YEAR</span>
  <span class="pub-links">
    <a href="https://doi.org/DOI">DOI</a>
    <a href="papers/FILENAME.pdf">PDF</a>
  </span>
  <span class="pub-note">AWARD OR PRESS MENTION</span>
</li>
```

### Preview locally

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

---

## 2. Publishing

The repo and remote are already configured, so shipping a change is just:

```bash
git add .
git commit -m "Add photo and bio"
git push
```

The live site rebuilds within about a minute.

Confirm **Settings → Pages** shows *Source: Deploy from a branch* on
`main` / `/ (root)`. That was already set for the previous Jekyll site, so it
should need no change.

### Note on the previous site

This repo previously held a `minima` Jekyll blog scaffold (Sept 2024) with one
test post. That scaffold was removed in favour of this page; the commits remain
in history, so nothing is lost:

```bash
git log --oneline          # old commits are still here
git show a423a64:index.md  # view any old file
```

A `.nojekyll` file at the root now tells GitHub Pages to skip Jekyll processing
and serve `index.html` directly.

---

## Notes & troubleshooting

- **Custom domain** (e.g. `sanketbhat.com`): add it under **Settings → Pages →
  Custom domain**, create a `CNAME` file containing just the domain, and point a
  `CNAME` DNS record at `sanketbhat419.github.io`. Enable *Enforce HTTPS* once
  the certificate is issued.
- **Changes not showing**: hard-reload (Cmd+Shift+R). Check the **Actions** tab
  for a failed *pages build and deployment* run.
- **Photo not loading**: filenames are case-sensitive on GitHub's servers.
  `Photo.JPG` will not match `photo.jpg`.
- **Dark mode** is automatic and follows the visitor's OS setting. To force one
  theme, delete the `@media (prefers-color-scheme:dark)` block in `<style>`.
- **Restyling**: every colour and the page width live in the `:root` block at the
  top of `<style>`.
- **GitHub profile README** (the panel on github.com/sanketbhat419) is a separate
  feature: create a repo named exactly `sanketbhat419`, add a `README.md`, and
  link it here.

