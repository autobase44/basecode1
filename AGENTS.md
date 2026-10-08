# AGENTS.md

## Project

Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Running in the sandbox

```
docker compose -f docker-compose.base44.yml up -d
```

- The app is bind-mounted from source; edit `server.js` and restart the container to see changes (no live-reload dev server).
- Web entry point on host port 3000; health check at `GET /health` → `{"status":"ok"}`.
- No environment variables or secrets required.
