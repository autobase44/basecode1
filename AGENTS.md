# Base44 Dev Environment

## Overview
Minimal Node.js web app (single `server.js`, no dependencies, no database, no env vars required).

## Setup
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- No `npm install` needed — the app uses only Node built-ins (`node:http`).
- No live-reload dev server; changes require a container restart or `reload_preview`.

## Verification
- `GET /` returns the page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
