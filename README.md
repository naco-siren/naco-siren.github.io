# Naco Siren's Blog

Personal blog & app support pages, powered by [Hexo](https://hexo.io/) with the [Cactus](https://github.com/probberechts/cactus-dark) theme.

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
```

The server watches for file changes and auto-reloads.

## Cheatsheet

### Posts

```bash
npx hexo new "My Post Title"           # New post   -> source/_posts/My-Post-Title.md
npx hexo new draft "WIP Idea"          # New draft  -> source/_drafts/WIP-Idea.md
npx hexo publish "WIP Idea"            # Promote draft to post
```

### Pages (for app support pages, about, etc.)

```bash
npx hexo new page "privacy-policy"     # New page -> source/privacy-policy/index.md
npx hexo new page "support"            # New page -> source/support/index.md
```

Pages are accessible at `/<page-name>/` (e.g., `/privacy-policy/`).

To add a page to the nav bar, edit `themes/cactus/_config.yml`:

```yaml
nav:
  Home: /
  Support: /support/
  Privacy: /privacy-policy/
```

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
layout: post        # or "page" for standalone pages
---

Your content here in **Markdown**.
```

For a standalone page with no post-like metadata (date, tags), use `layout: page` or simply create it via `hexo new page`.

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
npx hexo clean               # Clear cache & generated files (useful when things look stale)
```

### Theme Config

Theme settings live in `themes/cactus/_config.yml`:

- `colorscheme`: `dark`, `light`, `classic`, `white`
- `nav`: navigation menu links
- `social_links`: GitHub, Twitter, etc.
- `posts_overview.post_count`: number of posts on home page

### Quick Combos

```bash
npx hexo clean && npx hexo server   # Nuclear restart when something looks off
npx hexo clean && npx hexo deploy   # Clean build + deploy
```

## Project Structure

```
_config.yml          # Site config (title, URL, permalink, deploy target)
source/_posts/       # Blog posts
source/_drafts/      # Unpublished drafts
source/*/index.md    # Standalone pages
themes/cactus/       # Active theme
scaffolds/           # Templates for hexo new
```
