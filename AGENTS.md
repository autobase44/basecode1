# Base44 Dev Environment

## Overview

Minimal Node.js web app (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running

```bash
docker compose -f docker-compose.base44.yml up -d
```

- App runs on port 3000 (mapped from container port 3000).
- Uses `node --watch` (Node 20+ built-in) for live reload on file changes.
- Source is bind-mounted at `/app`; edits appear without rebuild.
- Healthcheck probes `GET /health` (returns `{"status":"ok"}`).

## Verification

- `curl http://localhost:3000/` — should return HTML with heading "Base Code E2E".
- `curl http://localhost:3000/health` — should return `{"status":"ok"}`.

## Notes

- No secrets, environment variables, or databases required.
- No `npm install` needed — zero dependencies.
