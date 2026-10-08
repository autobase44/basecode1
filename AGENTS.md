# Base44 Setup Notes

## Overview
Minimal Node.js web app (no dependencies, no database, no env vars) used as an E2E test fixture.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000, serves `GET /` (HTML page) and `GET /health` (JSON `{"status":"ok"}`).
- Live reload via `node --watch` (built into Node 20, no nodemon needed).

## Verification
- `curl http://localhost:3000/` returns HTML with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.
