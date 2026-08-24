# Flipbook Prototype — Build Task

Build a PDF.js-based flipbook prototype that replicates FlipHTML5's magazine template style and features.

## Goal
Create a standalone web app that:
1. Uses PDF.js to render PDF pages
2. Has realistic 3D page-flip animations (like FlipHTML5)
3. Has page-flip sound effects
4. Mimics the FlipHTML5 magazine template look and feel
5. Is deployable to GitHub Pages

## FlipHTML5 Reference
- Site: https://fliphtml5.com/templates/magazine/
- Key features to replicate:
  - **3D page flip animation** — pages turn with a realistic curl/fold effect, not just slide
  - **Page flip sound** — subtle paper whoosh on each page turn
  - **Two-page spread** — magazine shows left+right pages side by side
  - **Hard cover** — first/last pages have a rigid "hardcover" flip effect
  - **Zoom** — click to zoom into page content, pinch on mobile
  - **Thumbnail navigation** — grid of page thumbnails
  - **Table of contents** — clickable chapter navigation
  - **Fullscreen mode** — button to enter fullscreen
  - **Page counter** — current page / total pages
  - **Navigation arrows** — left/right click areas on the book edges
  - **Progress bar** — visual reading progress
  - **Toolbar** — top bar with buttons (thumbnails, TOC, zoom, fullscreen, share, download)
  - **Background** — magazine template uses a clean light background with the book centered
  - **Shadow effects** — pages cast shadows on each other during flip
  - **Magazine aesthetic** — glossy, professional, high-quality look

## Visual Design (Critical)
- **Background:** Light gradient (white to very light gray) like FlipHTML5 magazine template
- **Book:** Centered with realistic drop shadow
- **Pages:** White with slight texture, rounded outer corners
- **Shadows:** Dynamic shadows during page flip (the turning page casts shadow on pages beneath)
- **Cover:** Slightly larger than inner pages, with sheen/gloss effect
- **Toolbar:** Minimal, floating, semi-transparent dark bar at top
- **Navigation:** Large invisible click zones on left/right sides of the book
- **Page corners:** Slight curl hint on bottom-right of right page (hover effect)

## Animation Details
The page flip should use CSS 3D transforms:
- `transform: rotateY()` for the flip
- `transform-style: preserve-3d` for proper 3D rendering
- `perspective` on the container for depth
- The flipping page has a gradient overlay that shifts during rotation to simulate lighting
- Shadow gradient on the page beneath that grows/shrinks during flip
- Two phases: forward flip (rotateY 0 → -180deg) and the shadow follows
- Easing: cubic-bezier for natural paper feel (not linear, not ease-in-out — more like ease-out with slight overshoot)
- Duration: ~800ms for a natural flip

## Sound Effects
- Use Web Audio API to generate a subtle paper flip sound (no external files needed)
- A short "whoosh" with filtered noise — 200ms, low volume
- Play on each page turn (forward and backward)

## Tech Stack
- **PDF.js** (from CDN) — for PDF rendering
- **Vanilla JS + CSS** — no framework needed for prototype
- **Web Audio API** — for sound effects (generated, no files)
- **CSS 3D transforms** — for page flip animation
- Single `index.html` file with inline CSS and JS — simplest for GitHub Pages

## Sample PDF
Use a sample PDF URL for testing. Use the PDF.js sample: `https://mozilla.github.io/pdf.js/web/compressed.tracemonkey-pldi-09.pdf` as default, but allow loading any PDF via URL parameter `?pdf=URL`

## File Structure
```
flipbook-proto/
├── index.html          # Main app (single file with inline CSS/JS)
├── README.md
└── .github/
    └── workflows/
        └── deploy.yml  # GitHub Pages deploy
```

## Acceptance Criteria
1. Opens with a sample PDF loaded
2. Shows two-page spread (magazine style)
3. Clicking right side flips forward with 3D animation + sound
4. Clicking left side flips backward with 3D animation + sound
5. Toolbar with: thumbnails toggle, zoom, fullscreen, page counter
6. Thumbnail grid overlay shows all pages
7. Zoom mode: click page to zoom, drag to pan, click again to unzoom
8. Fullscreen mode works
9. Page counter shows "X / Y" and updates on flip
10. Navigation arrows (visible on hover)
11. Shadows during flip animation
12. Magazine-style visual polish (background, shadows, book centered)
13. Responsive — works on mobile (single page view on narrow screens)
14. Deployed to GitHub Pages

## Repository
- Create repo: `cmcintosh/flipbook-proto`
- Set up GitHub Pages deployment via GitHub Actions
- Push all code

## After Building
1. Take screenshots of the result at key states (initial load, mid-flip, thumbnail view, zoomed)
2. Verify the look matches FlipHTML5 magazine template aesthetic
3. Report what's working and what might need polish