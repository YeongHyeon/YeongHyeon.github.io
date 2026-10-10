# Changelog

Work history for this site. Newest first.

## 2026-10-10

### Repository cleanup
- Removed files nothing referenced: `_includes/embed.html`, `_includes/archive.html`, `archive.html`, `_layouts/page.html`, the Font Awesome icon data and SVG sprite, the bundled PT Sans fonts, 5 unreferenced images, and 14 unreferenced PDFs.
- Trimmed KaTeX to the files the layout loads (`katex.min.css`, `katex.min.js`, `contrib/auto-render.min.js`, woff2 fonts).
- Removed unused config keys (`show_excerpts`, `show_frame`, `show_sidebar`, `minimal`, `excerpt_separator`, `comments`) and the matching comment-system hooks in the layouts.
- Fixed a stray HTML comment inside the YAML front matter of `tags.html`.
- CV links now use `relative_url` instead of a hardcoded host.
- Gemfile now uses the `github-pages` gem so local builds match the GitHub Pages builder.
- Added `README.md` and this changelog.

### Build fix
- GitHub Pages builds failed in the Sass step: Ruby Sass rejects trailing `//` comments on variable declarations in `_sass/index.sass`. Comments moved to their own lines.

### Independence from the contrast theme
- Removed `UNLICENSE.txt` inherited from niklasbuschmann/contrast. The repo has no theme dependency: all layouts, includes, and styles are vendored.

### Initial publish
- Pushed the site to `YeongHyeon/YeongHyeon.github.io` as a fresh repository with no upstream history.
