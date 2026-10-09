# AGENTS.md — Base44 sandbox notes

## What this app is
A zero-dependency Node HTTP server (`server.js`) that serves one static page and a
`GET /health` JSON endpoint. No database, no env vars, no external services, no secrets.

## Sandbox run
- Bring up: `docker compose -f docker-compose.base44.yml up -d --build`
- The web entry point is host port **3000** (`docker-compose.base44.yml`).
- The service runs `node --watch server.js` against a bind mount of the repo, so edits to
  `server.js` restart the server automatically — no rebuild needed.

## Verifying it works
- `curl -s http://localhost:3000/health` → `{"status":"ok"}`
- `curl -s http://localhost:3000/` → HTML containing the heading `Base Code E2E`
- `docker compose -f docker-compose.base44.yml ps` → `web` reports healthy.

## Quirks
- `README.md` states the app content is a fixture for Base44 E2E tests and must not be
  changed. Keep setup changes confined to compose/config files, not `server.js`.
- There are no dependencies, so there is no install step and no `node_modules` volume.
