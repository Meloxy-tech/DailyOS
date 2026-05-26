# DailyOS

Your everyday productivity operating system — notes, timers, tasks, habits, and utilities in one beautiful dashboard.

![DailyOS](https://img.shields.io/badge/Next.js-15-black?style=flat-square)
![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=flat-square)
![Tailwind](https://img.shields.io/badge/Tailwind-4-38bdf8?style=flat-square)

## Features

- **Landing page** — Free app overview with daily-flow guidance & FAQ
- **Authentication** — Supabase email/password, Google OAuth, guest mode
- **Dashboard** — Draggable, resizable widgets (react-grid-layout)
- **Notes** — Markdown editor, folders, tags, pins, AI summarize
- **Focus** — Pomodoro, stopwatch, fullscreen focus mode
- **Tasks** — Kanban board with drag status transitions
- **Habits** — Streaks, XP, weekly heatmap
- **Utilities** — Password, QR, JSON, color picker, counter, random picker
- **Analytics** — Productivity stats & weekly charts
- **AI Assistant** — OpenAI-powered sidebar (graceful fallback)
- **PWA** — Installable web app manifest

## Tech Stack

- Next.js 15 (App Router)
- TypeScript
- Tailwind CSS v4
- ShadCN-style Radix UI components
- Framer Motion
- Supabase Auth
- Prisma ORM + PostgreSQL
- Zustand (persisted local state)
- Vercel-ready deployment

## Quick Start

```bash
cd dailyos
npm install
cp .env.example .env.local
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

### Guest mode (no setup)

Click **Continue as guest** on the login page — all core features work with local persistence.

## Environment Variables

Copy `.env.example` to `.env.local`:

| Variable | Required | Description |
|----------|----------|-------------|
| `NEXT_PUBLIC_APP_URL` | Yes | App URL (e.g. `http://localhost:3000`) |
| `NEXT_PUBLIC_SUPABASE_URL` | For auth | Supabase project URL |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | For auth | Supabase anon key |
| `DATABASE_URL` | For sync | Postgres connection string |
| `DIRECT_URL` | For migrations | Direct Postgres URL |
| `OPENAI_API_KEY` | Optional | AI assistant & note summaries |

## Supabase Setup

1. Create a project at [supabase.com](https://supabase.com)
2. Copy **Project URL** and **anon key** to `.env.local`
3. Enable **Email** auth under Authentication → Providers
4. Enable **Google** OAuth (add redirect: `https://your-domain.com/auth/callback`)
5. Under **Database**, copy the Postgres connection string to `DATABASE_URL`

## Database Setup

```bash
# Push schema to Supabase Postgres
npm run db:push

# Seed demo data
npm run db:seed
```

### Prisma Studio

```bash
npm run db:studio
```

## Folder Structure

```
dailyos/
├── prisma/
│   ├── schema.prisma    # Database models
│   └── seed.ts          # Demo seed data
├── public/
│   └── manifest.json    # PWA manifest
├── src/
│   ├── app/
│   │   ├── (app)/       # Authenticated app pages
│   │   ├── (auth)/      # Login & signup
│   │   ├── api/         # API routes (AI, sync)
│   │   └── auth/        # OAuth callback
│   ├── components/
│   │   ├── dashboard/   # Widget grid
│   │   ├── layout/      # Shell, sidebar, command palette
│   │   ├── landing/     # Marketing page
│   │   ├── ui/          # Design system
│   │   └── widgets/     # Dashboard widgets
│   ├── lib/             # Prisma, Supabase, utils
│   ├── stores/          # Zustand app state
│   └── types/           # Shared TypeScript types
└── .env.example
```

## Deploy to Vercel

1. Push repo to GitHub
2. Import project in [Vercel](https://vercel.com)
3. Add all environment variables from `.env.example`
4. Deploy — `postinstall` runs `prisma generate` automatically
5. Run `npm run db:push` against production database once

### Build locally

```bash
npm run build
npm start
```

## API Routes

| Route | Method | Description |
|-------|--------|-------------|
| `/api/ai` | POST | OpenAI chat assistant |
| `/api/sync/notes` | GET/POST | Sync notes to Prisma (when DB configured) |
| `/auth/callback` | GET | Supabase OAuth callback |

## Keyboard Shortcuts

- `⌘K` / `Ctrl+K` — Command palette

## License

MIT
