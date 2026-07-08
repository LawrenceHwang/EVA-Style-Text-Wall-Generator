# EVA-Style Text Wall Generator

Generate Neon Genesis Evangelion–style typographic title cards and text
walls entirely in the browser — no build step, no dependencies, no server.
Everything renders live to an HTML `<canvas>` and exports as a PNG.

**Live demo:** enable GitHub Pages for this repo (see [Deployment](#deployment))
and it will be published at `https://<your-username>.github.io/<your-repo>/`.

- [`index.html`](index.html) — the main generator: pick an arrangement mode
  (justified title card, mixed text wall, or the fully random "Advanced Wall"
  packer), tweak colors/canvas size/font, and download a PNG.
- [`slideshow.html`](slideshow.html) — a distraction-free slideshow that
  continuously generates new random "Advanced Wall" compositions at an
  adjustable interval, with an optional fullscreen mode. Press any key to stop.

## Features

- **EVA Title Card** — classic justified/flush-edge title layout with small
  caption lines (prefix a line with `*`).
- **EVA Text Wall** — procedurally collaged rows/columns of mixed horizontal
  and vertical text.
- **EVA Advanced Wall** — each input line is treated as one "unit" with its
  own randomized size and orientation (horizontal or vertical), packed onto
  the canvas with strict no-overlap collision detection. Adjustable fill
  amount, tightness, and horizontal/vertical ratio, plus an "I'm Feeling
  Lucky" randomizer.
- **Slideshow mode** — the Advanced Wall algorithm on a timer (10 ms – 300 s),
  with a drift-corrected `requestAnimationFrame` scheduler for smooth,
  accurate pacing, and a fullscreen toggle.
- Bilingual UI (English / Traditional Chinese), custom canvas presets, and
  PNG export.

## Getting started

This is a static site — just open the HTML files in a browser:

```bash
open index.html
```

Or serve it locally (recommended, since some browsers restrict canvas/font
behavior on `file://` URLs):

```bash
npm start   # runs `npx serve .` on http://localhost:8642
```

Any static file server works equally well (`python3 -m http.server`, etc.).

## Deployment

This repo deploys to **GitHub Pages via GitHub Actions**
([.github/workflows/deploy.yml](.github/workflows/deploy.yml)). To enable it:

1. Push this repo to GitHub.
2. Go to **Settings → Pages** and set **Source** to **GitHub Actions**.
3. Push to `main` (or run the workflow manually from the **Actions** tab).

The workflow uploads the repository root as the Pages artifact and deploys
it — no build step is required.

## Project structure

```
.
├── index.html                  # Main generator (all arrangement modes)
├── slideshow.html               # Random Advanced Wall slideshow
├── .github/workflows/deploy.yml # GitHub Pages deployment
├── .nojekyll                    # Serve as plain static files
├── LICENSE
└── README.md
```

## Contributing

Issues and pull requests are welcome. Since there's no build step, please
test changes by opening the affected page directly in a browser before
submitting.

## License

[MIT](LICENSE)
