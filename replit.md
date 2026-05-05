# ByteStor IT Services

A professional IT consultancy and services website for ByteStor, featuring pages for IT services, consulting, training, clients, news, and contact.

## Run & Operate

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **Frontend**: React + Vite (artifacts/bytestor-website)
- **Routing**: wouter
- **Styling**: Tailwind CSS v4 + tw-animate-css
- **UI components**: shadcn/ui (Radix UI)
- **Animations**: framer-motion
- **Theme**: next-themes (dark by default)
- **API framework**: Express 5 (artifacts/api-server)
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)

## Where things live

- `artifacts/bytestor-website/src/pages/` — all page components (Home, KnowUs, Services, ITServices, Consulting, Training, Clients, News, Contact)
- `artifacts/bytestor-website/src/components/Layout.tsx` — shared Navbar + Footer
- `artifacts/bytestor-website/src/index.css` — Tailwind theme + CSS variables
- `artifacts/bytestor-website/src/App.tsx` — wouter routing
- `lib/api-spec/openapi.yaml` — OpenAPI contract (source of truth for API)
- `lib/db/src/schema/` — Drizzle schema definitions

## Architecture decisions

- Dark theme by default (enforced via next-themes with `enableSystem={false}`)
- Frontend-only app — no API routes needed; the api-server scaffold is present but unused
- wouter used for client-side routing with BASE_URL prefix support
- All pages use a shared `<Layout>` wrapper with sticky Navbar and Footer
- Tailwind CSS v4 with CSS custom properties for theming (light + dark modes)

## Product

- **Home**: Hero section, stats counter, services overview, CTA
- **Know Us**: Company story, mission, team info
- **Services**: Overview of IT Services, Consulting, Training
- **IT Services / Consulting / Training**: Dedicated service detail pages
- **Clients**: Client logos and testimonials
- **News**: Latest news and updates
- **Contact**: Contact form with location/email info

## User preferences

_Populate as you learn them._

## Gotchas

- Do NOT run `pnpm dev` at workspace root — use the workflow runner instead
- PORT and BASE_PATH env vars are required by vite.config.ts (provided by workflow)
- The `@assets` alias points to `/attached_assets/` at the monorepo root

## Pointers

- See `.local/skills/pnpm-workspace/SKILL.md` for monorepo structure
- See `.local/skills/react-vite/SKILL.md` for frontend conventions
