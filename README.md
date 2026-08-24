# Flipbook Prototype

A PDF.js-based flipbook that replicates FlipHTML5's magazine template aesthetic.

## Features

- **3D page-flip animation** — CSS 3D transforms with realistic rotateY, preserve-3d, perspective
- **Page-flip sound** — Generated via Web Audio API (filtered noise burst, no external files)
- **Two-page magazine spread** — Side-by-side pages like a real magazine
- **Hardcover effect** — First/last pages have a rigid cover with gloss/shine
- **Dynamic shadows** — Pages cast shadows during flip animation
- **Page texture** — Subtle repeating texture for paper realism
- **Toolbar** — Thumbnails, TOC, zoom, fullscreen, page counter, download
- **Thumbnail grid** — Visual overview of all pages with click-to-navigate
- **Table of contents** — Built from PDF outline (or auto-generated)
- **Zoom mode** — Click to zoom, drag to pan, pinch on mobile, scroll wheel to zoom
- **Fullscreen mode** — One-click fullscreen
- **Navigation** — Click zones, arrow keys, on-screen arrows, swipe on mobile
- **Progress bar** — Visual reading progress at bottom
- **URL parameter** — Load any PDF via `?pdf=URL`
- **Mobile responsive** — Single-page view on narrow screens with swipe navigation

## Usage

### Default PDF
```
https://cmcintosh.github.io/flipbook-proto/
```

### Custom PDF
```
https://cmcintosh.github.io/flipbook-proto/?pdf=https://example.com/your.pdf
```

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| → / Space | Next page |
| ← | Previous page |
| F | Fullscreen |
| Z | Zoom |
| T | Thumbnails |
| Esc | Close panels / exit zoom |

## Tech Stack

- **PDF.js** (CDN) — PDF rendering
- **Vanilla JS + CSS** — No framework
- **Web Audio API** — Generated page-flip sound
- **CSS 3D transforms** — Page flip animation
- **GitHub Pages** — Hosting via GitHub Actions

## File Structure

```
flipbook-proto/
├── index.html          # Main app (single file, inline CSS/JS)
├── README.md
└── .github/
    └── workflows/
        └── deploy.yml  # GitHub Pages deploy
```

## License

MIT