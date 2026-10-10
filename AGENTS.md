# AGENTS.md

## Project Overview

Minimal Node.js web app (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running

```
docker compose -f docker-compose.base44.yml up -d
```

App listens on port 3000. Healthcheck: `GET /health` → `{"status":"ok"}`.

## Notes

- No live-reload dev server — plain `node server.js`. After edits, call `reload_preview`.
- No environment variables or secrets required.
- Node >= 20.
