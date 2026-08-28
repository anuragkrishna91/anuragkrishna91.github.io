# Personal academic homepage

A single-file static site. No build step, no dependencies, no framework — `index.html`
contains the markup and the stylesheet, so GitHub Pages serves it exactly as written.

---

## 1. Deploy

1. Create a new repository named **`USERNAME.github.io`**, replacing `USERNAME` with your
   GitHub username in lowercase. The name must match exactly, or Pages will serve the site
   from a subpath instead of the root.
2. Upload `index.html` to the repository root.
3. Go to **Settings → Pages**. Under *Build and deployment → Source*, choose
   **Deploy from a branch**, then select `main` and `/ (root)`.
4. Wait one to two minutes. The site appears at `https://USERNAME.github.io`.

Reference: [Quickstart for GitHub Pages](https://docs.github.com/en/pages/quickstart)

**Note on privacy:** a Pages site is public on the internet even when the repository
itself is private. Don't commit anything you wouldn't publish.
([Creating a GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site))

---

## 2. Remaining placeholders

The content is filled in and verified. Search `index.html` for `TODO` — five remain, all
housekeeping:

| Location | What to do |
|---|---|
| `<meta property="og:url">` | Your live URL once deployed |
| `cv.pdf` link in the hero | Drop `cv.pdf` in the repository root |
| `#news` comment | Confirm the two year-only 2026 dates (NRCT acceptance, ARMOR/SHINE awards) |
| `#projects` comment | Confirm each stated role (Coordinator, PI, Partner, Host supervisor) |
| NRCT publication entry | Add the full author list and DOI once published online |

Everything else — profile links, publications with full verified author lists, project
links and dates — is final.

---

## 3. Add a publication

Copy one `<li>` block inside `<ul class="pubs">`, paste it under the correct year, and edit
four things:

```html
<li>
  <p class="pub-title">Paper title in sentence case</p>
  <p class="pub-meta">
    A. Author, <span class="me">A. Krishna</span>, B. Author ·
    <em>Journal Name</em> <strong>12</strong>, 2400123 (2026)
  </p>
  <div class="pub-links">
    <a href="https://doi.org/10.xxxx/xxxxx">DOI</a>
    <a href="papers/filename.pdf">PDF</a>
  </div>
</li>
```

`<span class="me">` bolds your own name in the author list. For a new year, copy an entire
`<p class="year">…</p>` heading along with its `<ul class="pubs">`.

---

## 4. Design notes

Worth knowing before you change things.

**Palette** is taken from a device cross-section: `--fto` is glass grey, `--absorber` is the
brown-black of a perovskite film and serves as the text colour, `--gold` is the evaporated
top contact and is the only accent. All six values are declared once in `:root` — edit them
there and the whole page follows.

**Type** is Spectral for headings, IBM Plex Sans for body, IBM Plex Mono for labels,
dates and metadata. Loaded from Google Fonts; every stack has a system fallback, so the
page degrades gracefully offline.

**The hero** is purely typographic: name, a thesis line set off by a gold rule, both
affiliations, and the profile links. A portrait can be added beside it later if wanted.

**Publications** carry full author lists verified against the publisher pages, with your
name bolded via `<span class="me">`. The *Nature Reviews Clean Technology* entry has a
placeholder author line until the article is published online.

**Accessibility floor:** responsive to 360 px, keyboard focus rings on every interactive
element, `prefers-reduced-motion` disables all animation and smooth scrolling, and the SVG
carries `<title>` and `<desc>` for screen readers.

---

## 5. Optional next steps

- **Custom domain.** Add a `CNAME` file containing your domain, configure DNS with your
  registrar, then set the domain under Settings → Pages.
  ([Managing a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site))
- **Photo.** A portrait can replace or sit beside the stack diagram in the hero grid.
- **Split the CSS.** If the file gets unwieldy, move everything inside `<style>` into
  `style.css` and link it. Nothing else changes.
- **Add pages.** For a group page, teaching page, or blog, either add `group.html` alongside
  `index.html` and link it from the nav, or move to a static generator.

If you outgrow a single file, [al-folio](https://github.com/alshedivat/al-folio) and
[academicpages](https://github.com/academicpages/academicpages.github.io) are the two
established Jekyll templates for academic sites, and both build on GitHub Pages without
local tooling.
