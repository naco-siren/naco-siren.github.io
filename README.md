# Naco Siren's Blog

Personal blog & app support pages, powered by [Hexo](https://hexo.io/) with the [Hueman](https://github.com/ppoffice/hexo-theme-hueman) theme.

Live at: https://naco-siren.github.io

## Setup

```bash
# Requires Node.js (tested on v25+)
npm install
```

## Local Development

```bash
npx hexo server          # Start dev server at http://localhost:4000
npx hexo server -p 5000  # Use a different port
npx hexo clean && npx hexo server   # Nuclear restart when things look stale
```

The server watches for file changes and auto-reloads.

## Cheatsheet

### Posts

```bash
npx hexo new "My Post Title"           # New post   -> source/_posts/My-Post-Title.md
                                        #               source/_posts/My-Post-Title/  (asset folder)
npx hexo new draft "WIP Idea"          # New draft  -> source/_drafts/WIP-Idea.md
npx hexo publish "WIP Idea"            # Promote draft to post
```

### Pages (for app support pages, about, etc.)

```bash
npx hexo new page "privacy-policy"     # New page -> source/privacy-policy/index.md
npx hexo new page "support"            # New page -> source/support/index.md
```

Pages are accessible at `/<page-name>/` (e.g., `/privacy-policy/`).

To add a page to the nav bar, edit `_config.hueman.yml`:

```yaml
menu:
    Home: /
    About: /about/index.html
    Apps: /apps/
```

### Images in Posts

Each post gets its own asset folder (`source/_posts/<Post-Title>/`). Drop images there:

```
source/_posts/My-Post-Title/
  screenshot.png
  demo.gif
```

Reference them in the post:

```markdown
{% asset_img screenshot.png "A screenshot of the app" %}

![Also works](screenshot.png)
```

Set a **thumbnail** for the post card on the home page:

```yaml
---
thumbnail: screenshot.png
---
```

If no `thumbnail` is set, Hueman auto-picks the first image in the post.

### Front Matter

Every `.md` file starts with YAML front matter:

```yaml
---
title: My Post Title
date: 2026-04-04 12:00:00
tags:
  - iOS
  - app-update
categories:
  - Announcements
thumbnail: hero.png         # Post card image (optional)
toc: true                   # Show table-of-contents in sidebar
sticky: 1                   # Pin to top (higher number = higher)
comments: false             # Disable comments on this post
excerpt: "One-line summary" # Custom excerpt (or use <!-- more --> in body)
photos:                     # Photo gallery above post content
  - photo1.jpg
  - photo2.jpg
---

Your content here in **Markdown**.
```

For standalone pages (no date/tags), create via `hexo new page`.

### Static Files

Drop files into `source/` and they'll be copied as-is to the output:

```
source/images/app-icon.png   ->  /images/app-icon.png
source/downloads/press.zip   ->  /downloads/press.zip
```

### Build & Deploy

```bash
npx hexo generate            # Build static files to public/
npx hexo deploy              # Deploy to GitHub Pages (git push)
npx hexo clean               # Clear cache & generated files
npx hexo clean && npx hexo deploy   # Clean build + deploy
```

## Theme Customization

Personal overrides go in **`_config.hueman.yml`** (root directory). Do not edit `themes/hueman/_config.yml` directly.

### Social Links

```yaml
customize:
    social_links:
        github: https://github.com/naco-siren
        instagram: https://www.instagram.com/naco_siren
        linkedin: https://www.linkedin.com/in/nacosiren
        twitter: https://twitter.com/xxx
        rss: /atom.xml
        # Any FontAwesome brand icon name works as the key
```

### Sidebar Widgets

```yaml
widgets:
    - catalog          # Table of contents (needs toc: true in post)
    - recent_posts
    - sticky_posts     # Posts with sticky front matter
    - category
    - archive
    - tag
    - tagcloud
    - links
```

### Other Options

| Setting | Values | What it does |
|---------|--------|--------------|
| `customize.theme_color` | `'#006bde'` | Accent color (header, links) |
| `customize.sidebar` | `left` / `right` | Sidebar position |
| `customize.thumbnail` | `true` / `false` | Show post thumbnails on index |
| `plugins.lightgallery` | `true` / `false` | Click-to-zoom image lightbox |
| `plugins.mathjax` | `true` / `false` | LaTeX math rendering |
| `plugins.counter` | `true` / `false` | Word count & reading time (needs `hexo-wordcount`) |
| `comment.disqus` | shortname / empty | Disqus comments (empty = off) |
| `share` | `default` / `addtoany` | Share buttons on posts |
| `poweredby` | `true` / `false` | "Powered by Hexo" in footer |

## Switching Themes

Both Cactus and Hueman are installed. To switch:

```yaml
# In _config.yml, change:
theme: hueman    # or: cactus
```

Each theme has its own override file (`_config.hueman.yml` / `_config.cactus.yml`).

To add a new theme:
```bash
git clone https://github.com/user/hexo-theme-xxx themes/xxx
rm -rf themes/xxx/.git
cp themes/xxx/_config.yml.example themes/xxx/_config.yml  # if needed
# Then set theme: xxx in _config.yml
```

## Project Structure

```
_config.yml              # Site config (title, URL, permalink, deploy)
_config.hueman.yml       # Hueman theme overrides (personal config)
_config.cactus.yml       # Cactus theme overrides (personal config)
source/_posts/           # Blog posts (each with its own asset folder)
source/_drafts/          # Unpublished drafts
source/*/index.md        # Standalone pages
themes/hueman/           # Hueman theme (active)
themes/cactus/           # Cactus theme (backup)
scaffolds/               # Templates for hexo new
```
