# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no environment variables. Serves a static HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Web entry point: port 3000
- Health check: `GET /health` → `{"status":"ok"}`
- Source is bind-mounted; no live-reload watcher (app has no dev deps and README says don't change it). Use `reload_preview` after edits.

## Notes
- Do NOT modify `server.js` or `package.json` — the E2E tests depend on their exact content.
- No secrets required.
