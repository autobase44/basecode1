# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no environment variables. Used as a Base44 Base Code E2E test fixture — do not change its content.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Web entry point: host port 3000 → `GET /` (HTML page with "Base Code E2E" heading)
- Health check: `GET /health` → `{"status":"ok"}`
- No live-reload dev server; `server.js` runs directly via `node`. After edits, call `reload_preview` to refresh the preview.

## Secrets
None required. No external services.
