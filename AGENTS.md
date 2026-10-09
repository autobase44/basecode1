# AGENTS.md

## Project overview

Minimal Node.js web app (single `server.js`, no dependencies, no database).
Serves an HTML page at `GET /` and `{"status":"ok"}` at `GET /health`.

## Running in the Base44 sandbox

```
docker compose -f docker-compose.base44.yml up -d --build
```

- Base image: `node:20-alpine`; source is bind-mounted at `/app`.
- Dev command: `node --watch server.js` (Node 20+ built-in file watcher — no extra dependencies needed).
- No environment variables or external credentials required.
- Web entry point on host port 3000; healthcheck probes `/health`.

## Verifying

- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
