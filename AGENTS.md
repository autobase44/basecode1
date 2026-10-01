# AGENTS.md

## Overview
Minimal Node.js web app (single `server.js`, no dependencies, no database, no env vars).

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts on port 3000.
- Uses `node:20-alpine` with the source bind-mounted at `/app`. No build step needed.
- `GET /` → HTML page with heading "Base Code E2E". `GET /health` → `{"status":"ok"}`.

## Editing
- Plain `node server.js` has **no live-reload**. After editing `server.js`, call `reload_preview` (or restart the container) for changes to appear.
- No `node_modules` — only Node built-in modules are used.
