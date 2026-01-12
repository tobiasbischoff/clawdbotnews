# Clawdbot Daily

Executive-friendly daily summaries of the `clawdbot/clawdbot` repository.

## What it does
- Pulls commits from GitHub for a date range.
- Groups them by day and renders a CTO/CEO-ready brief.
- Uses MiniMax (Anthropic-compatible) to generate concise AI summaries per day.

## Local setup
```bash
npm install
cp .env.example .env
npm run dev
```

Then open `http://localhost:3000`.

## Environment variables
- `ANTHROPIC_BASE_URL` (required for AI): `https://api.minimax.io/anthropic` (global) or `https://api.minimaxi.com/anthropic` (China).
- `ANTHROPIC_API_KEY` (required for AI): your MiniMax key.
- `ANTHROPIC_MODEL` (optional): defaults to `MiniMax-M2.1`.
- `GITHUB_REPO` (optional): defaults to `clawdbot/clawdbot`.
- `GITHUB_BRANCH` (optional): defaults to `main`.
- `GITHUB_TOKEN` (optional): increases GitHub rate limits.

## Notes
- Without `ANTHROPIC_API_KEY`, the UI still renders commit history but AI summaries are disabled.
- GitHub API rate limits apply. Add `GITHUB_TOKEN` for higher limits.
- Commit data and AI summaries are cached in SQLite for faster reloads and to avoid rate limits.
- SQLite runs via `sql.js` (WASM), so there is no native build step.
- New commits are synced incrementally; set `SYNC_INTERVAL_MINUTES` to control how often GitHub is polled.

## Debugging summaries
Use `/api/summary?date=YYYY-MM-DD` to fetch the cached prompt + model response for a given day.
