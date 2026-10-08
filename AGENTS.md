# Base44 Dev Environment

## Project Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Setup
- `docker compose -f docker-compose.base44.yml up -d --build` brings up the app on port 3000.
- The source is bind-mounted; `node --watch` provides live reload on file changes.
- Health check: `GET /health` returns `{"status":"ok"}`.
- Main page: `GET /` returns HTML with heading "Base Code E2E".

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with `<h1>Base Code E2E</h1>`

## Notes
- No environment variables or secrets required.
- Node >=20 required (uses `node --watch`).
