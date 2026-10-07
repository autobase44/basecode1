# AGENTS.md

## Project

Minimal Node.js web app (test fixture for Base44 Base Code E2E tests). No dependencies, no database, no external services, no environment variables required.

- `server.js` — plain `node:http` server. `GET /` returns an HTML page; `GET /health` returns `{"status":"ok"}`.
- Binds to `::` (IPv4+IPv6) so `localhost` healthchecks work.
- `package.json` has zero dependencies — no `npm install` needed.

## Running in Base44 sandbox

- `docker compose -f docker-compose.base44.yml up -d` — runs `node:20-alpine` with the repo bind-mounted at `/app`, command `node server.js`, port 3000.
- No live-reload dev server (plain HTTP server); call `reload_preview` after source edits so the preview reflects them.
- Healthcheck uses `wget` (available in alpine) against `/health`.
- No secrets required.
