# AGENTS.md

## Project

Minimal Node.js HTTP server (`server.js`) with zero dependencies, no environment variables, and no database. Serves a static HTML page at `/` and JSON at `/health`.

## Running (Base44 dev environment)

```
docker compose -f docker-compose.base44.yml up -d --build
```

- Uses `node:20-alpine` with the source bind-mounted at `/app`.
- Live reload via `nodemon` (installed at container startup); edits to `server.js` restart the server automatically.
- Web entry point on host port 3000.
- Healthcheck probes `GET /health` (returns `{"status":"ok"}`).

## Notes

- The repo's own `Dockerfile` bakes source via `COPY` — do not use it for dev; the compose file above mounts live source instead.
- No external credentials or secrets are required.
