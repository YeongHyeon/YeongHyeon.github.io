# YeongHyeon.github.io

Personal site of YeongHyeon Park, published with GitHub Pages at https://yeonghyeon.github.io/.

## Layout

| Path | Purpose |
| --- | --- |
| `_config.yml` | Site title, navigation menu, footer links, plugins |
| `index.html` | Home page: intro rows plus a shuffled photo grid built from `images/thumbnails/` |
| `profile.md`, `publications.md`, `projects.md` | Static pages (`/about/`, `/publications/`, `/projects/`) |
| `_data/reviewing.yml` | Reviewing venues, first-participation dates, and conference years rendered on the About page |
| `tags.html` | Post archive grouped by tag |
| `404.html` | Not-found page |
| `_posts/` | Blog posts, `YYYY-MM-DD-slug.md` with `layout: post` and `categories: posts` |
| `_layouts/` | `default.html` (shell, header, footer, theme toggle) and `post.html` (article) |
| `_includes/` | `home.html`, `menu.html`, `meta.html`, `tags.html` |
| `_sass/`, `assets/css/index.sass` | Styles. Written in the indented Sass syntax for the Ruby Sass compiler used by GitHub Pages |
| `assets/katex/` | KaTeX (MIT) for math. Loaded only on pages with `mathjax: true` in front matter |
| `images/`, `pdfs/`, `resume/` | Static files referenced from pages and posts |

## Writing

- New post: add `_posts/YYYY-MM-DD-slug.md` with front matter `layout: post`, `categories: posts`, `title`, `tags`, and optionally `date-string` for a custom displayed date.
- Math: add `mathjax: true` to a page's front matter and write `$$ ... $$` or `\( ... \)`.
- Photos on the home page: drop image files into `images/thumbnails/`.

## Local preview

GitHub Pages builds this site with the `github-pages` gem (Jekyll 3.10). The Gemfile pins the same environment. It needs Ruby 3.x (Ruby 4 cannot install `commonmarker`), for example Homebrew `ruby@3.3`:

```sh
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000/.

Sass note: Ruby Sass rejects trailing `//` comments on variable declarations. Put comments on their own line.

## History

See `CHANGELOG.md`.
