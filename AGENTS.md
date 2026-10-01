# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file: `server.js` — serves `GET /` (HTML page) and `GET /health` (`{"status":"ok"}`).

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000 (mapped to host 3000).
- No live-reload dev server; after editing `server.js`, run `docker compose -f docker-compose.base44.yml restart web` then `reload_preview`.
- No environment variables or secrets required.

## Healthcheck
`GET /health` returns `{"status":"ok"}`.

## Notes
- The README asks not to change app content (E2E test fixture). Base44 artifacts (compose, environment.json, AGENTS.md) are additive.
