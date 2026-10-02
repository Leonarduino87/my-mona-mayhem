# Project Guidelines

## Overview

Mona Mayhem is an Astro 6 web app for comparing GitHub contribution activity. The app uses server output with the standalone `@astrojs/node` adapter. Route files live in `src/pages/`; the home page is `src/pages/index.astro`, and the dynamic contributions endpoint is `src/pages/api/contributions/[username].ts`.

The app is still a scaffold: the home page is a placeholder and the contributions endpoint returns 501. Keep changes focused on the Astro app and do not treat the workshop materials as application code.

## Development

- Install dependencies with `npm ci` (uses `package-lock.json`).
- Start the development server with `npm run dev`.
- Build with `npm run build`; preview the built app with `npm run preview`.
- There are currently no test or lint scripts in `package.json`.
- GitHub Pages currently publishes `docs/` and `workshop/`, not the Astro app. The app's server output requires a Node-capable host; see the deployment notes in [README.md](README.md) before changing its output mode or deployment workflow.

## Astro Conventions

- Add pages and endpoints under `src/pages/`; file names define routes. Use bracketed file names for dynamic route parameters.
- Use `.astro` files for page markup. Put server-side JavaScript or TypeScript in the frontmatter block between `---` delimiters; keep browser-only behavior in client scripts or hydrated framework components when needed.
- Type API handlers as `APIRoute` from `astro`. Keep dynamic endpoints server-rendered (`prerender = false`) and return explicit HTTP status codes and response content types.
- Preserve the strict Astro TypeScript configuration and use the existing Node standalone adapter unless the deployment target is intentionally changed.
- Avoid adding client-side hydration for content that can be rendered on the server.