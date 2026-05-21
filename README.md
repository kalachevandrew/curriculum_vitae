# kalachevandrew.github.io

Personal site + writing space, built with Jekyll, deployed to GitHub Pages.
Working folder name: `260521_blog_cv/`. Remote repo name: `kalachevandrew.github.io`.

---

## Local development

Requires Ruby 3.x and Bundler.

```bash
cd /Users/andrei.kalachev/ai_slop/260521_blog_cv
bundle install
bundle exec jekyll serve
```

Site runs at <http://localhost:4000>. Live-reload on file changes.

If `bundle install` complains about a missing Ruby version, install via Homebrew:
```bash
brew install ruby
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
exec zsh
gem install bundler
```

---

## Adding a post (article, thought, or project)

Create a file in `_posts/` named `YYYY-MM-DD-slug.md` (or `.html`):

```markdown
---
layout: post
title: "How I shipped X"
date: 2026-05-21
type: article    # article | thought | project
excerpt: "Short 1-2 sentence summary that appears on the home page card."
---

Write the body in Markdown (or raw HTML — both work).
```

The post auto-appears in the **Writing & Projects** section on the home page
(most recent 6 shown) and lives at its own URL like
`/writing/2026/how-i-shipped-x/`.

The "type" field controls the colored chip on the card:
- `article` → blue (v2)
- `thought` → teal (v3)
- `project` → green (v4)

---

## Deploying to GitHub Pages

One-time setup:

```bash
cd /Users/andrei.kalachev/ai_slop/260521_blog_cv
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin git@github.com:kalachevandrew/kalachevandrew.github.io.git
git push -u origin main
```

Then in GitHub: **Settings → Pages → Build and deployment**:
- Source: `Deploy from a branch`
- Branch: `main` / `/ (root)`

After ~60 seconds the site is live at <https://kalachevandrew.github.io>.

For subsequent updates:
```bash
git add .
git commit -m "describe change"
git push
```

---

## Printing the page as a CV (PDF)

The site is dual-purpose: on screen it's responsive, but `Cmd-P` / `Ctrl-P`
renders the original print CV exactly. The Writing section and site footer
are hidden in print mode.

In Chrome's print dialog: enable **Background graphics** so the viridis
dots and highlights print in color. Save as PDF, fits to a single A4 page.

---

## File map

```
260521_blog_cv/
├── _config.yml           # site metadata, plugins, permalinks
├── Gemfile                # github-pages gem + webrick
├── _layouts/
│   ├── default.html       # base shell (head + footer)
│   └── post.html          # article layout
├── _includes/
│   └── head.html          # meta, og, favicon, stylesheet
├── _posts/                # your writing lives here
├── assets/
│   ├── css/style.css      # all styling (viridis palette)
│   └── favicon.svg        # viridis-gradient dot
├── index.html             # CV + Writing section
├── 404.html               # not-found page
└── README.md              # this file
```

---

## Visual notes

- Viridis palette stops: `#440154 → #3b528b → #21918c → #5ec962 → #fde725`.
- Numbered sections via CSS `counter-reset` on body + `counter-increment` on
  `.section-title`. Adding/removing a section shifts the numbers automatically.
- Job timeline dot colors are positional (`.job:nth-child(n)`). If you reorder
  the four job blocks in `index.html`, the dot colors will follow positions
  1→5, 2→4, 3→3, 4→2 by design.
