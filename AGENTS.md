# Agent guide: select-wines-web

This repository is an [Astro](https://astro.build/) site (minimal starter). Treat **Bun** as the primary runtime and package manager for installs and scripts.

## Bun workflow

- **Install dependencies:** `bun install` (uses `bun.lock`; do not switch this project to npm/yarn/pnpm unless the team explicitly migrates lockfiles).
- **Run package scripts:** `bun run <script>` or the shorthand `bun <script>` when unambiguous (e.g. `bun dev`, `bun build`, `bun preview`).
- **Add/remove packages:** `bun add <pkg>`, `bun add -d <pkg>`, `bun remove <pkg>`.

`package.json` declares `"type": "module"` and `engines.node` `>=22.12.0`. Astro and tooling are invoked through Bun executing those scripts; `@types/bun` is available if you add Bun-specific APIs in TypeScript.

## Project layout

| Path | Role |
|------|------|
| `src/pages/` | Routes: `.astro` and `.md` files map to URLs (e.g. `index.astro` → `/`). |
| `public/` | Static assets served as-is at the site root. |
| `astro.config.mjs` | Astro configuration (`defineConfig` from `astro/config`). |
| `tsconfig.json` | Extends `astro/tsconfigs/strict`. |
| `dist/` | Production build output (from `bun build`; gitignored). |

There is no `src/components/` directory yet; create it if you add shared Astro (or framework) components.

## Commands agents should use

| Goal | Command |
|------|---------|
| Dev server (default [http://localhost:4321](http://localhost:4321)) | `bun dev` |
| Production build | `bun build` |
| Preview production build locally | `bun preview` |
| Astro CLI (`add`, `check`, etc.) | `bun astro -- <args>` e.g. `bun astro -- check` |

Defined in `package.json` `scripts`: `dev`, `build`, `preview`, and `astro`.

## Conventions

- Prefer **small, task-scoped changes**; match existing Astro and TypeScript style.
- After dependency or config changes, run `bun install` if needed and verify with `bun build` (and `bun dev` when touching UI).
- Do not commit secrets; use env vars and local `.env` patterns Astro supports when adding configuration later.

For human-oriented setup and Astro links, see `README.md`.
