# Repository Guidelines

## Project Structure & Module Organization
- `server.js` is the Express API server (GitHub sync, AI summaries, SQLite persistence).
- `public/` contains the static UI assets: `index.html`, `styles.css`, and `app.js`.
- `data/` holds the SQLite database (`clawdbotnews.sqlite`). It is generated at runtime.
- `.env` and `.env.example` define runtime configuration (API keys, sync intervals, model settings).

## Build, Test, and Development Commands
- `npm install` — installs dependencies.
- `npm run dev` — starts the local server at `http://localhost:3000`.
- `npm start` — same as `dev`, for production-style start.

## Coding Style & Naming Conventions
- JavaScript (ESM) is used throughout. Keep modules small and focused.
- Use 2‑space indentation and double quotes for strings (match existing files).
- Prefer descriptive names: `syncIssuesAndPRs`, `buildFallbackSummary`, `groupByDateKey`.

## Testing Guidelines
- There are no automated tests in this repo yet.
- If you add tests, place them alongside source modules (e.g., `server.test.js`) and document how to run them in this file.

## Commit & Pull Request Guidelines
- This repo does not enforce a commit format. Use clear, imperative messages.
- Recommended prefixes (consistent with the upstream `moltbot` repo): `feat`, `fix`, `refactor`, `docs`, `test`, `chore`.
- PRs should include a short description of user-facing impact and screenshots for UI changes.

## Security & Configuration Tips
- Never commit `.env` or API keys.
- For GitHub API rate limits, set `GITHUB_TOKEN` in `.env`.
- AI summaries require `ANTHROPIC_API_KEY` and `ANTHROPIC_BASE_URL`.

## Architecture Notes
- GitHub commits, issues, and PRs are incrementally synced to SQLite.
- AI summaries are cached in SQLite and reused across reloads.
