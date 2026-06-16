# CLAUDE.md — Handoff for New Sessions

## First thing to do

Install dependencies before running any commands:

```powershell
pnpm install
```

If `pnpm` is not recognized, add the npm global bin to PATH first:

```powershell
$env:PATH += ";C:\Users\Local_Admin\AppData\Roaming\npm"
```

## Set up the local database

```powershell
$env:DATABASE_URL="file:./dev.db"
pnpm prisma migrate deploy
pnpm db:seed
```

## What this project is

Ticket triage dashboard for Bistec Global PMO staff. Built spec-first as part of the BISTEC Hearts Academy IRP Week 1 challenge.

- **Framework:** Next.js 15 App Router, TypeScript strict
- **Data:** Prisma + SQLite
- **Styling:** Tailwind CSS
- **Validation:** Zod
- **Tests:** Vitest
- **CI:** GitHub Actions (lint → typecheck → test → build)

## Key scripts

| Command | What it does |
|---|---|
| `pnpm dev` | Start dev server |
| `pnpm lint` | ESLint |
| `pnpm typecheck` | `tsc --noEmit` |
| `pnpm test` | Vitest smoke tests |
| `pnpm build` | Next.js production build |
| `pnpm db:migrate` | Create a new migration |
| `pnpm db:seed` | Seed the database with 12 sample tickets |

## Where things live

- `docs/spec/prd.md` — Product requirements
- `docs/spec/stories/` — S-001 through S-007 user stories
- `prisma/schema.prisma` — DB schema
- `src/app/api/tickets/` — GET and PATCH route handlers
- `src/app/tickets/` — Dashboard UI (server page + client TicketRow)
- `tests/` — Vitest smoke tests
- `.github/workflows/ci.yml` — CI pipeline

## Current status

- Scaffold is built and committed
- `prisma/migrations/` exists and is tracked — CI uses `prisma migrate deploy`
- Next step: verify all four CI checks pass (lint, typecheck, test, build)
