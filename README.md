# Web Chess Game

A fully client-side chess game built with Next.js — play a complete two-player chess match in the browser with full rules enforcement, move history, and captured-piece tracking.

## What it does

- Full 8×8 chess board with all standard pieces and starting positions
- Complete move validation: legal moves per piece, check detection, checkmate, and stalemate
- Turn-based local play (White vs Black on the same device)
- Legal-move highlighting when a piece is selected
- Move history list and captured-pieces panels
- Game controls: reset/new game, plus game status display (check / checkmate / stalemate)

## Features

- Pure client-side React — no backend, no accounts, no network calls
- Game logic isolated in `lib/chess-rules.ts` (move validation, check/checkmate/stalemate)
- Click-to-select and click-to-move interaction with valid-move dots
- Responsive Tailwind UI with shadcn-style components (`components/ui/`)
- Dark/light theme support (`components/theme-provider.tsx`)

## Tech stack

- **Next.js 15** (App Router, statically exported — no server needed)
- **React 19**
- **TypeScript**
- **Tailwind CSS 3.4** (+ `tailwindcss-animate`)
- **Radix UI** primitives, `lucide-react`, `next-themes`

## Quick start

```bash
npm install        # or: pnpm install
npm run dev
```

Open http://localhost:3000 — White moves first; click a piece to see its legal moves, click a highlighted square to move.

Production build:

```bash
npm run build
npm run start
```

## Project structure

```
app/                    # App Router: layout.tsx, page.tsx (renders <ChessGame />)
components/             # chess-game.tsx (state), chess-board.tsx, chess-square.tsx,
                        # game-controls.tsx, game-info.tsx, ui/ (button, card, tabs)
lib/                    # chess-types.ts (PieceType/PieceColor/Position),
                        # chess-rules.ts (isValidMove, makeMove, isCheck, isCheckmate, isStalemate),
                        # chess-utils.ts, utils.ts
public/                 # static assets
next.config.mjs         # static export config (see note below)
```

## Environment variables

None.

## Deployment

This app is fully static (`output: 'export'` in `next.config.mjs`), so it deploys to any static host — GitHub Pages, Cloudflare Pages, Netlify, Vercel:

```bash
npm run build     # emits ./out/
# serve or upload the ./out/ directory
```

> Note: `next.config.mjs` sets `basePath: '/web-chess-game'` for the GitHub Pages subpath. Remove the `basePath` line when deploying to a root domain or Vercel.

Live demo: https://girishlade111.github.io/web-chess-game/

---

Built by Girish Lade · https://ladestack.in
