# Mona Mayhem — Copilot Instructions

## Project Overview

**Mona Mayhem** is a retro arcade-themed GitHub Contribution Battle Arena built with **Astro v5**. It fetches GitHub contribution data for two users and renders a head-to-head comparison. The app runs in **server-side rendering (SSR)** mode via the `@astrojs/node` adapter.

```
src/
  pages/
    index.astro                        # Main UI page
    api/
      contributions/[username].ts      # SSR API route — fetches GitHub contribution data
public/                                # Static assets (favicon, etc.)
astro.config.mjs                       # Astro config — SSR + Node adapter
```

## Build & Dev Commands

| Command | Description |
|---------|-------------|
| `npm run dev` | Start the local dev server at `http://localhost:4321` |
| `npm run build` | Production build (outputs to `dist/`) |
| `npm run preview` | Preview the production build locally |

## Tech Stack

- **Astro v5** — SSR mode (`output: 'server'`)
- **@astrojs/node** — Node.js standalone adapter
- **TypeScript** — used for API routes
- **Press Start 2P** — retro gaming Google Font for UI

## Astro Best Practices

- **Pages** live in `src/pages/`. File-based routing is automatic.
- **API routes** live in `src/pages/api/`. Export named HTTP method handlers (`GET`, `POST`, etc.) typed with `APIRoute` from `astro`.
- **Set `export const prerender = false`** on any SSR route that must not be statically pre-rendered.
- **Use the frontmatter fence (`---`)** in `.astro` files for server-side logic; keep markup below the second `---`.
- **Prefer Astro components** (`.astro`) for UI. Use framework components (React, Vue, etc.) only when interactivity requires client-side state.
- **Scope styles** with `<style>` inside `.astro` files — they are automatically scoped to the component.
- **Use `Astro.params`** to access dynamic route segments (e.g., `[username].ts` → `params.username`).
- **Use `Astro.request`** for SSR request details (headers, URL, method).
- **Keep API routes thin** — validate input, fetch external data, return a `new Response(...)` with appropriate status and `Content-Type` headers.
- **Do not import Node-only modules** at the top level of `.astro` files; use them inside the frontmatter fence or in dedicated `.ts` modules.
- **Assets in `public/`** are served as-is at the root path (e.g., `public/favicon.svg` → `/favicon.svg`).
