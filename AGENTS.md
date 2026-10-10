# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no external services).

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App serves on port 3000: `GET /` shows the page, `GET /health` returns `{"status":"ok"}`
- Source is bind-mounted; no live-reload dev server — restart the container after edits.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Constraints
- The repo is a test fixture; the E2E tests depend on its exact content. Do not change `server.js` or `package.json` unless asked.
