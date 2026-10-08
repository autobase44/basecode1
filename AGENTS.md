# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Serves a single page at `/` and a health check at `GET /health`.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d --build
```
The app listens on port 3000. It uses `node --watch` for live reload on file changes.

## Verification
- `curl http://localhost:3000/` — returns HTML with heading "Base Code E2E"
- `curl http://localhost:3000/health` — returns `{"status":"ok"}`

## Notes
- No `npm install` needed — the app uses only Node.js built-in modules.
- No environment variables or secrets required.
