# Base44 Dev Environment

Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Run
```
docker compose -f docker-compose.base44.yml up -d --build
```
- Web entry point: http://localhost:3000/ (heading "Base Code E2E")
- Health check: http://localhost:3000/health → `{"status":"ok"}`
- Live reload: Node's built-in `--watch` restarts on edits to `server.js`.

## Notes
- No secrets or environment variables are required.
- The app binds to `::` (IPv4+IPv6), so `localhost` healthchecks work.
