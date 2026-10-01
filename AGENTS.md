# AGENTS.md

## Project

Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no environment variables.

## Running

- `docker compose -f docker-compose.base44.yml up -d` — runs `node server.js` from the bind-mounted source on port 3000.
- No live-reload dev server; restart the container after code changes (`docker compose -f docker-compose.base44.yml restart app`).
- `GET /` serves the page; `GET /health` returns `{"status":"ok"}`.

## Notes

- The README asks not to change this fixture app — the E2E tests depend on its exact content.
