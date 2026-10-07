# Base44 Dev Environment

This is a minimal Node.js app (`server.js`) with no dependencies, no database, and no environment variables.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The source is bind-mounted into the container at `/app`; `node server.js` runs it directly.
- There is no live-reload dev server (plain `http.createServer`). After editing `server.js`, run `docker compose -f docker-compose.base44.yml restart web` then reload the preview.

## Health
- `GET /health` returns `{"status":"ok"}`.
- `GET /` returns the HTML page with heading "Base Code E2E".

## Notes
- The repo's own `Dockerfile` bakes source via `COPY`; it is NOT used for dev — the compose file runs from the bind-mounted source so edits are picked up.
- No secrets or external services are required.
