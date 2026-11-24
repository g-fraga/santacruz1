# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Academic landing page for Santa Cruz Bicycles, written in a single self-contained `index.html`. No build tools, no frameworks, no package manager — open the file directly in a browser.

## Previewing the page

```bash
# Any of these work:
python3 -m http.server 8080     # then open http://localhost:8080
xdg-open index.html             # Linux — opens directly in the default browser
```

## Architecture

Everything lives in `index.html`:

- **CSS** — inline `<style>` block at the top; uses CSS custom properties defined on `:root` for the color palette (`--vermelho`, `--preto`, `--branco`, etc.) and `--angle` for the diagonal section cuts.
- **Fonts** — Google Fonts: `Barlow Condensed` for headings, buttons, labels and numbers; `Inter` for body text.
- **Sections** — each has a unique `id` used by the sticky nav (`#marca`, `#identidade`, `#tecnologia`, `#modelos`, `#personalizacao`, `#experiencia`, `#contato`). The large outlined background numbers come from a `data-num` attribute (rendered via `[data-num]::before`). Dark sections with class `angle-bottom` get a diagonal bottom edge; the next section is pulled up underneath it.
- **Responsive layout** — two `@media` breakpoints: `max-width:1000px` (tablets) and `max-width:650px` (phones).
- **JavaScript** — small inline script at the end of `<body>`: scroll reveal animations (IntersectionObserver), header shadow on scroll, and color swatch selection in Personalização.
- **Images** — all in the project root. Product photos `MY27_*.webp` have transparent backgrounds. `logo-santacruz.png` (header), `logo-santacruz-branco.png` (footer) and `favicon.png` were generated from `santa-cruz-bicycles-logo-vector.png`. `bikeazul.png`, `bikeverde.png` and `images.png` have white backgrounds, so model cards use `mix-blend-mode:multiply` to hide them.

## Notes

- `logo01.png` is actually an AVIF file with a `.png` extension and is no longer referenced by the page.
