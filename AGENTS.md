# AGENTS.md

## Project Overview

Minimal Node.js web app (single file `server.js`, no dependencies, no database, no external services). Used as a fixture for Base44 Base Code E2E tests.

## Running in the Base44 Sandbox

- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in watcher).
- Source is bind-mounted, so edits are picked up without rebuilding the image.
- Health endpoint: `GET /health` → `{"status":"ok"}`.
- No environment variables or secrets required.
