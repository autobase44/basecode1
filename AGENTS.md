# Base44 Dev Environment

Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Web entry point: http://localhost:3000/ (heading "Base Code E2E")
- Health check: `GET /health` → `{"status":"ok"}`

## Notes
- The compose setup bind-mounts the source and runs `node --watch server.js` so edits hot-reload without an image rebuild.
- The repo's own `Dockerfile` bakes source via `COPY . .` (production-style); it is NOT used for the dev preview.
- No external credentials are needed.
