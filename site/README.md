# Grand Circle Studio — site

Static front page for Grand Circle Studio, websites for small businesses in
Corona, CA. No build step, no JavaScript, no dependencies. Deployed to GitHub
Pages by `.github/workflows/pages.yml` on every push to `main` that touches
`site/`.

Live at: https://saddlebackcreative.github.io/saddlebackcreative/

> This repository is also the GitHub **profile README** repo. The root
> `README.md` renders on the profile — leave it alone. Everything for the site
> lives under `site/`.

## Files

| Path | What it is |
| --- | --- |
| `index.html` | The whole front page. |
| `404.html` | Not-found page, same design system. |
| `styles.css` | Tokens → primitives → sections → responsive. |
| `assets/favicon.svg` | The sticker mark. |

All asset paths are **relative** — the site is served from a project-pages
subpath (`/saddlebackcreative/`), so absolute paths would break. Keep them
relative.

## Design system (neo-brutalism)

Single light palette, no dark mode.

| Token | Value |
| --- | --- |
| `--background` | `#FFFDF5` cream |
| `--foreground` | `#000000` |
| `--surface` | `#FFFFFF` |
| `--accent` | `#FF6B6B` red |
| `--secondary` | `#FFD93D` yellow |
| `--muted` | `#C4B5FD` violet |

- **Type:** Space Grotesk (Google Fonts).
- **Radius:** binary — `0` or `9999px`. Nothing in between.
- **Borders:** 2 / 4 (default) / 8px, always pure black.
- **Shadows:** hard offsets 4/8/12/16px, zero blur, plus `--shadow-invert`
  (white, for elements sitting on black blocks).
- **Spacing:** `--space-1`…`--space-16` on an 8px grid.

### Two deliberate deviations from the spec

1. **Black text on red, never white.** White on `#FF6B6B` is 2.8:1 and fails
   WCAG AA; black is 7.6:1. Contrast won.
2. **Weight 900 renders at 700.** Space Grotesk only ships 300–700.

## Editing

Change the look in `:root` in `styles.css`. Never inline.

Primitives: `.btn` (`--primary` / `--secondary` / `--violet` / `--pill` /
`--invert`), `.card` (+ `.card__badge`), `.badge`, `.label`, and the
`.halftone` / `.graph` textures.

Sections color-block in rotation — cream → yellow → cream + graph → violet →
black → cream + halftone → red → yellow footer — each closing with an 8px
black border.

Interactions: buttons translate 3px and drop their shadow on `:active`; cards
lift 4px and step their shadow up on hover; everything is disabled under
`prefers-reduced-motion`.

## Accessibility

Semantic landmarks, a skip link, 44px+ touch targets, black-on-color text
throughout, and motion off under `prefers-reduced-motion`.

## Placeholders to fill before launch

- `[YOUR PHONE]` — also inside every `tel:` href.
- `[YOUR EMAIL]`
- `$[YOUR PRICE]`
- The six project cards are **examples**. Swap them for real clients. No
  invented stats anywhere — keep it that way.

## Deploy

GitHub → Settings → Pages → **Source: GitHub Actions** (not "Deploy from a
branch"). The workflow handles the rest.
