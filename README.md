# alorasmith

Landing page for [alorasmith.com](https://alorasmith.com), hosted on GitHub Pages.

A single self-contained `index.html`: no build step, no dependencies beyond the Fredoka font from Google Fonts. All artwork is inline SVG, so it is easy to edit by hand.

## What's on the page

Alora's name in big cream lettering on a pink panel, surrounded by things she loves. Tap a character and it reacts.

| Theme | Character | Tap behavior |
|---|---|---|
| Gymnastics | Purple ninja in a mid-kick stance (ninja gymnastics classes), traced from reference art | Hops |
| Ballet | Vector tutu with a purple bodice and bow | Twirls |
| Baking | Cupcake with cherry and sprinkles | Pops |
| KPop Demon Hunters | Derpy the tiger in a white cowboy hat | Pops |
| Music | Floating notes and sparkles | Decoration only |

Animations respect `prefers-reduced-motion`.

## Structure

- `index.html`: page markup, styles and SVG symbols (`<symbol id="ninja">`, `tutu`, `cupcake`, `tiger`, `note1`, `note2`, `sparkle`)
- `favicon.svg`, `favicon-32.png`, `favicon.ico`, `apple-touch-icon.png`: the tab icon (Derpy the tiger, cropped to his face; PNG/ICO versions are for Safari and home screens)
- `CNAME`: custom domain for GitHub Pages (`alorasmith.com`)

## Ninja artwork

The ninja is the one character that is not hand-coded: it was traced from a reference illustration into SVG with [vtracer](https://github.com/visioncortex/vtracer) (stacked color layers, 6-bit color, speckle filter 12), white background removed. The traced paths live in `<symbol id="ninja">` in `index.html` (about 160 KB, gzipped by GitHub Pages). To redo it, crop the reference, upscale it 3x, and run vtracer again with the same settings.

## Editing

- Colors are CSS variables at the top of the `<style>` block (`--page`, `--panel`, `--blob`, `--cream`, `--coral`).
- To add a character, define a `<symbol>` in the hidden SVG at the top of `<body>`, add a `<button class="char ...">` inside `.stage`, and position it with a `.char.<name>` rule.
- To make a character do something special on tap, add it to the `timed` map in the script at the bottom (name to CSS class) and define the animation.

## Hosting and DNS

Served by GitHub Pages from `main` (`/`). DNS is managed in Squarespace:

| Type | Host | Value |
|---|---|---|
| A | `@` | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| CNAME | `www` | `0n11san.github.io` |

Enforce HTTPS in the repo's Pages settings once GitHub has issued the certificate.

Sibling site: [ethanlsmith.com](https://ethanlsmith.com), built the same way.
