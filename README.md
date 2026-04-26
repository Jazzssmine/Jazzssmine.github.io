# yian-wang.github.io

Personal site for Yian Wang. Single static HTML file, no build step.

## Files

```
site/
├── index.html        ← the whole site
├── assets/
│   ├── photo.png     ← (add your photo here, ~400×500 works well; rename to photo.jpg and update index.html if you prefer JPG)
│   └── cv.pdf        ← (add your CV here)
└── README.md
```

## Edit content

Open `index.html` in any editor. Everything is plain HTML — find the section
you want to change (search for `<!-- 01 About -->`, `<!-- 03 News -->`, etc.)
and edit the text directly. No framework, no compilation.

To add a news item, copy any `<li>` inside `<ul class="news">` and edit it:

```html
<li><time>2026·05</time><span>Your news here.</span></li>
```

To add a publication, copy any `<article class="pub">` block and edit it.

## Deploy to GitHub Pages

1. Create a new public repo on GitHub named `<yourusername>.github.io`
   (e.g. `yian-wang.github.io`).
2. Copy the contents of this `site/` folder into the repo root (so
   `index.html` lives at the top level, not inside a `site/` subfolder).
3. Commit and push:
   ```bash
   git init
   git add .
   git commit -m "initial site"
   git branch -M main
   git remote add origin git@github.com:<yourusername>/<yourusername>.github.io.git
   git push -u origin main
   ```
4. In repo Settings → Pages, set Source = `main` branch, `/ (root)`. Save.
5. Site is live at `https://<yourusername>.github.io` within ~1 minute.

### Custom domain (optional)

Add a file `CNAME` at the repo root containing just your domain
(e.g. `yianwang.com`), then point your DNS to GitHub's IPs per their docs.

## Local preview

Just open `index.html` in a browser, or:
```bash
cd site && python3 -m http.server 8000
# then visit http://localhost:8000
```

## Design notes

- Type: IBM Plex Sans + JetBrains Mono + Caveat (handwritten accents)
- Palette: warm paper (`#f5f1e8`) + ink (`#1a1a1a`) + sepia rust accent (`#a44a2e`)
- One file, ~14KB, no JS framework, no build, no tracking
- Works offline once loaded; fonts are the only external dependency
