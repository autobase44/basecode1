# Base44 dev environment

Minimal Node.js HTTP server (`server.js`), no dependencies, no database, no external services.

## Run
`docker compose -f docker-compose.base44.yml up -d` — serves on host port 3000.

## Notes
- No live-reload dev server; `server.js` changes require `reload_preview` (or `docker compose restart web`) to take effect.
- `GET /` → HTML page with heading "Base Code E2E"; `GET /health` → `{"status":"ok"}`.
- No secrets or environment variables required.
