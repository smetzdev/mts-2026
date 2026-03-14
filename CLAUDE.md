# Förderverein MTS Website

German-language single-page website for the "Förderverein der Meister- und Techniker aus- und -fortbildung im saarländischen Handwerk e.V."

## Tech Stack

- **Astro 6** (static site generation)
- **Tailwind CSS v4** (configured via `@theme` in `src/styles/global.css`, no tailwind.config.js)
- **TypeScript** (strict mode)
- **Node >= 22.12.0**

## Commands

```bash
npm run dev      # Start dev server on localhost:4321
npm run build    # Build static site to dist/
npm run preview  # Preview production build
```

## Project Structure

```
src/
  layouts/Layout.astro     # Main HTML shell, SEO, font loading
  components/              # All Astro components (Nav, Hero, TheClub, Card, Executives, Contact, Partners, Footer)
  data/                    # TypeScript data files (menus, club, executives, contact, partners)
  pages/                   # index.astro (homepage), impressum.astro (legal page)
  content/pages/           # Markdown content (impressum.md) via Astro content collections
  images/                  # All images (processed by Astro's built-in image optimization)
  styles/global.css        # Tailwind theme + base styles
public/                    # Static assets (PDFs, logo, favicon)
```

## Key Patterns

- **Styling**: Tailwind utility classes only. Custom colors defined in `global.css` under `@theme` (e.g., `text-primary-semidark`, `bg-grey-light`). Non-standard breakpoints use arbitrary values: `min-[690px]:`, `min-[820px]:`, etc.
- **Images**: Executive and partner images are loaded dynamically via `import.meta.glob`. Static SVGs (logo) are served from `public/`.
- **Navigation**: CSS `scroll-behavior: smooth` with anchor links. Hamburger menu uses vanilla JS in a `<script>` tag (no framework).
- **Data**: Plain TypeScript files in `src/data/`, not content collections. Image references are filename strings, resolved at build time.
- **Impressum**: Uses Astro content collections (`src/content.config.ts`) to render markdown.
- **Fonts**: Self-hosted Inter via `@fontsource/inter` (weights 300, 700). No external CDN calls.

## Design Tokens (from global.css @theme)

- Primary blue: `#1D77C9` (base), `#03437C` (semidark/headings), `#D6ECFF` (light)
- Grey body text: `#61626B`, light backgrounds: `#FCFCFD`
- Max content width: 1080px
- Font: Inter, weight 300 (body), 700 (bold/headings)
