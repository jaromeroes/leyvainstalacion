# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Website for **Leyva Instalaciones**, a local electrical installation business in Granada, Spain. Built with Astro 6 and deployed on Netlify. All content is in Spanish.

## Commands

- `npm run dev` — Dev server at localhost:4321
- `npm run build` — Production build to `./dist/`
- `npm run preview` — Preview production build locally
- Requires Node >= 22.12.0

## Architecture

- **Astro 6** static site, no UI framework integrations (pure `.astro` files)
- **Single shared layout** at `src/layouts/Layout.astro` — contains nav, footer, global CSS variables, and all shared styles (design system lives here, not in separate CSS files)
- **File-based routing** in `src/pages/`:
  - `index.astro` — Landing page with hero, services overview, about, and contact sections (anchor-based navigation: `#nosotros`, `#servicios`, `#contacto`)
  - `servicios/*.astro` — Individual service pages (reforma-vivienda, obra-nueva, domotica, industrial, comunidades, averias)
  - `blog/index.astro` — Blog listing page
  - `blog/*.astro` — Individual blog articles
- Each service and blog page duplicates a `servicios` array for cross-linking sidebar navigation
- **No components directory** — all markup is inline within page files
- Static assets in `public/` (images, favicons)

## Design System (in Layout.astro)

CSS custom properties define the palette: `--g` (green), `--gd` (green dark), `--gm` (green mid), `--m` (mint accent), `--c` (cream), `--ln` (linen), `--w` (white), `--ink` (near-black), `--mid` (gray). Fonts: Oswald (headings), DM Sans (body), DM Mono (kickers/small labels).

## Deployment

Netlify config in `netlify.toml`: builds with `npm run build`, publishes `dist/`. Note: Netlify uses Node 20 (set in `netlify.toml`) while `package.json` engines require >= 22.12.0.
