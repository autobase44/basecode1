# AGENTS.md

## Overview
Minimal Node.js HTTP fixture app (`server.js`), no dependencies, no database, no environment variables.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Source is bind-mounted; no live reload (plain `node server.js`). Call `reload_preview` after edits.
- `GET /` serves the HTML page; `GET /health` returns `{"status":"ok"}`.

## Notes
- The repo is a Base44 E2E test fixture — avoid changing its content unless explicitly asked.
