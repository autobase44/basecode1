# AGENTS.md

## Overview
Minimal Node.js web app (single `server.js`, no dependencies, no database, no environment variables).

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App served on port 3000; `GET /health` returns `{"status":"ok"}`.
- Uses `node --watch server.js` for live reload on file changes.

## Notes
- No `npm install` needed — zero dependencies.
- No external credentials required.
- The README warns not to change app content (it's an E2E test fixture).
