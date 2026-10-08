# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no env vars, and no external services.

## Setup
- Runs via `docker compose -f docker-compose.base44.yml up -d` using `node:20-alpine` with the source bind-mounted.
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in watcher).
- No `npm install` needed — the app uses only `node:http`.

## Verification
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`
- Preview is on port 3000.
