# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no environment variables, and no build step. Used as an E2E test fixture.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Source is bind-mounted; the container runs `node server.js` directly (no live-reload dev server — call `reload_preview` after edits).
- Health check: `GET /health` returns `{"status":"ok"}`.
- Homepage: `GET /` returns the HTML page with heading "Base Code E2E".

## Notes
- No `npm install` needed — only uses `node:http` (built-in).
- No secrets or external credentials required.
