# Base44 Setup Notes

## Overview

Minimal Node.js web app (`server.js`) — no dependencies, no database, no external services. Serves an HTML page at `/` and JSON at `/health`.

## Running

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

- App runs on port 3000.
- Source is bind-mounted; `node server.js` is the start command (no live-reload dev server — call `reload_preview` after edits).
- Healthcheck: `GET /health` returns `{"status":"ok"}`.

## Verification

- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E".
- `curl http://localhost:3000/health` → `{"status":"ok"}`.
