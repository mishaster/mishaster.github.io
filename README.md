# Academic homepage

A single-page academic site (plain HTML + Tailwind via CDN). No build step.

## Files

| File | What it's for |
| --- | --- |
| `index.html` | The page. Edit the `CONFIG` block at the very top for contact details & file paths. |
| `publication_list.bib` | **Your publication list (BibTeX).** Add a paper = add one entry here. No HTML needed. |
| `profile.jpg` | Your portrait (square). Optional — a placeholder shows until you add it. |
| `technion-logo.png` | Affiliation logo. Optional. |
| `figures/paper-*.png` | One teaser image per paper. Optional per paper. |

## Adding a publication

Open `publication_list.bib` and add a BibTeX entry. Display order = order in the file.

```bibtex
@inproceedings{davidov2026mypaper,
  title   = {My New Paper Title},
  author  = {D. Davidov and A. Coauthor and C. Advisor},
  venue   = {NeurIPS · 2026},
  image   = {figures/paper-4.png},
  summary = {One or two sentences describing the contribution.},
  pdf     = {https://example.com/paper.pdf},
  arxiv   = {https://arxiv.org/abs/0000.00000},
  code    = {https://github.com/you/repo}
}
```

Field notes:

- **`title`** — required.
- **`author`** — names separated by `and` (standard BibTeX). Both `First Last` and
  `Last, First` work. Your own name (the `authorName` value in `index.html`'s
  `CONFIG`, default `"D. Davidov"`) is **bolded automatically** — write it the same
  way it should display.
- **`venue`** — the small grey line above the title. If omitted, it's built from
  `booktitle`/`journal` + `year`.
- **`image`** — path to the teaser figure. Optional; a placeholder box shows if omitted.
- **`summary`** — optional one-liner (you can also use `abstract`).
- **Link fields** — any of `pdf`, `arxiv`, `code`, `url`, `video`, `slides`,
  `poster`, `bibtex`, `data`, `demo`. They render as buttons in the order written,
  and the **first** one is also where the title and the figure point. Add or remove
  freely; unknown fields are ignored.
- The `@type{...}` (e.g. `@inproceedings`, `@article`) and the citation key
  (`davidov2026mypaper`) can be anything unique — they aren't shown on the page.

## Previewing locally

The page loads `publication_list.bib` with `fetch`, which browsers block when you open
the file via `file://`. To preview locally, serve the folder over HTTP:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

(On GitHub Pages it just works — no server command needed.)

## Publishing on GitHub Pages

1. Push these files to a repo.
2. Repo **Settings → Pages → Build and deployment → Deploy from a branch**, pick your
   default branch and the `/ (root)` folder.
3. The site appears at `https://<username>.github.io/<repo>/`.
