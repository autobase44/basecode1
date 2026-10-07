# AGENTS.md

## Project Overview

Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Setup

- Runtime: Node.js >= 20 (via `node:20-alpine` in `docker-compose.base44.yml`).
- Source is bind-mounted into the container; no image rebuild needed for edits.
- No live-reload dev server exists — after editing `server.js`, call `reload_preview` so the preview reflects the change.
- No secrets or external credentials required.

## Verification

- `GET /` returns HTML with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
- Healthcheck in compose probes `/health` via wget.
