# Base44 Dev Environment

Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables.

## Running

```
docker compose -f docker-compose.base44.yml up -d
```

- Uses `node:20-alpine` with the repo bind-mounted at `/app`.
- Runs `node --watch server.js` for live reload on file changes.
- Web entry point on host port 3000.
- Healthcheck: `GET /health` → `{"status":"ok"}`.

## Notes

- The repo's own `Dockerfile` bakes source via `COPY` (production build) — don't use it for dev; the compose file above runs from the cloned source instead.
- No external credentials needed.
