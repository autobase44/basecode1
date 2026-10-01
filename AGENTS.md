# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no external credentials.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App runs on port 3000 with `node --watch` for live reload on file changes.
- Health check: `GET /health` → `{"status":"ok"}`

## Structure
- `server.js` — single-file HTTP server serving a static HTML page at `/` and JSON at `/health`.
- `package.json` — no dependencies; `npm start` runs `node server.js`.
- `Dockerfile` — production build (not used by Base44 dev compose).

## Notes
- No env vars or secrets required.
- Node `--watch` provides live reload; edits to `server.js` restart the server automatically.
