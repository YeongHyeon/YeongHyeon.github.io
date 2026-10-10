# Changelog

Work history for this site. Newest first.

## 2026-10-10

### Design
- Footer now links to the other blogs, LiteBites and Tityra, next to Github on every page.
- Link groups on the About and Publications pages (`.links`) now share the theme toggle look: grey outline and muted text, darkening on hover.
- Links inside posts (`post`, `paper`, `slide`, `poster`) are now solid-bordered buttons (`a.btn`) in the mono-brief style; the markdown `[[label](url)]` pattern was converted to `<a class="btn">` and one empty placeholder link was dropped.
- The light/dark toggle is a single ◐ mark in a square outlined button instead of the words Dark/Light.
- Home intro is a single sentence without the current organization; the thick rule moved under it.

### Local build
- GitHub Pages needs Ruby < 4 (commonmarker). Added `vendor/` to `.gitignore`, pinned `github-pages ~> 232`, and documented Ruby 3.3 for local preview.

### Content
- Added ICASSP 2027 to the conference reviewer list on the About page.

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
