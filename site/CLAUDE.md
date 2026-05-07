# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development

No build step. Open any `.html` file directly in a browser or serve with any static server:

```bash
npx serve .
# or
python3 -m http.server 8080
```

Tailwind CSS and Inter font load via CDN, no npm install required.

## Architecture

Multi-page static marketing site for **Setbox Sistemas Digitais** (setbox.com.br).

```
site/
├── index.html          - Home: hero, client logos, business areas, CTA
├── servicos.html       - Serviços: Smartsourcing + Consultoria + Tecnologias
├── sobre.html          - Sobre: values, careers section
├── subsidiarias.html   - Subsidiárias: Urban View, Agroprocess, PJ Park
├── produtos.html       - Produtos: Integra Moda, Pigeon, Plog, RelatórioCCB
├── 404.html            - 404 error page
├── assets/             - Self-contained assets (no external image refs)
│   ├── setbox-lateral.png
│   ├── favicon.ico / favicon-*.png / apple-touch-icon.png
│   ├── logo-integramoda.png
│   ├── logo-urbanview.png
│   ├── clientes/       - 7 client logos (grayscale)
│   ├── icones/         - github.png, linkedin.png
│   ├── icones/tecnologias/ - 13 tech logos
│   └── subsidiarias/   - agroprocess.png, pjpark.png
├── DESIGN.md           - Full design system reference
└── CLAUDE.md           - This file
```

## Design System

**Color tokens in use:**

| Token | Value | Use |
|---|---|---|
| bg | `#FAFAFA` | Page background |
| bg-alt | `#F7F7F7` | Alternate section background |
| text | `#111111` | Primary text |
| muted | `#555555–#888888` | Secondary text |
| accent | `#FB0D1C` | Red - CTAs, bullets, labels, active nav |
| accent-hover | `#C4000F` | Hover state for red buttons |
| border | `#E5E5E5` | Section dividers, card borders |

**Typography:** Inter (Google Fonts, optical size 14..32, weights 300–800). `tracking-tight` or `tracking-[-0.03em]` on large headings.

**Layout:** `max-w-5xl` container, `px-4 md:px-8` horizontal padding. Two-column `grid grid-cols-1 md:grid-cols-2 gap-10 md:gap-16` for feature sections.

**Nav:** sticky, `h-14`. Items: Serviços, Sobre, Divisões, Produtos. Active page: `text-[#FB0D1C] font-medium`. Inactive: `text-[#111111] hover:opacity-50 transition-opacity hidden md:block`.

See `DESIGN.md` for full component patterns.

## Content Conventions

- Language: Brazilian Portuguese
- All main CTAs point to `mailto:contato@setbox.com.br`
- Section labels: `text-[11px] text-[#FB0D1C] font-semibold tracking-wide uppercase`
- Bullets use red arrow: `<span class="text-[#FB0D1C] flex-shrink-0 font-bold">→</span>`
- No trailing period on any title or subtitle (h1-h6)
- Never use em dash (—) anywhere — use hyphen (-) or comma
- Client logos: grayscale with `filter: grayscale(100%)`, color on hover
- Footer: always includes green status dot "Operacional" and 3-column link grid

## Nav Pattern (copy-paste)

```html
<nav class="sticky top-0 z-50 bg-[#FAFAFA] border-b border-[#E5E5E5]">
  <div class="max-w-5xl mx-auto px-4 md:px-8 h-14 flex items-center justify-between">
    <a href="index.html"><img src="assets/setbox-lateral.png" alt="Setbox" class="h-6 w-auto"></a>
    <div class="flex items-center gap-4 md:gap-7">
      <a href="smartsourcing.html" class="hidden md:block text-sm text-[#111111] hover:opacity-50 transition-opacity">Smartsourcing</a>
      <a href="consultoria.html" class="hidden md:block text-sm text-[#111111] hover:opacity-50 transition-opacity">Consultoria</a>
      <a href="sobre.html" class="hidden md:block text-sm text-[#111111] hover:opacity-50 transition-opacity">Sobre</a>
      <a href="subsidiarias.html" class="hidden md:block text-sm text-[#111111] hover:opacity-50 transition-opacity">Subsidiárias</a>
      <a href="produtos.html" class="hidden md:block text-sm text-[#111111] hover:opacity-50 transition-opacity">Produtos</a>
      <a href="mailto:contato@setbox.com.br" class="text-sm bg-[#FB0D1C] text-white px-4 py-1.5 rounded-[6px] hover:bg-[#C4000F] transition-colors font-medium whitespace-nowrap">Falar conosco</a>
    </div>
  </div>
</nav>
```

Change the active page link to: `class="hidden md:block text-sm text-[#FB0D1C] font-medium"`
