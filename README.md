# siyuanguo.com

A plain static site — no Hugo, no build step, no dependencies. Edit the HTML, push, done.

```
index.html    the whole homepage (bio, research, publications, students, news)
bio.html      speaker bio + talk abstract  (old /bio/ URL redirects here)
style.css     all styling; the dials you'd want are at the very top in :root
img/          avatar
uploads/      CV and talk PDFs (same paths as the old site, so old links still work)
```

## Previewing locally

Just double-click `index.html`. (Or `python3 -m http.server` in this folder and open
http://localhost:8000 if you want the redirects to behave exactly as in production.)

## Common edits

**Add a news item** — copy the top `<li>` in the News section of `index.html`:

```html
<li><span class="date">Sep 2026</span><span>Your news, with a <a href="https://...">link</a>.</span></li>
```

Keep newest first. Move older items down into the `<details>` block ("Earlier news") so the
page stays short.

**Add a paper** — copy one `<li>` in the publications list:

```html
<li>
  <a class="pub-title" href="https://arxiv.org/abs/XXXX.XXXXX">Paper title</a>
  <span class="pub-authors">Author One, Siyuan Guo, Author Three</span>
  <span class="pub-venue"><em>NeurIPS</em>, 2026 <span class="badge">Oral</span></span>
</li>
```

The `<span class="badge">` is optional — use it for orals, spotlights, awards.

**Add a student** — copy one `<li>` in the Students section. The `<span class="work">` line
is optional.

**Change the look** — everything is in the `:root` block at the top of `style.css`:

| Variable | What it does |
|---|---|
| `--accent` | link / badge colour (currently warm sienna) |
| `--bg`, `--ink` | page background and text colour |
| `--measure` | text column width — the main readability dial |
| `--serif`, `--sans` | font stacks |
| `--leading` | line height |

Dark mode is handled automatically by the `@media (prefers-color-scheme: dark)` block right
below `:root`.

## Deploying

`.github/workflows/deploy.yml` publishes the repo as-is to GitHub Pages on every push to
`main`. In **Settings → Pages**, the source should be **GitHub Actions**. `CNAME` keeps the
custom domain siyuanguo.com.

## Migrating from the old Hugo Blox site

When you copy these files into the repo, delete the old framework files — they are no longer
used: `config/`, `layouts/`, `content/`, `assets/`, `data/`, `static/`, `go.mod`, `go.sum`,
`theme.toml`, `netlify.toml`, `academic.Rproj`, `preview.png`, `images/`, and the old
`.github/workflows/publish.yaml`.

Old URLs that still work: `/bio/` (redirects to `/bio.html`) and `/uploads/CV.pdf`.
