# Base44 Setup Notes

## Overview
Minimal zero-dependency Node.js HTTP server (`server.js`) used as an E2E test fixture.
No database, no external services, no secrets required.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch` (built into Node 20) for live reload on file changes.
- Source is bind-mounted; edits appear without rebuilding the image.

## Verification
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
