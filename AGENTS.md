# Base44 Dev Environment

## Project
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables. Serves a single HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- App runs on port 3000 via `node:20-alpine` with source bind-mounted at `/app`.
- Uses `nodemon --legacy-watch` for live reload of `server.js` edits.
- Healthcheck probes `GET /health` (expect `{"status":"ok"}`).

## Notes
- No external credentials needed.
- No migrations or seeds.
- The README says this is a test fixture — avoid changing its content unless asked.
