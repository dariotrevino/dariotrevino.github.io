# dariotrevino.com

My personal site: writing, a bookshelf, and what I'm working on.

Live at [dariotrevino.com](https://dariotrevino.com).

## What's on it

- **Writing**: posts grouped by topic (cybersecurity, philosophy, technology)
- **Bookshelf**: the books that changed how I think
- **Now** and **Projects**: what I'm studying and building

## How it's built

- [Jekyll](https://jekyllrb.com/) 4 with no theme. The layouts and the stylesheet are written by hand.
- Hosted on [GitHub Pages](https://pages.github.com/). Every push to `main` builds the site, checks the links with [html-proofer](https://github.com/gjtorikian/html-proofer), and deploys it.
- Plugins: `jekyll-feed`, `jekyll-seo-tag`, `jekyll-sitemap`.

## Run it locally

You need Ruby and Bundler.

```sh
bundle install
bundle exec jekyll serve
```

Then open <http://127.0.0.1:4000>.

## Where things live

| Path | What it is |
| --- | --- |
| `_posts/` | Posts, named `YYYY-MM-DD-title.md` |
| `_tabs/` | The About and Books pages |
| `_data/home.yml` | Home page text: intro, socials, Now, Projects, bookshelf |
| `_layouts/`, `_includes/` | Page templates |
| `assets/css/site.css` | All the styles |
| `assets/img/` | Images |

## Writing a post

Add a Markdown file to `_posts/` with this at the top:

```yaml
---
title: Post Title
date: 2026-01-31 09:00:00 -0600
categories: [Philosophy]
tags: [philosophy]
---
```

The first category is the post's topic on the [Writing](https://dariotrevino.com/writing/) page. A new category creates a new topic automatically.

## Contact

[info@dariotrevino.com](mailto:info@dariotrevino.com), or any of the links on the site.

## License

The writing, photos and design are © Dario Trevino. Please ask before reusing them.

A few build files come from the [Chirpy Starter](https://github.com/cotes2020/chirpy-starter) and stay under its MIT license. See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).
