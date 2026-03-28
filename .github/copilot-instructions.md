---
name: Mona Mayhem project
description: "Astro 5 project with Node.js adapter. Build & dev commands: `npm run dev` (dev server), `npm run build` (production build), `npm run preview` (local preview). Key paths: `src/pages/` (routes), `src/pages/api/` (API endpoints). Use `.astro` files for pages (Astro components) and `.ts` for API routes."
---

# Mona Mayhem — Copilot Instructions

## Project Overview

**Mona Mayhem** is an Astro 5 web application with Node.js server-side rendering that builds a GitHub Contribution Battle Arena. Users compare GitHub contribution graphs in a retro arcade-themed interface.

- **Framework:** Astro 5.14.4 with `@astrojs/node` adapter
- **Rendering:** Server-side (SSR) with Node.js adapter in standalone mode
- **Language:** TypeScript (configured via `tsconfig.json`)

## Development Workflow

### Common Commands

| Command | Purpose |
|---------|---------|
| `npm run dev` | Start dev server (hot reload) on `localhost:3000` |
| `npm run build` | Build for production (outputs optimized site) |
| `npm run preview` | Locally preview the production build |
| `npm run astro` | Run Astro CLI directly for advanced tasks |

### Development Tips

- **Dev server auto-reloads** when files change (`.astro`, `.ts`, CSS)
- **API routes** in `src/pages/api/` are automatically routed (e.g., `src/pages/api/contributions/[username].ts` → `/api/contributions/:username`)
- **Build output** goes to `dist/` (add to `.gitignore` if not already)

## File Structure

```
src/pages/
├── index.astro          # Homepage (route: /)
└── api/
    └── contributions/
        └── [username].ts # Dynamic API endpoint for fetching user contributions
```

## Astro Best Practices

### Pages & Routing

- **`.astro` files** in `src/pages/` create routes automatically (file-based routing)
- **Dynamic routes** use `[param]` syntax (e.g., `[username].ts` → `GET /api/contributions/:username`)
- **Component structure:** Use `export const preload = true` in API routes when data is needed before rendering

### Server-Side Rendering (SSR)

- With Node.js adapter, all pages render on the server by default
- Use `export function get()` or `export function post()` in API routes for HTTP handlers
- Import and use utilities from `astro:server` for server-specific logic

### Styling & Assets

- **Global CSS:** Place in `src/` and import into layout/pages (e.g., `import '../styles.css'`)
- **Component scoping:** Styles in `<style>` blocks inside `.astro` files are scoped to that component
- **Public assets:** Place static files in `public/` — they're served as-is

### Component Development

- **Astro components** (`.astro` files) are server-rendered by default
- Use `---` frontmatter fence to write server-side JavaScript (imports, data fetching, utils)
- HTML template comes after the frontmatter fence
- Export props via `interface Props {}` for type safety

## Key Conventions

- **TypeScript optional** — all `.ts` files support TypeScript natively
- **Environment variables:** Store in `.env` and access via `import.meta.env.VARIABLE_NAME`
- **Async API routes:** Use `async` functions for data fetching to GitHub API
- **CORS:** Node.js adapter can use headers middleware if needed for API responses

## Related Documentation

- [Astro docs](https://docs.astro.build) — comprehensive reference and tutorials
- [Node.js adapter docs](https://docs.astro.build/en/guides/integrations-guide/node/) — server-specific features
- [Workshop guide](./workshop/00-overview.md) — building context and project goals
